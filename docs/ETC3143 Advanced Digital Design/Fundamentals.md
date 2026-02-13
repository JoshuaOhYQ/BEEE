# Chapter 0: Recap from Digital Fundamentals

## Basic Logic Gates 


### AND Gate
| NAME | SYMBOL | A | B | Y |
|------|--------|---|---|---|
| AND | $$Y = A \cdot B$$ | 0 | 0 | 0 |
| | | 0 | 1 | 0 |
| | | 1 | 0 | 0 |
| | | 1 | 1 | 1 |

### NOT Gate
| NAME | SYMBOL | A | B | Y |
|------|--------|---|---|---|
| NOT | $$Y = \overline{A}$$ | 0 | 0 | 1 |
| | | 0 | 1 | 1 |
| | | 1 | 0 | 1 |
| | | 1 | 1 | 0 |

### XOR Gate
| NAME | SYMBOL | A | B | Y |
|------|--------|---|---|---|
| XOR | $$Y = A \oplus B$$ | 0 | 0 | 1 |
| | | 0 | 1 | 1 |
| | | 1 | 0 | 1 |
| | | 1 | 1 | 0 |

### XNOR Gate
| NAME | SYMBOL | A | B | Y |
|------|--------|---|---|---|
| XNOR | $$Y = AB + \overline{A}B$$ | 0 | 0 | 1 |
| | | 0 | 1 | 0 |
| | | 1 | 0 | 0 |
| | | 1 | 1 | 1 |

---

## Boolean Expressions

**Boolean Expression**: 
$$Y = A \cdot B$$

**Truth Table**:
| NAME | SYMBOL | A | B | Y |
|------|--------|---|---|---|
| AND | $$Y = A \cdot B$$ | 0 | 0 | 0 |
| | | 0 | 1 | 0 |
| | | 1 | 0 | 0 |
| | | 1 | 1 | 1 |

### NAND Gate
| NAME | SYMBOL | A | B | Y |
|------|--------|---|---|---|
| NAND | $$Y = \overline{A} \cdot B$$ | 0 | 0 | 1 |
| | | 0 | 1 | 1 |
| | | 1 | 0 | 1 |
| | | 1 | 1 | 0 |

### NOT Gate (Alternate View)
| NAME | SYMBOL | A | B | Y |
|------|--------|---|---|---|
| NOT | $$Y = \overline{A}$$ | 0 | 1 | 0 |
| | | 0 | 0 | 1 |
| | | 1 | 1 | 0 |

---

## XOR

**XOR Gate Truth Table**
| A | B | Y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

**XOR Boolean Expression**
$$Y = A \oplus B = \overline{A}B + A\overline{B}$$