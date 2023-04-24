[![Test](https://github.com/pyt-team/torch_topo/actions/workflows/test.yml/badge.svg)](https://github.com/pyt-team/torch_topo/actions/workflows/test.yml)
[![Lint](https://github.com/pyt-team/torch_topo/actions/workflows/lint.yml/badge.svg)](https://github.com/pyt-team/torch_topo/actions/workflows/lint.yml)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/pyt-team/torch_topo/blob/main/examples/Introduction_to_deep_higher_order_networks.ipynb)

# 🌐 TopoModelX (TMX) 🍩
# Topological Deep Learning

![tnns_network_with_layers](https://user-images.githubusercontent.com/8267869/234083711-26959012-e590-4808-be22-9c6cc979f276.png)


`TopoModelX` (TMX) is a Python module for topological deep learning, which simple and efficient solutions for science and engineering. 

TMX's development follows the topological deep learning (TDL) blue print laid out in:
- [Hajij et al. 2023. Topological Deep Learning: Going Beyond Graph Data](https://arxiv.org/abs/2206.00606). 

TMX can reproduce and extend the topological neural networks (TNNs) surveyed in:
- [Papillon et al. 2023. Architectures of Topological Deep Learning: A Survey on Topological Neural Networks](https://arxiv.org/abs/2304.10031).

Their TNN equations are available at [https://github.com/awesome-tnns/awesome-tnns](https://github.com/awesome-tnns/awesome-tnns).


## 🦾 Contributing to TMX

To develop tmx on your machine, here are some tips.

First, we recommend using Python 3.10, which the python version used to run the unit-tests.

Then:

1. Clone a copy of tmx from source:

   ```bash
   git clone git@github.com:pyt-team/TopoModelX.git
   cd TopoModelX
   ```

2. If you already cloned tmx from source, update it:

   ```bash
   git pull
   ```

3. Install tmx in editable mode:

   ```bash
   pip install -e ".[dev,full]"
   ```

   This mode will symlink the Python files from the current local source tree into the Python install. Hence, if you modify a Python file, you do not need to reinstall tmx again and again.

4. Install torch, torch-scatter, torch-sparse with or without CUDA depending on your needs.

      To install the binaries for PyTorch 1.12.0, simply run:
      ```bash
      pip install torch==1.12.0 --extra-index-url https://download.pytorch.org/whl/${CUDA}
      pip install torch-scatter torch-sparse torch_geometric -f https://data.pyg.org/whl/torch-1.12.0+${CUDA}.html
      ```

      where `${CUDA}` should be replaced by either `cpu`, `cu102`, `cu113`, or `cu115` depending on your PyTorch installation (`torch.version.cuda`).

      For PyTorch 10 or 11 replace `torch-1.12` by `torch-1.10` or `torch-1.11`.

5. Install the package TopoNetX from source, following: https://github.com/pyt-team/TopoNetX
6. Install the package TopoEmbedX from source, following: https://github.com/pyt-team/TopoEmbedX

7. Ensure that you have a working tmx installation by running the entire test suite with 

   ```bash
   pip install pytest
   pytest
   ```

   In case an error occurs, please first check if all sub-packages ([`torch-scatter`](https://github.com/rusty1s/pytorch_scatter), [`torch-sparse`](https://github.com/rusty1s/pytorch_sparse), [`torch-cluster`](https://github.com/rusty1s/pytorch_cluster) and [`torch-spline-conv`](https://github.com/rusty1s/pytorch_spline_conv)) are on its latest reported version.

8. Install pre-commit hooks:

   ```bash
   pip install pre-commit
   pre-commit install
   ```

### Unit Testing

The tmx testing suite is located under `test/`.
Run the entire test suite with

```bash
pip install pytest
pytest
```

## 🔍 References ##

To learn more about the topological deep learning blueprint:

- Mustafa Hajij, Ghada Zamzmi, Theodore Papamarkou, Nina Miolane, Aldo Guzmán-Sáenz, Karthikeyan Natesan Ramamurthy, Tolga Birdal, Tamal K. Dey, Soham Mukherjee, Shreyas N. Samaga, Neal Livesay, Robin Walters, Paul Rosen, Michael T. Schaub. [Topological Deep Learning: Going Beyond Graph Data](https://arxiv.org/abs/2206.00606).
```
@misc{hajij2023topological,
      title={Topological Deep Learning: Going Beyond Graph Data}, 
      author={Mustafa Hajij and Ghada Zamzmi and Theodore Papamarkou and Nina Miolane and Aldo Guzmán-Sáenz and Karthikeyan Natesan Ramamurthy and Tolga Birdal and Tamal K. Dey and Soham Mukherjee and Shreyas N. Samaga and Neal Livesay and Robin Walters and Paul Rosen and Michael T. Schaub},
      year={2023},
      eprint={2206.00606},
      archivePrefix={arXiv},
      primaryClass={cs.LG}
}
```
