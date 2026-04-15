# metagenomics-sunbeam-pipeline
This is a pipeline for metagenomics that I optimized for work on the cluster
#check for git module
module avail git
#git alone wont let you jave remote https

#load conda env
module load miniconda3 #this works for the uahpc

module load miniconda3/base/py38_4.13.0 #works too

conda init bash
source ~/.bashrc

conda create -n gitfix git -y #not really necessary

#create sunbeam env. I had to do all these before finally being able to use git clone
conda create -n sunbeam_env git -y

#activate sunbeam env
conda activate sunbeam_env

#check remote https
ls $(git --exec-path)/git-remote-https
ls

git clone -b stable https://github.com/sunbeam-labs/sunbeam sunbeam-stable #this didnt work
git ls-remote --heads https://github.com/sunbeam-labs/sunbeam

#worked getting the files for sunbeam
git clone https://github.com/sunbeam-labs/sunbeam
 #change directory or git branch wont work
cd sunbeam/
git branch -a
