About the test app
------------------
To launch the test app, you need to make sure the following repos are
adjacent to the tk-multi-publish2 repo.

- tk-core (for bootstrapping)
- tk-frameworks-qtwidgets
- tk-frameworks-shotgunutils

You also need a connection to the internet as the shell engine and the core will
be pulled from the Toolkit AppStore and the app requires a connection to a
Flow Production Tracking site. You can use any site.

The app itself has a few plugins that pretend to operate on items found in a
scene.

Install tk-toolchain and use pytest to run the tests

For example (on \*nix), you have only just [git cloned](https://git-scm.com/docs/git-clone)
down this repository and currently cd'd into its root folder:

1. Setup a virtual environment with the Python requirements:

   ```bash
   python -m venv .venv
   .venv/bin/pip install git+https://github.com/shotgunsoftware/tk-toolchain.git#egg=tk-toolchain
   .venv/bin/pip install PySide6
   ```

2. Clone down the required `tk-*` repos adjacent to the current repository.

   Only run this if you don't have those repos already cloned down.

   ```bash
   xargs -i -t git clone git+github.com/shotgunsoftware/tk-{}.git ../tk-{} << EOF
   core
   shell
   frameworks-qtwidgets
   frameworks-shotgunutils
   EOF
   ```

3. Run pytest and output coverage to HTML to execute the tests:

   ```bash
   .venv/bin/coverage run -m pytest
   .venv/bin/coverage html
   ```

3. Run pre-commit to check the code quality:

   ```bash
   .venv/bin/pre-commit run --all
   ```
