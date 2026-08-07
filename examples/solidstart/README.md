<!-- deno-fmt-ignore-file -->

Fedify–SolidStart integration example
=====================================

This is a simple example of how to integrate Fedify into a [SolidStart]
application.

[SolidStart]: https://start.solidjs.com/


Running the example
-------------------

1.  Clone the repository:

    ~~~~ sh
    git clone https://github.com/fedify-dev/fedify.git
    ~~~~

2.  Build packages:

    ~~~~ sh
    cd fedify
    mise install
    ~~~~

3.  Move to example folder:

    ~~~~ sh
    cd examples/solidstart
    ~~~~

4.  Start the server:

    ~~~~ sh
    deno task dev
    ~~~~


How it works
------------

Fedify integrates into SolidStart by handling ActivityPub requests alongside
SolidStart's standard HTTP routing:

 -  **`src/federation.ts`**: Defines the `Federation` instance and configures
    actor dispatchers, key pairs, and inbox/outbox handling.
 -  **`src/routes/`**: Handles web traffic and exposes API routes. Fedify
    intercepts incoming HTTP requests for federated endpoints (such as
    `/users/{identifier}` and `/inbox`) and delegates them to
    `federation.fetch()`.


Testing endpoints
-----------------

Once the server is running on `http://localhost:3000`, you can test ActivityPub
content negotiation using `curl` or the Fedify CLI:

~~~~ sh
# Lookup actor via Fedify CLI
fedify lookup http://localhost:3000/users/demo
~~~~
