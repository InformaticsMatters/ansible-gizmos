# Ansible Gizmos

![GitHub tag (latest SemVer)](https://img.shields.io/github/v/tag/InformaticsMatters/ansible-gizmos)

[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit)
[![Packaged with Poetry](https://img.shields.io/badge/packaging-poetry-cyan.svg)](https://python-poetry.org/)

[![lint](https://github.com/InformaticsMatters/ansible-gizmos/actions/workflows/lint.yaml/badge.svg?branch=main)](https://github.com/InformaticsMatters/ansible-gizmos/actions/workflows/lint.yaml)

Generally useful Ansible playbooks (and roles), designed to run on localhost
(without an inventory), that don't fit in any other project. The outer project is
managed by Poetry.

Each **gizmo** is implemented in an Ansible Role and has a supporting project-root-level
playbook/site-file, named after the role, e.g. `site-k8s-database-dump.yaml`.

## Getting started
Prerequisites: -

1.  [Poetry]

Some **gizmos** may have additional prerequisites.
If they do the playbook should assert they are satisfied or make the prerequisite clear.

To get started, use the Poetry shell (environment): -

    poetry shell
    poetry install

And from here you can run a playbook: -

    ansible-playbook site-k8s-database-dump.yaml

And use a `parameters.yaml` file if you need to,
which is protected from git with our `.gitignore` file: -

    ansible-playbook site-k8s-database-dump.yaml -e @parameters.yaml

## Contributing
The project uses: -

- [pre-commit] to enforce linting of files prior to committing them to the
  upstream repository
- [Commitizen] to enforce a [Conventional Commit] commit message format

You **MUST** comply with these choices in order to  contribute to the project.

To get started review the pre-commit utility and the conventional commit style
and then set-up your local clone by following the **Installation** and
**Quick Start** sections: -

    pre-commit install -t commit-msg -t pre-commit

Now the project's rules will run on every commit, and you can check the
current health of your clone with: -

    pre-commit run --all-files

---

[commitizen]: https://commitizen-tools.github.io/commitizen/
[conventional commit]: https://www.conventionalcommits.org/en/v1.0.0/
[pre-commit]: https://pre-commit.com
[poetry]: https://python-poetry.org/
