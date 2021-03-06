\ifndef{fourierBasis}
\define{fourierBasis}
\editme

\subsection{Fourier Basis}

\slides{* }
\notes{[Joseph Fourier](https://en.wikipedia.org/wiki/Joseph_Fourier) suggested that functions could be converted to a sum of sines and cosines. A Fourier basis is a linear weighted sum of these functions.}
  $$\basisFunc_j(\inputScalar) = \mappingScalar_0  + \mappingScalar_1 \sin(\inputScalar) + \mappingScalar_2 \cos(\inputScalar) + \mappingScalar_3 \sin(2\inputScalar) + \mappingScalar_4 \cos(2\inputScalar)$$


\setupcode{import numpy as np}
\code{%load -s fourier mlai.py}


\setupcode{import matplotlib.pyplot as plt
import mlai
import teaching_plots as plot}

\plotcode{f, ax = plt.subplots(figsize=plot.big_wide_figsize)
loc =[[0., 0.4,],
      [0.5, 0.4],
      [1, -0.4],
      [1.25, 0.4],
      [1.5, -0.4]]
text =['$\phi(x) = 1$',
       '$\phi(x) = \sin(x)$',
       '$\phi(x) = \cos(x)$',
       '$\phi(x) = \sin(2x)$',
       '$\phi(x) = \cos(2x)$']
plot.basis(mlai.fourier, x_min=0, x_max=2, 
           fig=f, ax=ax, loc=loc, text=text,
           diagrams='../slides/diagrams/ml',
           num_basis=5)}

\setupcode{import pods
from ipywidgets import IntSlider}
\displaycode{pods.notebook.display_plots('fourier_basis{num_basis:0>3}.svg', 
                            directory='../slides/diagrams/ml', 
							num_basis=IntSlider(0,0,4,1))}

\notes{In this code, basis functions with an *odd* index are sine and basis functions with an *even* index are cosine. The first basis function (index 0, so cosine) has a frequency of 0 and then frequencies increase every time a sine and cosine are included.}

\displaycode{pods.notebook.display_prediction(basis=mlai.fourier, num_basis=5)}

\subsection{Functions Derived from Fourier Basis}

$$
\mappingFunction(\inputScalar) = {\color{cyan}\mappingScalar_0}  + {\color{green}\mappingScalar_1 \sin(\inputScalar)} + {\color{yellow}\mappingScalar_2 \cos(\inputScalar)} + {\color{magenta}\mappingScalar_3 \sin(2\inputScalar)} + {\color{red}\mappingScalar_4 \cos(2\inputScalar)}
$$

\slides{
\define{width}{80%}
\startanimation{fourier_function}{0}{4}
\newframe{\includediagram{../slides/diagrams/ml/fourier_function000}{\width}}{fourier_function}
\newframe{\includediagram{../slides/diagrams/ml/fourier_function001}{\width}}{fourier_function}
\newframe{\includediagram{../slides/diagrams/ml/fourier_function002}{\width}}{fourier_function}
\newframe{\includediagram{../slides/diagrams/ml/fourier_function003}{\width}}{fourier_function}
\newframe{\includediagram{../slides/diagrams/ml/fourier_function004}{\width}}{fourier_function}
\endanimation
}

\notes{\figure{\includediagram{../slides/diagrams/ml/fourier_basis004}{80%}}{A Fourier basis is made up of sine and cosine functions with different frequencies.}{fourier-basis-4}}

\setupdisplaycode{import pods
from ipywidgets import IntSlider}
\displaycode{pods.notebook.display_plots('fourier_function{func_num:0>3}.svg', directory='../slides/diagrams/ml', func_num=IntSlider(0,0,2,1))}


\endif
