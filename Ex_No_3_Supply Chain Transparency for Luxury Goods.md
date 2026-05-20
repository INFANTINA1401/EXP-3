# NAME: INFANTINA MARIA L
# REG NO: 212223100013
# EX: Supply Chain Transparency for Luxury Goods
# Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
# Algorithm:
The manufacturer records product creation details on-chain.


The product moves through different supply chain checkpoints.


The ownership of the product can be transferred securely.


Buyers can verify the product’s authenticity.


# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
# Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.
<img width="1918" height="972" alt="Screenshot 2026-05-20 115015" src="https://github.com/user-attachments/assets/25d9f172-f6f5-4cdd-98fd-eb2b9d262efc" />

<img width="1918" height="960" alt="Screenshot 2026-05-20 115044" src="https://github.com/user-attachments/assets/1c3b0b55-2977-4483-ae10-d22de71b90ad" />

Ownership is transferred at every checkpoint.
<img width="1913" height="962" alt="Screenshot 2026-05-20 115128" src="https://github.com/user-attachments/assets/506d2830-dbc8-4362-a442-f6f20736166f" />


Buyers can check the authenticity before purchasing.
<img width="1918" height="965" alt="Screenshot 2026-05-20 115146" src="https://github.com/user-attachments/assets/25329305-567f-4c27-a38a-e87f33041de4" />

# High-Level Overview:
Helps prevent counterfeit luxury goods.
Teaches real-world supply chain use cases.

# RESULT : 
Thus a smart contract that tracks the supply chain of luxury goods ensuring authenticaly is executed sucessfully
