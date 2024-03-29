# Simple Ciphers and Keyspaces

In this activity, you'll practice using each of the classic ciphers discussed in lecture, and analyze their keyspaces to "rank" them in terms of strength.

## Instructions

### Caesar Cipher

- Use the Caesar Cipher with `k = 3` to encrypt the message: `attack at dawn!`
    - dwwdfn dw gdzq

- How big is the keyspace of the Caesar Cipher? I.e., how many possible keys can you use?
    - 26 possible keys

- By corollary: How many keys do you have to try to attack this cipher via brute force?
    - 25

### General Substitution Cipher

In the General Substitution Cipher, any letter can be replaced by any other. In other words, instead of shifting each letter by one space, we'll replace each letter with some arbitrary other letter.

For example:

```
# Original Alphabet
ABCDEFGHIJKLMNOPQRSTUVWXYZ

# Substituted Alphabet
QWERTYUIOPASDFGHJKLZXCVBNM
```

#### Questions

- The above "Substituted Alphabet" is just one example of the possible substitued alphabets we could have created. How many such alphabets are there?
  
  - 26!

- **Bonus**: To find a precise answer, consider the following questions.
  - Assume you want to create a substituted alphabet, starting from scratch. In the example above, we replaced `A` with `Q`. How many letters could you choose to encrypt the letter `A`?
  - Let's say we stick with the transformation `A` -> `Q`. Now, how many letters do you have available to encrypt the letter `B`?
  - What about the letter `C`? `D`? Etc., all the way throuh `Z`?
  - Multiply all the numbers from the questions above. This product is the size of the keyspace. Is this as big as you expected?
    - **Hint**: The factorial operator is helpful here: <https://en.wikipedia.org/wiki/Factorial>

### Transposition Cipher

- Use the following encryption rule to encrypt the message `attack at dawn!!`:

    ```bash
        | 1 2 3 4 |
    E = |         |
        | 2 4 1 3 |
    ```

    - taat cakdta !w!


- The key space of the transposition cipher depends on the block size. In particular, the larger the block, the larger the key space. How big does the block size need to be for the transposition cipher to be just as strong as the Generalized Substitution Cipher?

    - The block size needs to be equal to 26

### Questions

- Rank the above three ciphers from weakest to strongest.

    - Caesar
    - Transposition (with `k <= 26`)
    - Generalized Substitution
    - Transposition (with `k > 26`)

### Extension

Consider the "substituted alphabets" from above, in the case of the Generalized Substitution Cipher. 

Each possible substituted alphabet is a random arrangement of letters. These random arrangements are called _permutations_. As you see from the comparison of keyspaces between the Caesar and Generalized Substitution Ciphers, permutations add considerable strength to ciphers.

In modern algorithms, _substitutions_ and _permutations_ are used together to make stronger algorithms.
- First, we _substitute_ data, using something like the Generalized Substitution Cipher.
- Then, we _permute_ the substituted data.
- Finally, we repeat this process a large number of times to generate a complicated encrypted string.

The details of how these substitutions and permutations are implemented are beyond the scope of this course, but it's important to understand that these operations lead to increased complexity and, therefore, improvements in a cipher's crytopgrahic strength.
