# elixir-elm
a container to run a phoenix application together with elm


# Erlang

To update the Erlang version:
    - Update the version number
    - download the archive of the appropriate version to your local machine
    - use 'sha1sum $theArchive' to create a new checksum
    - update the checksum in the dockerfile

To update the rebar3 version:
    - Update the version number
    - download the archive of the appropriate version to your local machine
    - use 'sha256sum $theArchive' to create a new checksum
    - update the checksum in the dockerfile