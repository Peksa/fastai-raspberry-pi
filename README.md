# Python wheels for installing fast.ai on a raspberry pi

Should work with Python 3.6, fast.ai 1.0 on armv6 (tested) or armv7 (not tested).

I didn't manage to build a working wheel for `spacy` - however it's only required for the fastai text package - vision works fine without it.

These have been tested on a **Raspberry Pi Zero W, running Raspbian Buster and Berryconda 3.2**.

PyTorch was built with the following options:
```
NO_CUDA=1
NO_DISTRIBUTED=1
NO_MKLDNN=1 
```

# Instructions
Make sure you get Python 3.6 on the raspberry first, I used Berryconda: https://github.com/jjhelmus/berryconda

Then install the wheels:
```
pip install numpy-1.17.2-cp36-cp36m-linux_armv6l.whl
pip install numexpr-2.7.0-cp36-cp36m-linux_armv6l.whl
pip install Bottleneck-1.2.1-cp36-cp36m-linux_armv6l.whl
pip install Pillow-6.1.0-cp36-cp36m-linux_armv6l.whl
pip install torch-1.2.0a0+8554416-cp36-cp36m-linux_armv6l.whl
pip install torchvision-0.4.0a0+d31eafa-cp36-cp36m-linux_armv6l.whl
```

And finally
`pip install fastai --no-deps`

Inference time with a resnet34 model is around **52s per image** on a Raspberry Pi zero - not exactly fast, but enough for my use-case :)

# Credits
Thanks to [@nmilosev](https://github.com/nmilosev) for the very useful guide of getting cross-compilation of PyTorch working on a desktop:
https://nmilosev.svbtle.com/compling-arm-stuff-without-an-arm-board-build-pytorch-for-the-raspberry-pi

(I used Ubuntu and debootstrap with qemu)
