conda-zsh-completion
--------------------

Zsh completion for conda.

This branch (``awk-parser``) keeps the completion free of a Python runtime by
embedding a trimmed, query-oriented copy of JSON.awk to parse conda's JSON
output.

Changes in this branch
~~~~~~~~~~~~~~~~~~~~~~

* Removed the Python ``json`` dependency; JSON.awk is embedded in ``_conda``.
* Updated command, option and description specs against conda 24.11.3 and
  conda-build 24.5.1.
* Added missing completions for package versions, environment variables,
  configuration keys/values, revisions, multiple paths and common plugin
  commands.
* Added ``conda activate --stack`` and ``--no-stack``.
* Added caching for package/version queries and silenced completion-time
  parser/conda errors.
* Removed mamba/micromamba registration; this completion targets ``conda``.
* Applied the zsh ``completion-style-guide`` cleanup.

Performance
~~~~~~~~~~~

The embedded JSON.awk parser is somewhat slower than the previous Python-based
parser, especially for large ``conda search`` payloads. Package and version
lists are cached to reduce repeated completion cost, while the Python runtime
dependency is removed.

Acknowledgements
~~~~~~~~~~~~~~~~

* JSON.awk by step-, MIT licensed; see ``LICENSE.JSON.awk.txt``.
* The conda-zsh-completion upstream authors and contributors.
* The conda project and its command help output.
* The zsh ``completion-style-guide`` maintainers.

License
~~~~~~~

BSD-3-Clause; see ``LICENSE.txt``. The embedded JSON.awk parser is distributed
under the MIT license; see ``LICENSE.JSON.awk.txt``.
