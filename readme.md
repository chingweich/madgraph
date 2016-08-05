git clone git@github.com:cms-sw/genproductions.git genproductions
cd genproductions/bin/MadGraph5_aMCatNLO/
bash
source gridpack_generation.sh interactive
cd MG5_aMC_v2_2_2/models
cp /afs/cern.ch/cms/generators/www/MonoHiggs_Zp2HDM_v1.4.tgz
tar xvzf MonoHiggs_Zp2HDM_v1.4.tgz
mv Zp2HDM_v1.4 Zp2HDM
cd ..
./bin/mg5_aMC proc_card.dat
cd ZphA0/Cards/
cp ../../run_card.dat .
cp ../../param_card.dat .
cp ../../makeXsec.sh .

changing 263400 to 263000 in run card #L52
cd ..
./bin/generate_events -f
cd Cards

./makeXsec.sh >& xsec.txt
root -l makeXsec.C++