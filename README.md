# MeCA_internship
Inter-species correspondences in primates' cortical morphology

Here are the scripts resulting from the 7 weeks-internship I had the chance to do with Olivier COULON and Kep Kee LOH 
in the Methods and Computational Anatomy (MeCA) team at the Institut de Neurosciences de la Timone, Marseille in June 2020.

Using the Cortical Surface toolbox that the team has developed and which is available on the software BrainVisa 
(http://meca-brain.org/software/) my goal was to develop a computational tool that would enable inter-species cortical surface
matching. Meaning that given the sulci-induced HIPHOP parameterization models of different primate species, the code is to
rescale the longitude and latitude textures of the primate we want to map a texture (of another species) onto, so that next
we can obtain a spherical mesh from it that still needs to be resampled and then remeshed to a cortical mesh. The overall idea
is detailed in the report of the internship that you will find in this repository.

More specifically, here is what the different scripts do:

* **read_file.py** contains functions that read text files such that HIP-HOP models (*read_model*) in their default generated format, 
correspondence tables (*read_corr*), and the affine transformations text files that are returned by the present code (*read_affine*).
This code is called by the other ones and has no use on its own.
* **PrimateToPrimate.py** was the first version of the code and can be ignored. It is however functional. It computes the affine
transformations and use them to rescale the corresponding longitudes and latitudes all at once.
* **Affine_transformations.py** Given two models and a correspondences text file, it returns the two text files of the affine transformations
from one primate to the other and the other way around.
* **Rescale.py** uses the affine transformations returned in the text files to rescale the longitude and latitude textures of 
the corresponding primate (the second one in the input parameters)
* **Affine_trans_compo.py** is a more sophisticated version of **Affine_transformations.py** as it uses an intermediary model to compute
the affine transformations. Hence it needs three models and two correpondences text files as inputs. For instance, it can help
reparameterizing the macaque's cortical mesh thanks to the putative sulci correspondences between the human and the macaque, the
macaque and the chimpanzee and the chimpanzee and the human.
* **Iterate.py** enables to rescale the longitude and latitude textures of all individuals of a model, in a Database that has the following shape:




