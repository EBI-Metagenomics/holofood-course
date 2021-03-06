[![Documentation Status](https://readthedocs.org/projects/holofood-course/badge/?version=latest)](https://holofood-course.readthedocs.io/en/latest/?badge=latest)

# Holofood Course: workshop notes
## Organisation and utilisation of hologenomic datasets

This repository contains the source of the workshop notes of the "Organisation and utilisation of hologenomic datasets" course.

The notes are written using [Sphinx/RST](https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html).
It is a markup language.

The notes are built automatically to a [ReadTheDocs](https://readthedocs.org/) site: https://holofood-course.rtfd.io

## Using the course notes
Head to the [live documentation page](https://holofood-course.readthedocs.io/en/latest/)

## Adding to the course notes (as a course instructor)
- Clone this repository.
- (Optional): create a virtualenv / conda env. Sphinx uses Python.
- `pip install -r requirements.txt`
- Run Sphinx in watch mode, to build and serve the notes website as you write:
  - `sphinx-autobuild . _build/html --port 8000`
  - Go to [the locally served documentation site](http://127.0.0.1:8000) to see what your notes look like.
- Add a sub-directory for your course session to the `sessions` directory.
  - You can add `.rst` files and images etc as you wish. 
  The Sphinx website has [good tutorials](https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html) for using `.rst` if you are new to it. 
  - There is a stub example under `session/metagenomics`.
- Add a line to the `index.rst` table-of-contents with the path to your new `.rst` file(s).
- Open a pull request on GitHub to merge your changes in with everybody else's.

### Where to store other course assets (as a course instructor)
- You can also add a few scripts or notebooks or small datafiles etc to this repository, if they're needed for your course session.
- For big (>20MB) datafiles, host them elsewhere e.g. on an FTP server. During the course itself, we have S3 available for this purpose. 
- Use of Docker is fine / encouraged for packing software requirements. Quay.io is a good option for building/hosting these images.
