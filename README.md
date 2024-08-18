# Avalanche_advanced_HyperSDK

HyperSDK is a powerful framework that streamlines the development of blockchain applications on the Avalanche network. It provides essential tools and libraries to build custom blockchain protocols with ease, focusing on speed, scalability, and security. With HyperSDK, developers can quickly deploy decentralized applications, making the development process more efficient and less complex.

## Description
HyperSDK is better than using a traditional subnet on Avalanche because it offers a more streamlined and efficient development process for creating custom blockchain applications. While subnets allow for customization, HyperSDK goes further by providing optimized tools and libraries specifically designed to enhance transaction processing speed, scalability, and security. It reduces the complexity and time required to build and deploy decentralized applications, making it a more efficient choice for developers who want to leverage the full potential of the Avalanche network without getting bogged down in the intricacies of subnet configuration and management.

## Getting Started
- Vedio explanation of the project work.
https://www.loom.com/share/aedc4042f6af461f85bbe9d79d24ebe8?sid=df80ce4f-169e-476c-bfc8-e117d0396204
### Installing
- For creating a custom virtual machine we first need to install the go compiler [https://go.dev/doc/install] from here.
- Then we have to run {go mod tidy} to normalize all the dependencies in our project folder.
-  Afterwards we have to configure the project constants by going on consts/consts.go then we have to add the missing code in the registry/registry.go
  // TODO: register action: actions.CreateAsset
		consts.ActionRegistry.Register(&actions.CreateAsset{}, actions.UnmarshalCreateAsset, false),
		// TODO: register action: actions.MintAsset
		consts.ActionRegistry.Register(&actions.MintAsset{}, actions.UnmarshalMintAsset, false),
- Then check the go compiler version of ours
  
  ![WhatsApp Image 2024-08-10 at 17 09 18_81333ac5](https://github.com/user-attachments/assets/483270b6-d985-4240-ad5f-7e7098e3bbee)
  
- Then [./scripts/run.sh;] run this command for launching the subnet and for one run this command also [Run MODE="run-single" ./scripts/run.sh].
- To interact with the tokenvm, implement the token-cli. Next, we'll need to build this. by using this command[./scripts/build.sh]
- This command will put the compiled CLI in ./build/token-cli._
- Lastly, we'll need to add the chains that we created and the default key to the token-cli. we can use the following commands [./build/token-cli key import demo.pk]
  [./build/token-cli chain import-anr]

### Executing program
- Firstly we are going to create our asset for that we have to run command [./build/token-cli action create-asset] then it will give the address and chainID , then asks for the metadata where we have to provide our chain name.
  
<img width="1083" alt="Screenshot 2024-08-12 at 7 54 28 PM" src="https://github.com/user-attachments/assets/0869ce40-7d93-43b2-ae4e-042724f2e4e2">

- After successful creation we are going to mint using the following command [./build/token-cli action mint-asset] then after running this command we have to provide our assetID which is similar to our txID (so copy and give it to the assetID) then it will ask for the value so give some and type 'y' for confirmation.

 <img width="1047" alt="Screenshot 2024-08-12 at 7 54 37 PM" src="https://github.com/user-attachments/assets/a3fa8ef7-688d-4faa-85d4-46ef33c60cb6">

- Then we will be going to check/view our balance using  command [./build/token-cli key balance] here also we have to give the assetID which is similar to the txID.

  <img width="1087" alt="Screenshot 2024-08-12 at 7 54 10 PM" src="https://github.com/user-attachments/assets/b7a1a427-3695-4bcc-baab-119ac7d84144">


- We are having some command which we can also  use for different functionalities
./build/token-cli action create-order
./build/token-cli action fill-order

<img width="1201" alt="Screenshot 2024-08-12 at 7 55 13 PM" src="https://github.com/user-attachments/assets/87a5151d-f3b9-47b9-9e85-d31a6d2d6c81">

./build/token-cli action close-order
./build/token-cli chain watch
./build/token-cli chain watch
./build/token-cli action export
./scripts/tests.load.sh
./scripts/tests.disk.sh

- At the end for closing our Local Avalanche Network , we have to run [killall avalanche-network-runner]

## Authors
Surbhi Priya

Email - psurbhi237@gmail.com
