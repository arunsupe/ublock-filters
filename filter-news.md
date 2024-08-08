# Filtering News Headlines: A Personal Approach

## Introduction
Many websites show hundreds of headlines, catering to everyone's interests; not just mine. To personalize, here is a simple filteration method I use: 

1. I maintain a list of keywords of my interests. Occassionally adding or subtracting.
    Example "my-likes.txt":

    ```
    technology
    science
    climate
    AI
    health
    ```

2. curl | grep -f this list
    ```bash
    curl -s https://news.ycombinator.com/ \
        | tr '\n' ' ' \
        | grep -oP '<a href.+?/a>' \
        | sed 's/\/a>/\/a><br>\n/' \
        | grep -f path/to/my-likes.txt
    ```


# Query expansion
To expand my list of likes using synonyms, I worte [synonym-finder](https://github.com/arunsupe/semantic-grep/blob/main/model_processing_utils/synonym-finder.go). This program uses a word2vec embedding model to find synonyms of the words in "my-likes.txt". To use:
    ```bash
    #Compile 
    go build -o synonym-finder synonym-finder.go

    # Download google's large word embedding model
    curl -L -o GoogleNews-vectors-negative300.bin.gz "https://drive.google.com/uc?export=download&id=0B7XkCwpI5KDYNlNUTTlSS21pQmM"

    # unzip (Note: this is a 4GB+ file)
    gunzip GoogleNews-vectors-negative300.bin.gz

    # find synonyms for your list, saving in expanded-likes.txt
    synonym-finder -model_path GoogleNews-vectors-negative300.bin -threshold 0.5 -f my-likes.txt > expanded-likes.txt
    ```

# Automating the collection of my-likes
My past google search phrases are a good place to start (google's takeout can give you these). [Download](https://support.google.com/accounts/answer/3024190?hl=en), then 