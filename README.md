Workflow to push changes:

- Checkout `draft` branch
- Commit and push changes
- Build local version of website with `bundle exec jekyll serve`
- Local website is available at `http://localhost:4000/`

Then 

```
git checkout master
cp -r _site/* . && rm -rf _site/
git add .
git commit -m "blah blah"
git push --all origin
```
