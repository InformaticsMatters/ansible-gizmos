# Ansible Gizmos

![GitHub tag (latest SemVer)](https://img.shields.io/github/v/tag/InformaticsMatters/ansible-gizmos)

[![lint](https://github.com/InformaticsMatters/ansible-gizmos/actions/workflows/lint.yaml/badge.svg?branch=main)](https://github.com/InformaticsMatters/ansible-gizmos/actions/workflows/lint.yaml)

[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/pre-commit/pre-commit)
[![Packaged with Poetry](https://img.shields.io/badge/packaging-poetry-cyan.svg)](https://python-poetry.org/)

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

Some **gizmos** depend on [Ansible Galaxy] roles and collection.
These can be installed in the normal way using our `requirements.yaml` file: -

    ansible-galaxy install -r requirements.yaml

>   **CAUTION** Some playbooks can install command-line tools that may replace
    tools you already have. They do not do this automatically, you can install these
    tools yourself. If you want the gizmo to install the tool you have to set
    a suitable variable for these potentially destructive actions. One example is
    `kubectl`, which will be installed in `/usr/local/bin` if you set `ktl_install_kubectl`
    (see our `k8s_kubectl` role regarding this tool).

Once you're setup you can run a **gizmo*: -

    ansible-playbook site-k8s-database-dump.yaml

And use a `parameters.yaml` file if you need to control the playbook's behaviour,
which is protected from git with our `.gitignore` file: -

    ansible-playbook site-k8s-database-dump.yaml -e @parameters.yaml

>   Parameter files that you want to preserve should be put int the `site-parameter-files`
    directory, which is monitored by git. If there are sensitive values in the files,
    remember to encrypt the file with [Ansible Vault], and **ALWAYS** use the
    extension `.vault`.

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

[ansible galaxy]: https://galaxy.ansible.com/
[ansible vault]: https://docs.ansible.com/ansible/latest/vault_guide/index.html
[commitizen]: https://commitizen-tools.github.io/commitizen/
[conventional commit]: https://www.conventionalcommits.org/en/v1.0.0/
[pre-commit]: https://pre-commit.com/
[poetry]: https://python-poetry.org/
