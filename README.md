# COS-226-Hash-Table-Homework-Umangga_silwal
Here my Repository for today homework

# COS 226 - Hash Something Out

## Overview

This project tests different hash table implementations using a dataset
of 15,000 movie records. Two hash tables were created:

- Movie titles as keys
- Movie quotes as keys

The goal was to reduce wasted space and collisions while keeping
construction time reasonable.

Five different approaches were tested.


## Attempt 1 - Linked List + Poor Hash

The first attempt used linked-list chaining with a simple hash function.
The hash function adds the Unicode values of each character in the key.

### Title Hash Table
- Movies: 15,000
- Wasted buckets: 11,244
- Collisions: 45,508
- Construction time: 0.033 seconds

### Quote Hash Table
- Movies: 15,000
- Wasted buckets: 12,277
- Collisions: 56,718
- Construction time: 0.047 seconds

This method had a large amount of wasted space and many collisions.
The simple hash function did not distribute the keys very evenly.


## Attempt 2 - Linked List + Good Hash

The second attempt kept linked-list chaining but changed the hash function.
The new hash function multiplies the running total by 31 before adding
the Unicode value of each character.

### Title Hash Table
- Movies: 15,000
- Wasted buckets: 6,991
- Collisions: 11,896
- Construction time: 0.059 seconds

### Quote Hash Table
- Movies: 15,000
- Wasted buckets: 5,562
- Collisions: 7,578
- Construction time: 0.491 seconds

This greatly reduced collisions compared with Attempt 1.



## Attempt 3 - Linear Probing + Poor Hash

The third attempt changed the collision method to linear probing while
using the original poor hash function.

### Title Hash Table
- Movies: 15,000
- Wasted slots: 0
- Collisions: 87,848,466
- Construction time: 15.877 seconds

### Quote Hash Table
- Movies: 15,000
- Wasted slots: 0
- Collisions: 92,777,935
- Construction time: 16.220 seconds

Although there was no wasted space, the number of collisions became
extremely large. This shows that linear probing performs poorly when
combined with a poor hash function.


## Attempt 4 - Linear Probing + Good Hash

The fourth attempt used linear probing with the improved hash function.

### Title Hash Table
- Movies: 15,000
- Wasted slots: 0
- Collisions: 1,623,606
- Construction time: 0.313 seconds

### Quote Hash Table
- Movies: 15,000
- Wasted slots: 0
- Collisions: 1,679,845
- Construction time: 0.732 seconds

The improved hash function dramatically reduced collisions compared
with Attempt 3.


## Attempt 5 - Linear Probing + Good Hash + Larger Capacity

The fifth attempt kept the good hash function and linear probing but
increased the table capacity from 15,000 to 20,011.

The larger capacity gives the table more empty slots and reduces
clustering during linear probing.

### Title Hash Table
- Movies: 15,000
- Wasted slots: 5,011
- Collisions: 42,451
- Construction time: 0.057 seconds

### Quote Hash Table
- Movies: 15,000
- Wasted slots: 5,011
- Collisions: 22,076
- Construction time: 0.516 seconds

This greatly reduced the number of collisions compared with Attempt 4,
although it increased wasted space.


## Reflection

Attempt 1 showed that a simple hash function can produce many
collisions. Attempt 2 improved the distribution of keys and greatly
reduced collisions.

Attempt 3 showed that linear probing can perform very poorly when the
hash function produces a poor distribution. The collision count and
construction time were much higher than the other attempts.

Attempt 4 improved the results by combining linear probing with the
better hash function.

Attempt 5 was the most effective linear-probing optimization. Increasing
the table capacity created some wasted space, but it greatly reduced
collisions. Compared with Attempt 4, title collisions decreased from
1,623,606 to 42,451, while quote collisions decreased from 1,679,845
to 22,076.

Overall, Attempt 2 was the best method based on the lowest number
of collisions. Attempt 5 was the best linear probing
optimization** because it greatly reduced collisions while keeping
construction time reasonable.
