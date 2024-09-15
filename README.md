# metaschool
zkverify proof
Proof Submission TutorialWelcome back! In this lesson, we’re going to dive in and submit proofs for verification to zkVerify, walking through each step from start to finish.Let’s get started!Before we startIf you are using Mac or Linux, feel free to skip this section and directly jump onto the ‘Clone Repository’ section. But in case you are using Windows, you need to install Windows subsystem for Linux (or WSL). You can do so by using the simple command:
wsl --install
Make sure that if you are using Windows, use WSL to work with this project. Now let’s get started!Clone GIT repositoryFirst of all, open the terminal/CLI in your system and clone the repository using the following command.
git clone https://github.com/0xmetaschool/zkverify-proofverification.git

cd zkverify-proofverification
Do some installationsNow, we need to do some installations. So, run the following commands one by one.Install the snarkjs latest version:
npm install -g snarkjs@latest
If you have already installed it you might see something like this.Note: If you face permission issues with the installation add sudo before the command(only for Mac User)Install Rust. If prompted to ask about different installation setups please press “Enter” to just install the default ones.
curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
Here’s what it looks like for us on macOS:Now, we need to clone the circom git repository to do the installations. So, run the following command:
git clone https://github.com/iden3/circom.git
You will find the circom folder in your zkverify-proofverification folder.Move to circom folder and run the following cargo install command.
cd circom

cargo install --path circom

cd ..
Here’s what it looks like for us on macOS.Run the .sh fileNow, we need to run the circuit_setup.sh file. So, run the following commands.
sudo chmod +x circuit_setup.sh

./circuit_setup.sh
When asked to write any text, just type any text for example Entropy.After running the command, you’ll see that many new files namely proof.json, public.json, and verification_key.json are generated as shown below:Convert to zkVerify formatWe need to convert JSON files to zkVerify format to submit them for proof verifications. Follow the following steps to do so.Run the following commands one by one to set up the snarkjs2zkv.
git clone https://github.com/HorizenLabs/snarkjs2zkv.git

cd snarkjs2zkv

npm install
Run the following command and replace the <path_to_proof.json> path with the complete path of the proof.json file.
node snarkjs2zkv convert-proof <path_to_proof.json> -o proof_zkv.json
Run the following command and replace the <path_to_verification_key.json> path with the complete verification_key.json path.
node snarkjs2zkv convert-vk <path_to_verification_key.json> -o verification_key_zkv.json
Run the following command to convert the public.json file. Replace the <path_to_public.json> path with the complete path of the public.json file.
node snarkjs2zkv convert-public <path_to_public.json> -o public_zkv.json -c bn128
After completing these steps, you will see three new files generated in snarkjs2zkv called proof_zkv.json, public_zkv.json, and verification_key_zkv.json as below:That’s a wrapPhew! That was a lot but you did great! Next, we need to send the proofs we have to zkVerify for verification. See you in the next lesson!
