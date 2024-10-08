# ublock Obnoxiousness Filter
Are you getting more Trump or Taylor in your digital life than you care for? Ever open your news feed to find the same celebrity drama, political scandals, or clickbait headlines dominating the space? [uBlock Origin](https://github.com/gorhill/uBlock), the powerful ad blocker, can be your secret weapon for filtering out more than just ads!

Many news sources prioritize clicks over substance, bombarding us with celebrity gossip, manufactured outrage, and clickbait. This constant barrage can be overwhelming and detract from valuable information.

[uBlock Origin](https://github.com/gorhill/uBlock), historically used to filter out advertisements, can be equally effective in removing these attention-grabbing distractions. (I am sure this idea is not new, but I have not found any active implementations of it). 

This repository pilots the idea with a small, curated list of uBlock Origin [filters](https://raw.githubusercontent.com/arunsupe/ublock-filters/main/ublock-filters.txt) designed to remove some of these online annoyances. This is still an experiment. I want to make a useful list, without hurting performance. Not sure I have succeeded yet. **Viewer discretion adviced**.


## Key Benefits:
- **Reduce Information Overload:** Filter out content that you don't care for.
- **Enhance Readability:** Create a cleaner, streamlined, distraction free online environment.
- **Improve Focus:** Stay on track and avoid getting pulled into time-wasting clickbait articles.


## How to Use:
1. **Install uBlock Origin:** If you haven't already, install the [uBlock Origin](https://github.com/gorhill/uBlock) extension for your browser. It is available for most major browsers.
2. **Import the Filter List:**
   - Open uBlock Origin's settings.
   - Navigate to the "Filter lists" tab.
   - Click "Import" and paste the following URL:
     ```
     https://raw.githubusercontent.com/arunsupe/ublock-filters/main/ublock-filters.txt
     ```
   - Click "Apply Changes."


## Creating Your Own Filters:
uBlock Origin [filters](https://github.com/gorhill/uBlock/wiki/Static-filter-syntax#extended-syntax) are rules that tell the browser to hide or modify specific elements on a webpage. While these rules can be complex, simple keyword matches can take us a long way. For example:
```
! Remove any link that that has text that matches hollywood or celebrity (case insensitive)
*##a:has-text(/Hollywood|Celebrity/i)
! Same, but remove the div that has text that matches
*##div:has(> a:has-text(/Hollywood|Celebrity/i))
```
To add custom filters: `uBlock settings -> My filters -> (Paste the filters) -> Apply changes -> Reload page`

Note: Even one wayward rule can hurt overall performance. Please test the rules carefully, and convince yourself the tradeoff is worth it, before using them.


## Contributing:
All contributions are welcome! This list is constantly evolving, and your feedback or additional filters are highly encouraged. Here's how you can get involved:
- **Pull Requests:** If you've created filters that you think would benefit others, submit a pull request to add them to the repository.
- **Issues:** Encountered issues with a filter? Found a website that's slipping through the cracks? Report the issue to help us maintain and improve the filter list.


## Disclaimer:
The effectiveness of these filters may vary depending on the website, the specific content you're trying to block, and ongoing adjustments by websites themselves. Feel free to adjust or customize the filter list according to your preferences.


## License:
This repository and its contents are licensed under the [MIT License](https://github.com/arunsupe/ublock-filters?tab=MIT-1-ov-file).
