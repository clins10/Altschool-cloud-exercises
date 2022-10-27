## EXERCISE 10: 

**TASK:**
### Given the IP Address below:

```bash
 193.16.20.35/29
```


###  __WHAT IS__: 

    1. Network IP?
    2. Number of Hosts?
    3. Range of IP addresses?
    4. Broadcast IP from the this subnet? 
    
### **INSTRUCTION:**

```bash
Submit all your answers as a markdown file the this exercise.
```

## SOLUTION:

## 1. **The Network IP:**

#### To calcualate the *Network IP* we'll first have to get the binary form of the given *IP* and its *Subnet* Here our *subnet* is **29** *up bits (1s)* and **3** *down bits (0s)* which sums up to the *32* the total allowed bits in an *IP*

####    *up bits* === *network bits* designated with *1s*
####    *down bits* === *Host bits* designated with *0s*
    
```bash
8 => 11111111
8 => 11111111
8 => 11111111
5 => 11111000

29 => 11111111.11111111.11111111.11111000
```
#### Converting the *IP* values from **decimal** to **binary**
    
```bash
193 =>  11000001
16 =>   00010000
20 =>   00010100
35 =>   00100011

193.16.20.35 => 11000001.00010000.00010100.00100011
``` 
### NB: The *Network Address* is the **logical AND** of the **IP address** and **subnet(network mask)** when they are both converted to binary form.

#### 1.1. **Logical AND** of the *IP* and *Subnet* in **binary** form

```bash
193.16.20.35 => 11000001.00010000.00010100.00100011
29           => 11111111.11111111.11111111.11111000

                -----------------------------------
Logical AND =>  11000001.00010000.00010100.00100000
                -----------------------------------           
``` 
#### Now to get the *Network IP* we'll easily convert the **logical AND** value gotten from the above operation to *decimal*.

```bash
11000001.00010000.00010100.00100000 =>  193.16.20.32
```
#### 1.2. **The Network IP** of *193.16.20.35/29* is **193.16.20.32**

## 2. **Number of Hosts:**

#### To calculate the number of *Host* that can assigned on *193.16.20.35/29*, let's use the formaula below:
```bash
Max Number of hosts = 2^(32 - netmask_length) - 2

netmask_length = subnet_value
```

### **NB: The "-2" in the formula is the reserved address for Network and Broadcast Addresses**

```bash
Max Number of hosts = 2^(32 - 29) - 2
Max Number of host = 6
```
#### The Maximun number of hosts that can be assigned **IPs** on the is **6**

## 3. **The Broadcast IP:**

#### To get the *Broadcast IP*, the *host bits* of the *subnet value* are converted to **1s** and the *network bits* are converted to **0s**

```bash
29 => 11111111.11111111.11111111.11111000

    -----------------------------------
    00000000.00000000.00000000.00000111
    -----------------------------------
```
#### Now to get the *Broadcast IP* we'll easily perform a **logical OR** operation on the **IP address** and *new value of our subnet(29)*.

```bash
193.16.20.35        =>  11000001.00010000.00010100.00100011
new subnet value    =>  00000000.00000000.00000000.00000111
    
                        -----------------------------------
Logical OR         =>   11000001.00010000.00010100.00100111
                        -----------------------------------
```

#### Now to get the *Broadcast IP* we'll easily convert the **logical OR** value gotten from the above operation *decimal*.

```bash
11000001.00010000.00010100.00100111 =>  193.16.20.39
```

#### The *Broadcast IP* of *193.16.20.35/29* is **193.16.20.39**

## 4. **The Range of IP addresses:**

#### The *Range of IP addresses* is the values between the *Network IP* and the *Broadcast IP*. That is **193.16.20.32** - **193.16.20.39**

#### Hence The *Range of IP addresses*  is
    
```bash
193.16.20.33
193.16.20.34
193.16.20.35
193.16.20.36
193.16.20.37
193.16.20.28
```

