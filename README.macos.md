# Commands

Download models and put them into `./models`:
- https://huggingface.co/hacksider/deep-live-cam/resolve/main/GFPGANv1.4.pth
- https://huggingface.co/hacksider/deep-live-cam/blob/main/inswapper_128.onnx

```sh
brew install python3.10 tcl-tk
python3.10 -m venv env
```

Edit `env/bin/activate` and add:
```sh
# env/bin/activate
# ...

export PATH="/opt/homebrew/opt/tcl-tk/bin:$PATH"
export LDFLAGS="-L/opt/homebrew/opt/tcl-tk/lib"
export CPPFLAGS="-I/opt/homebrew/opt/tcl-tk/include"
export PKG_CONFIG_PATH="/opt/homebrew/opt/tcl-tk/lib/pkgconfig"
```

Install dependencies:
```sh
source env/bin/activate
pip install -r requirements.txt

# ❌ This is in README but DON'T DO THIS:
# pip uninstall onnxruntime onnxruntime-silicon
# pip install onnxruntime-silicon==1.13.1
```

Run:
```sh
python run.py --execution-provider coreml
```

Edit resolution at [`ui.py#L260`](https://github.com/gongzhang/Deep-Live-Cam/blob/a31e81fa6625d2293a62ad4335287c79b4b478d2/modules/ui.py#L260) to get better performance.
