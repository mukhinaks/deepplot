# deepplot
Link to original project: [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.2526396.svg)](https://doi.org/10.5281/zenodo.2526396)

Latex code for drawing neural networks for reports and presentation. Have a look into examples to see how they are made. Additionally, lets consolidate any improvements that you make and fix any bugs to help more people with this code.

## Difference from original
- If layer setting is not defined default box will be drawn
- You can change color of layers

## TODO
- [ ] Easy color usage
- [ ] Arrow modification
- [ ] Automatic legend
- [ ] Add examples 

## Getting Started
1. Install the following packages on Ubuntu.
    * Ubuntu 16.04
        ```
        sudo apt-get install texlive-latex-extra
        ```

    * Ubuntu 18.04.2
Base on this [website](https://gist.github.com/rain1024/98dd5e2c6c8c28f9ea9d), please install the following packages.
        ```
        sudo apt-get install texlive-latex-base
        sudo apt-get install texlive-fonts-recommended
        sudo apt-get install texlive-fonts-extra
        sudo apt-get install texlive-latex-extra
        ```

    * Windows
    1. Download and install [MikTeX](https://miktex.org/download).
    2. Download and install bash runner on Windows, recommends [Git bash](https://git-scm.com/download/win) or Cygwin(https://www.cygwin.com/)
    
    * Mac

      Install MacTex from [here](http://www.tug.org/mactex/mactex-download.html).

## Python usage

    import sys
    sys.path.append('..')

    from core.texpage import *
    import subprocess

    # Define tex page
    page = TexPage()

    # Add layers to model
    page.model.addLayer('Conv2D','c1', 2, 64, 64)
    page.model.addLayer('MaxPool', 'pool1', 2, 32, 32)
    page.model.addLayer('Conv2D', 'c2', 2, 32, 32)
    page.model.addLayer('MaxPool', 'pool2', 1, 28, 28)
    page.model.addLayer('SoftMax', 'soft', 1, 28, 28)
    page.model.addConnection('pool1', 'c2')
    page.model.addConnection('pool2', 'soft')

    # Create tex file
    namefile = str(sys.argv[0]).split('.')[0]
    page.generate(namefile + '.tex' )

    # Run tex to get pdf
    return_value = subprocess.call(['pdflatex', namefile + '.tex'], shell=False)


## Examples

Following are some network representations:

<p align="center"><img  src="https://user-images.githubusercontent.com/17570785/50308846-c2231880-049c-11e9-8763-3daa1024de78.png" width="85%" height="85%"></p>
<h6 align="center">FCN-8</h6>


<p align="center"><img  src="https://user-images.githubusercontent.com/17570785/50308873-e2eb6e00-049c-11e9-9587-9da6bdec011b.png" width="85%" height="85%"></p>
<h6 align="center">FCN-32</h6>


<p align="center"><img  src="https://user-images.githubusercontent.com/17570785/50308911-03b3c380-049d-11e9-92d9-ce15669017ad.png" width="85%" height="85%"></p>
<h6 align="center">Holistically-Nested Edge Detection</h6>
