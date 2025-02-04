# k0rdent documentation contributors' guide

k0rdent documentation is growing rapidly, and community members are very welcome to contribute by filing pull requests against documents in this repository. Thank you for your interest in k0rdent!

This page gives technical guidance for contributing to k0rdent documentation. It is _not_ a complete style guide. In most cases, Project k0rdent aspires to follow style recommendations adopted by the Kubernetes Project's SIG Docs group. Please see the [Kubernetes Documentation Style Guide](https://kubernetes.io/docs/contribute/style/style-guide/) for details.

## How k0rdent docs are written

k0rdent documentation is written mostly in [CommonMark](https://commonmark.org/) as adopted by GitHub, with a few CommonMark-compatible markdown enhancements used by MkDocs, the Material theme, and extensions (see below) to enable more-readable rendering of code, glossary items, images, and admonitions (e.g., NOTE:, TIP:, WARNING:, etc.). The [k0rdent documentation style guide](k0rdent-documentation-style-guide.md) details our markdown style, along with those extensions.

## How k0rdent docs are built

k0rdent documentation is built from Markdown (.md) documents using the [MkDocs](https://www.mkdocs.org/) static site generator with the [Material](https://squidfunk.github.io/mkdocs-material/) theme. We use several MkDocs extensions and plugins for rendering glossary items, admonitions (e.g., Note, Tip, Warning, etc.) and other special kinds of content.

Below you'll find [instructions for setting up MkDocs locally](#install-mkdocs-to-serve-k0rdent-docs-locally) to dynamically build and serve the k0rdent documentation from your local clone of the docs repository. This is handy for reviewing the rendered look and feel of changes and additions before filing a pull request.

## Contributing to k0rdent docs - simplest way: use GitHub

For making small corrections to k0rdent docs, the simplest tool is GitHub's website:

1. Search for

We like to use a standard open source workflow for 
## Install MkDocs to build k0rdent docs locally

MkDocs can be run on almost any contemporary Linux environment, desktop or server, inside a container, or on MacOS, Windows, or WSL. It requires recent (in k0rdent's case, 3.9+) versions of Python and pip.

    > NOTE:
    > k0rdent's MkDocs environment requires Python 3.9+ and a corresponding version of pip. 

Assuming you have a machine (desktop, laptop, VM) for editing with recent (Python 3.9+) versions of Python and pip:

1. Begin by cloning the k0rdent / docs repo locally using the git CLI or any git helper application.

    > NOTE:
    > the k0rdent / docs repo has a .gitignore already created in its root that will ignore the local /venv folder
    > and its contents you will create in step 3, below.

2. Switch into the cloned project directory:
   
   ```shell
   cd docs
   ```

3. Create a venv into which to install MkDocs and dependencies, saved in the /docs repo in a file called `requirements.txt`.

   ```shell
   python3 -m venv venv
   source venv/bin/activate
   ```

   Your terminal should now show `(venv)` in the prompt. This will create a local /venv folder in your copy of the repo, which the
   already-present .gitignore will ignore when you make commits and file pull requests. 

4. Install MkDocs and dependencies in the venv, using `requirements.txt`.

    > NOTE:
    > The file `requirements.txt` is in the /docs folder in k0rdent / docs
   
   ```shell
   pip install -r requirements.txt 
   ```

Once you've done this, you can execute MkDocs to dynamically build and serve docs locally on localhost (`http://127.0.0.1:8000`):

```shell
python3 mkdocs serve
```

Then just visit localhost in a browser (assuming you're doing this in a desktop-enabled environment).

Because localhost is unreachable from outside the local machine, you can also run MkDocs in a way that binds it to all network interfaces, making the docs viewable from any browser that can reach your MkDocs server. So you can, for example, set all this up on a desktop VM server instance, then view docs with your desktop's default browser on the VM's bridged or NATted IP address.

```shell
mkdocs serve -a 0.0.0.0:8000
```
