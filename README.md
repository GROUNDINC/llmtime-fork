# Large Language Models Are Zero Shot Time Series Forecasters

This repository contains the code for the paper
[_Large Language Models Are Zero Shot Time Series Forecasters_](https://github.com/ngruver/time-series-lm/tree/main)
by Marc Finzi, Nate Gruver, Shikai Qiu and Andrew Gordon Wilson (NeurIPS 2023).

<figure>
  <img src="./assets/llmtime_top_fig.png" alt="Image">
  <figcaption> We propose <em>LLMTime</em>, a method for <em>zero-shot</em> time series forecasting with large language models (LLMs) by encoding numbers as text and sampling possible extrapolations as text completions. LLMTime can outperform many popular timeseries methods without any training on the target dataset (i.e. zero shot). The performance of LLMTime also scales with the power of the underlying base model. However, models that undergo alignment (e.g. RLHF) do not follow the scaling trend. For example, GPT-4 demonstrates inferior performance to GPT-3. </figcaption>
</figure>

## 🛠 Installation
Run the following command to install all dependencies in a conda environment named `llmtime`. Change the cuda version for torch if you don't have cuda 11.8. 
```
sh install.sh
```
After installation, activate the environment with
```
conda activate llmtime
```
If you prefer not using conda, you can also install the dependencies listed in `install.sh` manually. 

Finally, add your openai api key to `~/.bashrc` with
```
echo "export OPENAI_API_KEY=<your key>" >> ~/.bashrc
```

## 🚀 Trying out LLMTime
Want a quick taste of the power of LLMTime? Run the quick demo in the `demo.ipynb` notebook. No GPUs required!

## 🤖 Plugging in other LLMs
We currently support GPT-3, GPT-3.5, GPT-4, and LLaMA 2. It's easy to plug in other LLMs by simply specifying how to generate text completions from them in `models/llms.py`.

## 💡 Tips 
Here are some tips for using LLMTime:
- The recently released `gpt-3.5-turbo-instruct` seems to work better with a lower temperature (e.g. 0.3) than other models, and tends to not outperform `text-davinci-003` from our limited experiments.

## 📊 Replicating experiments in paper
Run the following commands to replicate the experiments in the paper. The outputs will be saved in `./outputs/`. You can use `visualize.ipynb` to visualize the results. We also provide precomputed outputs used in the paper in `./precomputed_outputs/`.
### Darts (Section 4)
```
python -m experiments.run_darts
```
### Monash (Section 4)
```
python -m experiments.run_monash
```
### Synthetic (Section 5)
```
python -m experiments.run_synthetic
```
### Missing values (Section 6)
```
python -m experiments.run_missing
```
### Memorization (Appendix B)
```
python -m experiments.run_memorization
```

## Citation
Please cite our work as:
```bibtex
@article{finzi2023llmtime,
    title={{Large Language Models Are Zero Shot Time Series Forecasters}},
    author={Marc Finzi, Nate Gruver, Shikai Qiu and Andrew Gordon Wilson},
    journal={Neural Information Processing Systems (NeurIPS)},
    year={2023}
}
```