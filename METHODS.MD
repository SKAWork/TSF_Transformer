<strong><u>I. Introduction</strong></u>

This document aims to explain the scientific approach and reasoning behind the project, including the mathematical and machine learning concepts I explored.

This project is a purely personal endeavor. It may never reach a definitive end, and the results might never be groundbreaking. This is absolutely fine, as the primary goal is to explore concepts from pure mathematics—algebra, vector spaces, topology—which are my first passion, and machine learning, my second passion.

The project combines a decoder-only Transformer architecture with a time series forecasting task, where the main challenge is to predict a token from a continuous set rather than from a discrete vocabulary as in conventional LLMs.

<strong><u>II. Philosophy and Data Representation</strong></u>

The raw data consists of a set of points that I group into chunks of 100 points, each approximated by a Bernstein polynomial of degree 31.

Why Bernstein polynomials?
Bernstein polynomials have the unique property of uniform convergence towards any continuous function. This ensures stable polynomial approximations over the interval [0, 1].

Why degree 31?
Degree 31 is chosen because higher degrees can produce excessively large coefficients when computing Bernstein representations, which could harm numerical stability.

Once the Bernstein polynomial is obtained, I group sequences of 49 consecutive polynomials. The decoder-only Transformer is then trained to predict the 49th polynomial from the preceding 48. This creates a continuous token prediction problem, quite different from typical discrete token prediction in NLP.

<strong><u>III. Loss Functions</strong></u>

I have experimented with several loss functions, but none has yet produced consistently satisfactory results. The main approach currently uses the Sobolev inner product of degree 0, with its induced norm and distance:
⟨𝑃,𝑄⟩=∫𝑃(𝑥)⋅𝑄(𝑥) 𝑑𝑥

At degree 0, the Sobolev norm is equivalent to the L² norm, which captures pointwise similarity.

The advantage of using Sobolev norms is that we can extend to higher degrees, for instance degree 1, to also account for derivative similarity. This allows the loss function to consider both value similarity and variation (slope) similarity between polynomials.

Other loss functions implemented include projection-based distances and Gaussian negative log-likelihood, mainly for experimentation.

<strong><u>IV. Implementation Notes</strong></u>

Transformer architecture: decoder-only, without softmax at the output.

Softmax is difficult to apply in a continuous space. One possible solution is to cluster similar polynomials (e.g., 𝑃(𝑥)=𝑥² and 𝑄(𝑥)=0.9𝑥²) to reduce the output space and allow a softmax.

Pol2Vec (word2vec equivalent) is not yet implemented. I plan to use skip-gram to learn polynomial embeddings for better token representation.

Numerical precision: All polynomial computations are performed with float64, to avoid large errors when evaluating Bernstein polynomials.

Data splitting: The dataset is divided into train (80%), validation (10%), and test (10%) sets, ensuring non-overlapping sequences.

<strong><u>V. Results and Current Limitations</strong></u>

So far, the results are not conclusive. The model outputs remain largely constant.

This outcome is expected due to current architecture limitations, including the absence of softmax and the continuous nature of the output.

Future improvements include implementing token clustering, Pol2Vec embeddings, and higher-degree Sobolev losses.

<strong><u>VI. Next Steps</strong></u>

For planned features and improvements, see ROADMAP.MD. Upcoming work includes:

Pol2Vec embedding using skip-gram.

Token space reduction to enable softmax on continuous outputs.

Experiments with Sobolev norms of degree 1 or higher for derivative-aware loss.

Additional Transformer variants and hyperparameter tuning.