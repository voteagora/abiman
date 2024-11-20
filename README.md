# abiman

A web-app backed by GCS and a VM w/ Git Creds to manage (host, tag, verify, compare) contract ABIs.

## How it Works

A bucket on GCS with version control enabled stores:

- ABIs
- Snapshots of git repos at specific SHAs
- Contract Deployments

A web-tool & CLI then lets you link Contract Deployments to ABIs, optionally automatically verifying from deterministic builds.

## Features 

- Pass a git-sha of a public-repo to the UI -> the app takes a snapshot and builds the ABIs, waiting to be linked to contract deployments.
- Add a contract deployment to the UI -> given a chain ID, contract address and optionally flagging it as a proxy.
- kick off a build of the ABI, linking that git-sha to the ABI.
- upload an ABI file manually doing the linking.
- choose another ABI file that exists, and link that to a contract
- Tag the Contract+ABI pair against with types of distinct-tags (repo + SHA, SHA-only, unique string)
- Tag the Contract+ABI pair against with types of non-distict-tags (solidity file name, version number, string)
- An API lets you query ABIs based on explicit & safe mechanisms (ie, will fail if you query wrong) OR implicit & unsafe mechanism (ie, will try to do auto-magic to guess what you meant. Eg. Only pass an address and no chain ID -> takes first? Proxy or Implementation -> Implementation? etc.
