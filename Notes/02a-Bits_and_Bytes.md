# Bits and Bytes

### Transistors

A computer is an *electronic programmable calculating machine*. At a base level, any operation a computer can perform is executed by
electrical signals passing through circuits that implement logical operations. These circuits are built from *transistors*.

You can think of a transistor as a switch.

``` 
          power
            |
            |
            |  collector
          --
  base   |
---------|
         |
          --
            |
            v  emitter
            |
            |
          ground
```

When current is applied to the base terminal, the transistor switches "on" and allows current to flow from the collector to the 
emitter.

Multiple transistors may be combined together to create logic circuits that implement the basic logical operations AND, OR, and NOT. 
These basic functions can be further combined to design complex circuits that add, compare, switch, store, and perform all of the 
other tasks that are required for a computer to operate.

We won't actually study the design of digital logic circuits in the course &mdash; Dr. Carrington covers logic design as part of 
Applied Discrete Mathematics. For now, we'll just accept (using our powers of abstraction) that we have the capability to create the 
basic physical hardware of a computer.

### Bits

We can recognize two basic states in any digital logic circuit:
  
  1. The *presence* of a significant electrical voltage
  2. The *absence* of any significant electrical voltage

This recognition gives rise to the concept of a *binary digit* or ***bit***.

A single bit represents a basic unit of information having only two possible values, which we'll label as 0 (representing falseness or
absence) and 1 (representing truth or presence).

The meaning of "significant electrical voltage" depends on the technology used to implement the system's logic gates. It's common for 
a logical level of 0 to be represented by a voltage close to 0 and for a logical level of 1 to be represented by a voltage of +3.5 V.

### Everything is Bits

**All information in a computer system, regardless of its source, type, or use is represented as a sequence of bits**.

Numbers, text strings, program instructions, images, audio, video, web pages, spreadsheets, databases, and every other kind of
information used by any computer program must ultimately be encoded as sequences of bits.

This truth has an important corollary: the meaning of any particular string of bits depends on its context. For 
example, the 32-bit sequence

```
01100101011001100110011101101000
```

could represent a single signed `int`, or an unsigned `int`, or four `char` values, or two `short` values, or a machine language
instruction, or a `float`. The interpretation of the bit string depends upon the context in which it's used.

### Bits and Powers of 2

Suppose that you have a grouping of *N* bits. How many distinct combinations can that grouping represent? Each bit may take one of two
values, 0 or 1, so there are two choices for each of the *N* positions.

  - A single bit can encode two values (0 and 1)
  - Two bits can encode four values (00, 01, 10, and 11)
  - Three bits can encode eight values (000, 001, 010, 011, 100, 101, 110, and 111)
  
In general, an *N* bit sequence can represent *2^N* distinct values.

Here are all the powers of 2 from 0 to 20:

```
2^0  = 1
2^1  = 2
2^2  = 4
2^3  = 8
2^4  = 16
2^5  = 32
2^6  = 64
2^7  = 128
2^8  = 256
2^9  = 512
2^10  = 1024
2^11  = 2048
2^12  = 4096
2^13  = 8192
2^14  = 16384
2^15  = 32768
2^16  = 65536
2^17  = 131072
2^18  = 262144
2^19  = 524288
2^20 = 1048576
```

For back-of-the-envelope calculations, it's helpful to remember that 2^10 is a little bigger than 1000 and that 2^20 is a little 
bigger than 1 million (slightly less than 5% larger, in fact). This pattern holds at higher values, although it becomes less accurate:
2^30 is about 7.5% larger than 1 billion and 2^40 is about 10% larger than 1 trillion.

### Bytes and Larger Units

Even if all information in a compuer is ultimately a sequence of bits, it's inconvenient to reason about and work with
individual 0/1 values. All CPUs are designed to access and manipulate larger groups of bits.

The most important unit is the ***byte***, which is defined to be 8 bits. A single byte can encode 256 distinct values. Most CPUs and
memories, as well as the memory model of the C programming language, treat a single byte as the basic unit of access.

Early computers had variable concepts of how large a byte should be, often treating the size of a single text 
character as the basic unit of access. The industry didn't standardize on the 8-bit byte until IBM introduced the successsful System/360 mainframe in the 1960s.

In C, the `char` data type represents a single 8-bit byte. We wil explore the relationship between bytes and text characters in a
future note.
