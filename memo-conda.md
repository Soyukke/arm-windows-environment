# Surface Pro XのwslでJuliaからConda.jlを使う

## Armアーキテクチャ用のcondaをインストールする

## .bashrcの設定

.bashrcで環境変数を設定する．デフォルトのインストール先のcondaディレクトリパスを指定する．
condaのpathは`conda info -e`で確認することができる．
export CONDA_JL_HOME=/home/[ユーザ名]/c4aarch64_installer

## Build Conda

CONDA_JL_HOMEを設定した状態で`Conda.jl`をビルドする．

## Jupyter notebook

Condaを適切にbuildできていたら`IJulia`を使ってminicondaインストールが始まらずに起動できる．

## Build PyCall

```julia
using Conda
ENV["PYTHON"]=joinpath(Conda.PYTHONDIR, "python3")
```

python3を指定するで大丈夫なのか...?

```julia
using Pkg
Pkg.build("PyCall")
```

これでPyCallも動く．
