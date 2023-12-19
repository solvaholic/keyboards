# keyboards

## Iris rev4
I'm using [QMK firmware](https://github.com/qmk/qmk_firmware) on an Iris rev4, and finally gave the rotary encoder a job: My keyboard now has a volume knob on it :heart_eyes:

The volume knob requires [some configuration](https://github.com/qmk/qmk_firmware/blob/master/docs/feature_encoders.md) that doesn't just go in the .json file, so here we are.

## Iris rev6
I'm also using [QMK firmware](https://github.com/qmk/qmk_firmware) on an Iris rev6 without a volume knob.

### Layer 0

![layer0](https://github.com/solvaholic/keyboards/assets/14636658/bc75c453-5644-4d73-9153-7c89dde32a34)

<details><summary>Expand to see layers 1, 2, and 4</summary>
<p>
  
### Layer 1
![layer1](https://github.com/solvaholic/keyboards/assets/14636658/2a24fd9f-c8e6-4209-a7bf-95616d7f0abb)

### Layer 2
![layer2](https://github.com/solvaholic/keyboards/assets/14636658/f0b46c71-d700-4bcb-b808-65d7056736bf)

### Layer 4
![layer4](https://github.com/solvaholic/keyboards/assets/14636658/0d2a0bb0-bc5f-4f18-9e7c-04927a0d0f0c)

</p>
</details>

## QMK Configurator

QMK Configurator available online at <https://config.qmk.fm>. To spare the project some hosting and compute costs, consider running it in a Docker container locally.

If you want to run the configurator on your computer at <http://localhost:8888>, run this command:

```bash
docker run --detach --rm --publish 8888:80 qmkfm/qmk_configurator:latest
```

If you want to run the configurator on a server nearby, you could do something like:

```bash
DOCKER_HOST=ssh://nas docker run --detach --rm --publish 8888:80 qmkfm/qmk_configurator:latest
```

Remember to clean up after yourself: Use `docker stop` to stop and remove containers when you're done with them.

## QMK manual build
If your configuration doesn't all fit in the .json, and you prefer not to manage yet another build environment, run a shell in a qmk_firmware container:

```bash
_keymap=keebio/iris/keymaps/solvaholic
_image=qmkfm/qmk_firmware:latest
docker run -it --rm -v $(realpath $_keymap):/qmk_firmware/keyboards/$_keymap $_image /bin/bash
```

And compile your keymap like this:

```bash
qmk compile -kb keebio/iris/rev4 -km solvaholic
```

This leaves some manual moving of files and running of QMK Toolbox as an excercise for the reader. TODO: Next time I update my keyboard firmware I'll make this procedure less manual.

## Thank you
- https://qmk.fm for QMK
- https://keeb.io and Lewis Ridden for Iris
- @lee-dohm for sharing [his keyboard firmware](https://github.com/lee-dohm/keyboard-firmware) and for setting many good examples
