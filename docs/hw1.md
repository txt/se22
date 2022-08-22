  <a name=top><p>&nbsp;<hr>
  <p align=center>
  &nbsp;<a href="/README.md#top">home</a> &nbsp; | &nbsp;
  <a href="/docs/syllabus.md#top">syllabus</a> &nbsp; | &nbsp;
  <a href="https://docs.google.com/spreadsheets/d/1KuW-SH46KmFW0grEX2wT01jicUSew_5sr1QdGuSrweU/edit#gid=0">groups</a> &nbsp; | &nbsp;
  <a href="https://moodle-courses2223.wolfware.ncsu.edu/course/view.php?id=1771">moodle</a> &nbsp; | &nbsp;
  <a href="https://ncsu.hosted.panopto.com/Panopto/Pages/Sessions/List.aspx#folderID=%22389b8ebf-2f29-4c15-8231-aee9000e3f05%22">video</a> &nbsp; | &nbsp;
  <a href="/docs/review.md">review</a> &nbsp; | &nbsp;
  <a href="/LICENSE.md#top">&copy; 2022</a></p>
  <hr>
  <p align=center><a href="/README.md#top"><img  width=700 src="/etc/img/banner.png"></a></p>
  






# Howework 1: Write a "good" Github Repo


Your repo is your resume. But what is a good looking repo?


## Write a repo 


With the structure shown below. Ensure that  everyone in the group do at least one commit to the repo


Note:
- There is a lot to do here in a week. 
- You'll probably only get bits of this going in 1 week. But keep at it. Remember that homeworks can be submitted many
times with no penalties
- Suggestion: Divide up the structure between your group and everyone do different parts.
But make sure everyone knows what each part is.


Submit your a URL to your repo to Moodle.


## Structure


```txt
.gitignore
.travis.yml
CITATION.md : fill on once you've got your ZENODO DOI going
CODE-OF-CONDUCT.md
CONTRIBUTING.md
INSTALL.md
LICENSE.md
README.md
setup.py         // may change per language; e.g. Makefile 
requirements.txt // may change per language; e.g javascript uses package.json
data/
  README.md
test/
  README.md
code/
  __init__.py  // may change per language; 
```


If you don't know what any of the above do, then google them (they are quite standard). Also, read the following: 


- README.md
   - add the badge "build:passing" to your README.md. 
     -  Consider using a  free service like   github-actions
       - [instructions](https://lab.github.com/githubtraining/github-actions:-hello-world)
       - [example](https://github.com/timm/keys/blob/main/.github/workflows/unit-test.yml)
       - [badging](https://docs.github.com/en/actions/managing-workflow-runs/adding-a-workflow-status-badge) <a 
href="https://github.com/timm/keys/actions"><img src="https://github.com/timm/keys/actions/workflows/unit-test.yml/badge.svg"></a>
       - [badge graphics](https://shields.io/)
     - Consider using travis-ci see [Instructions](https://docs.travis-ci.com/user/customizing-the-build)
   - add the Zenodo DOI badge to your README.md. See [Instructions](https://genr.eu/wp/cite/)
- [.gitignore](https://github.com/github/gitignore)
- LICENSE.md
   - see [here](https://github.blog/2015-03-09-open-source-license-usage-on-github-com/)
   - and [Choose a License](https://choosealicense.com/licenses/)
- [CODE_OF_CONDUCT.md]( https://docs.github.com/en/github/building-a-strong-community/adding-a-code-of-conduct-to-your-project)
- [CONTRIBUTING.md](https://github.com/atom/atom/blob/master/CONTRIBUTING.md)
  - This contrib file is too verbose. Discuss with your group which 10-20 items you'd actually endorse from your project.
- [requirements.txt](https://www.idkrtm.com/what-is-the-python-requirements-txt/) (or equivalent in your language)
- [setup.py, __init__.py](https://github.com/bmcfee/spatialtree) (or equivalent in your language)
  - Test your package (`python3 setup.py install`) (or eqivalent in your language)


Regarding the last point, keep it real simple.
.e.g In Python, write the smallest example of [pytest](https://docs.pytest.org/en/stable/)
 running a file containing some `test_` functions.


```python
# content of __init__.py
def inc(x):
    return x + 1


def test_answer():
    assert inc(3) == 5
```


Hook that code into your repo so that the "build:passing" badge work (so that everytime you commit your repo, your tests re-run). This can be done with GitHub actions, and there are templates for runing test suites for many languages.


