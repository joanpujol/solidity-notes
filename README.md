# Welcome to StackEdit!

## Basic Solidity
### Version
```
pragma solidity 0.8.7;
pragma solidity ^0.8.7;  // We want this version or above
pragma solidity >=0.8.7 <0.9.0;  // We want a version within this range
```
### Creating a contract
```
constract SimpleStorage {

}
```
### Types
```
bool hasFavoriteNumber = false;
uint favoriteNumber = 123;
uint8 favoriteNumber = 123;  // Number indicates ammount of bits for the variable
uint256 favoriteNumber = 123;  // uint256 == uint
string favoriteText = "five";
address myAddress = "0x12345...";
bytes32 favoriteBytes = "cat";  // Can be converted directly to string
uint favoriteNumber;  // Default value is 0
```
### Functions
```
uint256 favoriteNumber;  // Or uint256 public to open visibility

function store(uint256 _favoriteNumber) public {
    favoriteNumber = _favoriteNumber;
}
```
### Visibility
- public, visible externally and internally + creates a getter func. for state variables.
- private, only visible in current contract
- external, only visible externally
- internal, only current contract and its children have visibility
### Function modifiers
- view, just to read state from contract
- pure, can't neither read nor write from the blockchain
```
returns(uint256)  // Indicates the return type for the function
```
### Structs
```
struct People {  // Creates a type People
    uint256 favoriteNumber;
    string name;
}

People public person = People({
	favoriteNumber: 1,
	name: "Patrick"
})
```
### Arrays
```
People[] public people;
People[3] public people; 

function addPerson(string memory _name, uint256 _favoriteNumber) public {
	people.push(People(_favoriteNumber, _name));
}
```
### Memory, storage and calldata
EVM can access and store information in six places: stack, memory, storage, calldata, code and logs.
calldata: temporary data that can't be modified.
memory: temporary data tha CAN be modified.
storage: permanent variables that can be modified.
Arrays, structs and mapping require you to specify where they're going to be stored.
### Mappings
```
mapping(string => uint256) public nameToFavoriteNumber;

nameToFavoriteNumber[_name] = _favoriteNumber;
```
### Contract deploying another contract
```
import "./SimpleStorage.sol";

SimpleStorage public simpleStorage;

function crateSimpleStorageContract() public {
	simpleStorage = new SimpleStorage();
}
```
### Interacting with another contract
1.- Address
2.- ABI
```
SimpleStorage simpleStorage = SimpleStorage(address)
```
### Inheritance
for a function to be overridable you need to add the "virtual" keyword
for a function to override another you need to add the "override" keyword
```
contract A is B {

}
```