# solidity-involving-timeStamp
Related to real time crowd sales . the time at which sales starts in online after specific timeStamp. Blockchian has its own timeStamp since 1 Thursday January 1970 , we can mention our own starting time.


pragma solidity 0.5.1;


contract MyContract {
    
    
    uint256 public peopleCount = 0;
    
    
    mapping(uint => Person) public people;

    uint256 startTime;

    modifier onlyWhileOpen() {
        require(block.timestamp >= startTime);
        _;
    }

    struct Person {
        uint _id;
        string _firstName;
        string _lastName;
    }

    constructor() public {
        startTime = 1544668513; // Update this value
    }

    function addPerson(
        string memory _firstName,
        string memory _lastName
    )
        public
        onlyWhileOpen
    {
        people[peopleCount] = Person(peopleCount, _firstName, _lastName);
    }

    function incrementCount() internal {
        peopleCount += 1;
    }
}


different modifires are used in above code. 
we must update the startTime using UNixTime in website that is blockchain had its own timestamp
