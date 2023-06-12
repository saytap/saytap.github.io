# SayTap: Language to Quadrupedal Locomotion

This repo contains the videos for our [paper](https://arxiv.org/abs/xxx.xxxx).

### If all you want to do is view the page locally

Run `python -m http.server` to serve on the base directory to view `index.html` in a local browser.

### Article

`draft.md` - main text of the article, in markdown.

`draft_appendix.md` - appendix, in markdown.

`draft_bib.html` - the citations.

`draft_header.html` - start of the document

`index.html` - generated, don't edit this file.

### Instructions to Build and Test
```bash
git clone https://github.com/saytap/saytap.github.io.git
cd saytap.github.io
npm install
```

Modify text by editing `draft.md` -- this is where all of the content exists.

Appendix content goes in `draft_appendix.md`. Add bib entries to `draft_bib.html`.

Run `./bin/make` to build document into `index.html` (which are identical).
Run `python -m http.server` to serve on the base directory to view `index.html` in a local browser for debugging.

To watch all markdown files for changes and then compile them, you can run the following
```
brew install fswatch
./bin/watch
```

### Citation

For attribution in academic contexts, please cite this work as

BibTeX citation
```
@article{saytap2023,
  author = {Yujin Tang and Wenhao Yu and Jie Tan and Heiga Zen and Aleksandra Faust and</br>Tatsuya Harada},
  title  = {SayTap: Language to Quadrupedal Locomotion},
  eprint = {arXiv:xxxx.xxxxx},
  url    = {https://saytap.github.io},
  note   = "\url{https://saytap.github.io}",
  year   = {2023}
```
