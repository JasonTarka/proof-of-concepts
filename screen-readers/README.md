Concerning an issue in NVDA where spaces are not read out for offscreen text, and in VoiceOver where text is read out character-by-character.

- NVDA issue: https://github.com/nvaccess/nvda/issues/5448
- WebAim offscreen recommendation: http://webaim.org/techniques/css/invisiblecontent/

## To test

- Use NVDA on Windows with Firefox and read the page as normal
  - The first block of "hidden" text will read without spaces
  - The second and third will read out correctly
  - Tested using Firefox 45, NVDA 2016.1, Windows 8.1 Enterprise
- Use VoiceOver on Mac OS X with Safari and read the page
  - The first block will read as individual characters
  - The second will read correctly
  - The third will read as a series of individual words
  - Tested using Safari 9.1 on OS X 10.11.4

## Conclusions

Using `word-wrap: break-word` on a parent element causes serious issues in both NVDA/Firefox and VoiceOver/Safari.
Adding `white-space: nowrap` fixes these issues, and stops the partial-issue in VoiceOver that occurs regardless of `word-wrap`.

