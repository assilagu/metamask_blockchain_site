# metamask_blockchain_site
Site web connecté à la blockchain via MetaMask.
// Importer ethers.js
import { ethers } from "https://cdnjs.cloudflare.com/ajax/libs/ethers/6.10.0/ethers.umd.min.js";

// Vérifier si MetaMask est installé
async function connectWallet() {
    if (window.ethereum) {
        try {
            // Demander à l'utilisateur de se connecter
            const accounts = await window.ethereum.request({ method: 'eth_requestAccounts' });
            const account = accounts[0];
            document.getElementById('walletAddress').innerText = `Adresse: ${account}`;
        } catch (error) {
            console.error("Erreur lors de la connexion à MetaMask", error);
        }
    } else {
        alert("Veuillez installer MetaMask");
    }
}

// Ajouter un écouteur d'événement sur le bouton
window.onload = function() {
    document.getElementById('connectButton').addEventListener('click', connectWallet);
};
