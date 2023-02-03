# Generated release notes: A demo

This directory provides a complete demo of a release notes documentation project. It uses the Cizrna tool to generate release notes from OpenShift tickets on Bugzilla and possibly on Jira.

## Layout

* The [master_template.adoc](master_template.adoc) file is the main AsciiDoc file. It includes both generated and manually written content.

* The [master_internal.adoc](master_internal.adoc) and [master_external.adoc](master_external.adoc) files are wrappers around [master_template.adoc](master_template.adoc). They enable you to select between an internal preview and a public version of the documentation.

* The [manual-sections](manual-sections) directory contains manually written AsciiDoc content that you can include from the main file.

* The [cizrna/](cizrna/) directory contains generator configuration files and generated AsciiDoc content that you can include from the main file:

    * [cizrna/tickets.yaml](cizrna/tickets.yaml) lists the tickets and ticket queries that populate your release notes.

    * [cizrna/tracker.yaml](cizrna/tracker.yaml) configures access to your Bugzilla and Jira instance.

    * [cizrna/templates.yaml](cizrna/templates.yaml) configures how your tickets are sorted into sections of the document.

    * [cizrna/generated/internal/](cizrna/generated/internal/) and [cizrna/generated/internal/](cizrna/generated/internal/) store the generated assemblies and modules.

## Generating the release notes

1. Install the Cizrna tool. See [https://msuchane.github.io/cizrna/#_installing_cizrna](https://msuchane.github.io/cizrna/#_installing_cizrna).

2. Navigate to this directory.

3. Set your API keys:

    ```bash
    $ export BZ_API_KEY=my-bugzilla-key
    $ export JIRA_API_KEY=my-jira-key
    ```

4. Generate the release notes:

    ```bash
    $ cizrna build
    ```

5. Build a preview of the internal and external document:

    ```bash
    $ asciidoctor --safe -vn master_internal.adoc
    $ asciidoctor --safe -vn master_external.adoc
    ```

## Previewing the result

Open the following files in your web browser:

* Internal, debugging preview: `master_internal.html`.

* External, public preview: `master_external.html`.

* Tracking information about your tickets and release note sin them: `cizrna/generated/status-table.html`.
