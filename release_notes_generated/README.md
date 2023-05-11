# Generated release notes: A demo

This directory provides a complete demo of a release notes documentation project. It uses the [Acorns](http://msuchane.github.io/acorns) tool to generate release notes from OpenShift tickets on Bugzilla and possibly on Jira.

## Layout

* The [master-template.adoc](master-template.adoc) file is the main AsciiDoc file. It includes both generated and manually written content.

* The [master-internal.adoc](master-internal.adoc) and [master-external.adoc](master-external.adoc) files are wrappers around [master-template.adoc](master-template.adoc). They enable you to select between an internal preview and a public version of the documentation.

* The [manual-sections](manual-sections) directory contains manually written AsciiDoc content that you can include from the main file.

* The [acorns/](acorns/) directory contains generator configuration files and generated AsciiDoc content that you can include from the main file:

    * [acorns/tickets.yaml](acorns/tickets.yaml) lists the tickets and ticket queries that populate your release notes.

    * [acorns/tracker.yaml](acorns/tracker.yaml) configures access to your Bugzilla and Jira instance.

    * [acorns/templates.yaml](acorns/templates.yaml) configures how your tickets are sorted into sections of the document.

    * [acorns/generated/internal/](acorns/generated/internal/) and [acorns/generated/internal/](acorns/generated/internal/) store the generated assemblies and modules.

## Generating the release notes

1. Install the Acorns tool. See [https://msuchane.github.io/acorns/#_installing_acorns](https://msuchane.github.io/acorns/#_installing_acorns).

2. Navigate to this directory.

3. Set your API keys:

    ```bash
    $ export BZ_API_KEY=my-bugzilla-key
    $ export JIRA_API_KEY=my-jira-key
    ```

4. Generate the release notes:

    ```bash
    $ acorns build
    ```

5. Build previews of the internal and external document:

    ```bash
    $ asciidoctor --safe -vn master-internal.adoc
    $ asciidoctor --safe -vn master-external.adoc
    ```

## Previewing the result

Open the following files in your web browser:

* Internal, debugging preview: `master-internal.html`.

* External, public preview: `master-external.html`.

* Tracking information about your tickets and release note sin them: `acorns/generated/status-table.html`.
