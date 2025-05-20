# `monogres`: The Reproducible PostgreSQL monorepo

**`monogres`** is a Postgres distribution that centralizes, builds, and
packages [PostgreSQL] along with a curated ecosystem of extensions. It’s
designed to be **reproducible**, **modular**, and **community-driven**.

At its core, `monogres` provides:

- **Upstream, reproducible PostgreSQL** builds with many predefined "option
  sets" (see below).
- A centralized place to manage and build **Postgres extensions** in a
  consistent and reproducible way.
- A **foundation** for downstream distributions to base their own customized
  Postgres variants.

## 🌱 Built for the Community

`monogres` isn’t an end-user product. It’s an upstream project meant to serve
as a **foundation** for building downstream Postgres distributions.

It’s developed and licensed under the [Apache 2 License], a permissive license
that favors the integration and proliferation of downstream projects,
encouraging Postgres vendors, contributors, and enthusiasts to: extend and
adapt the project to their specific needs.

## 🔒 Reproducible by Design

`monogres` aims to ensure **bit-for-bit reproducibility** by:

- Always building from upstream source
- Always version-pinning and checksumming **everything**: source code, tools,
  binary dependencies, etc.
- Maintaining [monogres/postgres], a mirror of the official PostgreSQL repo
  with per-version branches containing only the minimal patches needed to make
  builds reproducible.

These practices align with the principles of [Reproducible Builds] and make it
easy to verify the integrity of published artifacts, strengthening the build
pipeline against [supply chain attacks]:

> Reproducible Builds elevate deterministic builds by making the build process
> independently verifiable by anyone. This means others can confirm your
> binaries match the source code exactly, fostering trust, improving debugging,
> speeding up builds, and demonstrating your commitment to high standards.

> First, the **build system** needs to be made entirely deterministic:
> transforming a given source must always create the same result.

> Second, the set of tools used to perform the build and more generally the
> **build environment** should either be recorded or pre-defined.

> Third, users should be given a way to recreate a close enough build
> environment, perform the build process, and **validate** that the output
> matches the original build.

### 🪞 Postgres reproducible patches

We aim to never modify Postgres' functional source code. However, its build
process is not yet fully reproducible.

To address this, we maintain a minimal set of reproducibility-focused patches
for each release in the [monogres/postgres] mirror. These patches are usually
one-liners and **only change the build system and Postgres metadata**. Nothing
else is changed.

The long-term goal is for these patches to be upstreamed. Once that happens,
this mirror will no longer be needed for future PostgreSQL versions but it will
remain available to support reproducible builds of older releases.

## 🐘 Postgres, Your Way

`monogres` builds Postgres Postgres with many predefined "option sets"
(combinations of compile-time options) tailored for different use cases. For
more details, check [Monogres "Option Sets" table].

## 🧩 A Unified Extension Ecosystem

The Postgres extension ecosystem is vast, and every user has different needs,
only using a handful of different extensions.

`monogres` provides a centralized place to manage and build **Postgres
extensions** in a consistent and reproducible way:

- Pulls extensions from their official repositories.
- Builds them in a **reproducible** way.
- Delivers a coherent distribution that includes Postgres *plus* a wide range
  of popular extensions.

<!-- Links -->

[Apache 2 License]: https://www.apache.org/licenses/LICENSE-2.0
[Monogres "Option Sets" table]: https://github.com/monogres/monogres/?tab=readme-ov-file#option-sets
[monogres/postgres]: https://github.com/monogres/postgres
[PostgreSQL]: https://postgresql.org
[Reproducible Builds]: https://reproducible-builds.org
[supply chain attacks]: https://en.wikipedia.org/wiki/Supply_chain_attack
