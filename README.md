# Instructions for Madgraph simulation for Dark Photon Searches with Mu3e

Install Madgraph (no need for Pythia & Delphes) https://twiki.cern.ch/twiki/bin/view/CMSPublic/MadgraphTutorial

Put ApWW_UFO model (provided by Yiming Zhong, ymzhong@kicp.uchicago.edu) into models folder in Madgraph 

Run 
$ ./bin/mg5_aMC

To generate Standard Model Background
$ generate mu+ > e+ e+ e- ve vm~

To generate Ap 
$ import model ApWW_UFO
$ generate mu+ > Ap >  e+ e+ e- ve vm~

Show all particles in model
$ display particles

To see all Standard Model Feynman diagrams with same final state (a is photon in Madgraph syntax)
$ display diagrams  

Save work/make output folder
$output mu3e

$ launch mu3e
shower, detector etc should be set to off by default

Edit run card  to account for stopped muon beam instead of typical pp collision:
 0        = lpp1    ! beam 1 type
 0        = lpp2    ! beam 2 type
 0.0     = ebeam1  ! beam 1 total energy in GeV
 0.0     = ebeam2  ! beam 2 total energy in GeV
 
After running events, open unweighted_events.lhe. I have included two test files in the repository already. 

Jupyter notebook provided is a starter for making some plots. 

### Notes on Dark Photon Model (Ap)
Parameters for model are in models/ApWW_UFO/parameters.py. The important ones are MAp (mass), WAp (width), and GV (coupling to Standard model fermions). 
