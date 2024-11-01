smoltcp fork for Asterinas
==========================

We forked [smoltcp] because it is primarily [designed] for embedded users, thus making it unsuitable for building a general-purpose OS, like [Asterinas].

This repository consists of patches that adapt and expose smoltcp's internal APIs, so that we can build our high-performance networking stack, [bigtcp], on top of it.

[smoltcp]: https://github.com/smoltcp-rs/smoltcp
[designed]: https://github.com/smoltcp-rs/smoltcp/issues/973#issuecomment-2297601850
[Asterinas]: https://github.com/asterinas/asterinas
[bigtcp]: https://github.com/asterinas/asterinas/tree/main/kernel/libs/aster-bigtcp

## Contributing

 - **Consider submitting your patch upstream, if possible.** This is necessary because we want to minimize the number of out-of-tree patches here, to reduce the amount of effort required to resolve merge conflicts.
 - If your patch is accepted upstream, you can open a PR here to bump the smoltcp head by updating the `HEAD` file.
 - If your patch cannot be committed upstream, you can open a PR here to add a patch to the `patches` directory.

After merging the PR here, we use GitHub actions to automatically generate [tags] for the patched smoltcp. Another PR is needed in the Asterinas repository to bump the kernel dependency.

[tags]: https://github.com/asterinas/smoltcp/tags

## Development

 1. Run `apply.sh`, which will switch to the `staging` branch and apply all patches there.
 2. Create a new branch (to prevent changes in the `staging` branch from being overwritten by the next `apply.sh` run), and develop.
 3. Use `git format-patch` to regenerate the patches after development is finished, and update `HEAD` if the smoltcp head has been bumped.
 4. Submit the patch and head changes as a PR.
