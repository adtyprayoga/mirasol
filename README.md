# Mi-Ra-Sol

Aditya Prayoga's notes that grow and connect over time.

Mi-Ra-Sol is a personal digital garden built with [Quartz v5](https://github.com/jackyzha0/quartz). It publishes connected learning notes with short explanations, practical examples, and references. The collection currently focuses on cybersecurity, with room for other subjects as new public notes are prepared.

## Explore the Notes

Start with the [garden homepage](content/index.md), browse [all cybersecurity topics](content/Cybersecurity/topics.md), or choose a study area:

- [Identity and Access](content/Cybersecurity/identity-and-access/index.md)
- [Network and Cloud Controls](content/Cybersecurity/network-and-cloud-controls/index.md)
- [Application and Delivery Security](content/Cybersecurity/application-and-delivery-security/index.md)
- [Detection and Response](content/Cybersecurity/detection-and-response/index.md)
- [Cryptography and Resilience](content/Cybersecurity/cryptography-and-resilience/index.md)
- [Risk and Governance](content/Cybersecurity/risk-and-governance/index.md)

The [references and editorial method](content/Cybersecurity/references.md) explain how sources, examples, and limitations are handled.

## Run Locally

Install Node.js 22 or newer, npm 10.9.2 or newer, and Git. The repository's `.node-version` pins Node.js 22.16.0.

```sh
git clone https://github.com/adtyprayoga/mirasol.git
cd mirasol
npm install
npx quartz plugin install
npx quartz build --serve
```

Open [localhost:8080](http://localhost:8080). Quartz reads notes from `content/`, writes the site to `public/`, and rebuilds when files change.

## Repository Layout

| Path                       | Purpose                                                     |
| -------------------------- | ----------------------------------------------------------- |
| `content/`                 | Published Markdown notes and topic hubs                     |
| `quartz.config.yaml`       | Site identity, theme, plugins, and layout                   |
| `quartz/`                  | Quartz source, Preact components, styles, and static assets |
| `docs/`                    | Quartz framework documentation                              |
| `.quartz-nemu-export.json` | Export manifest recording content file hashes               |
| `public/`                  | Generated website; ignored by Git                           |

## Write and Preview

Add Markdown notes under `content/`. Use YAML frontmatter for metadata such as `title`, `description`, `created`, `updated`, and `tags`. Connect related notes with Obsidian wikilinks, for example `[[Cybersecurity/identity-and-access/least-privilege|Least Privilege]]`, and update the relevant topic hub.

The configured site supports search, backlinks, a graph view, callouts, Mermaid diagrams, and LaTeX. Review sources and keep meaningful qualifications alongside the explanation.

## Development Commands

| Command                    | Purpose                                   |
| -------------------------- | ----------------------------------------- |
| `npx quartz build`         | Build the static site into `public/`      |
| `npx quartz build --serve` | Preview notes with automatic rebuilds     |
| `npm test`                 | Run Node tests through `tsx`              |
| `npm run check`            | Check TypeScript and Prettier formatting  |
| `npm run format`           | Format repository files with Prettier     |
| `npm run docs`             | Preview Quartz documentation from `docs/` |

## Publishing

Set `configuration.baseUrl` in `quartz.config.yaml` to the intended hostname and path before building for deployment. Upload the generated `public/` directory to a static host.

The included CI and deployment workflows retain upstream `jackyzha0/quartz` repository guards. Configure workflows for this repository before relying on automatic checks or publishing.

## Credits and License

Built on [Quartz](https://github.com/jackyzha0/quartz) by Jacky Zhao and its contributors. Quartz documentation is included in `docs/`. See [LICENSE.txt](LICENSE.txt) for the MIT license.
