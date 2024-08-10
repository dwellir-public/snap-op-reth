# reth snap

The reth OP stack

Read the official op-reth docs here: https://reth.rs/run/optimism.html

The snap installs the "op-reth" command line tool and the op-reth-daemon service.

The snap only accepts --datadir paths: "/mnt /media /run/media" or $SNAP_COMMON/datadir (default)

## System considerations

TODO

## Running

```
op-reth node \
    --chain base \
    --rollup.sequencer-http https://mainnet-sequencer.base.org \
    --http \
    --ws \
    --authrpc.port 9551 \
    --authrpc.jwtsecret /path/to/jwt.hex
```

Start by installing reth:

    sudo snap install op-reth

(Optionally) Set the snap to not restart after an automatic upgrade. You need to restart the op-reth-daemon yourself if set.

    sudo snap set op-reth endure=true

Check and change the configuration of op-reth to your liking:

    snap get op-reth

Connect the snap removable-media interface. This allows the snap to access external filsystems/dirs (see: snap interface removable-media)

    sudo snap connect op-reth:removable-media

Configure your startup parameters (written to /var/snap/reth/common/service-arguments). 

    sudo snap set op-reth service-args='node ...'

Start op-reth.

    sudo snap start op-reth


Check logs:

    sudo snap logs op-reth -f


## Start op-reth-daemon (snap)
    sudo snap start op-reth