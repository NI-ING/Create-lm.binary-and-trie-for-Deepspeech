# Create lm.binary and trie for Deepspeech

this is a customize creation of lm.binary and the trie file for  **Deepspeech**

Deepspeech version : 0.6.1

## Build kenlm
sudo apt-get install libboost-all-dev libeigen3-dev
git clone https://github.com/kpu/kenlm.git ken
mkdir -p ken/build
cd ken/build
BOOST_LIBRARYDIR=/usr/lib/x86_64-linux-gnu cmake ..
make

## build lm.binary with kenlm 
./lmplz --text Ar_text.txt --arpa  Ar.arpa --o 4
./build_binary trie -q 16 -b 7 -a 64 Ar.arpa lm.binary


## build trie (native_client)
sudo ./generate_trie ../alphabet.txt ../lm.binary  trie
