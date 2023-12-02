# How this should work

* A new Issue with label "next-roundup" will be created.
* People add items to this issue as markdown: `- [category] short description with [links](/link/to/item)`
* Github action is setup 
  * On a trigger (date? manual?) it will look at the only "next-roundup" issue that it open and, ignoring the first post (which is just instructions), grab all of the comments in that issue, building a list as it goes of each category.
  * Next it will generate a new `.md` file out of all the comments - with a header for each category, and then a list of all the links/entries in that category:
      ```
      run: |
          cat > "content/posts/${POST_TITLE}.md" << EOF
          ${POST_BODY}
          EOF
      ```
  * then hugo does it's thing, updates the site with the new page
  * close the issue, create a new one with the same general instructions for the first commment
  * ? automate posting to twitter? other places?
 
# TODO

- [ ] Build the Hugo site 
- [ ] come up with specific layout for each roundup
- [ ] build workflow
  - [ ] scrape issues
  - [ ] combine into new `.md`
  - [ ] build with hugo
  - [ ] publish
- [ ] design a logo?

# Reference

* https://gohugo.io/hosting-and-deployment/hosting-on-github/
* https://shazow.net/posts/github-issues-as-a-hugo-frontend/
* https://cli.github.com/manual/gh_search_issues
* https://docs.github.com/en/actions/using-workflows/using-github-cli-in-workflows
* https://stackoverflow.com/questions/58597010/how-to-access-a-github-issue-comment-body-using-github-actions
