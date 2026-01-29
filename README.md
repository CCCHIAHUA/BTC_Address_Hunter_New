# BTC_Address_Hunter_New

(Note: Please try to run it on Linux/Unix.)

## 🚀 Bitcoin Address Hunter (Rust Edition)
    Bitcoin Address Hunter is an ultra-high-performance, multi-threaded command-line tool written in Rust. It is designed to brute-force search for Bitcoin private keys that generate specific P2PKH (Pay to Public Key Hash) addresses.
    
    Unlike standard tools that blindly generate keys, this hunter leverages ECC Point Addition (Stride) math, Physical Core Binding, and Bloom Filters to achieve search speeds significantly faster than traditional methods.

## Performance
<img src="image/rust1.png" alt="" width="400">
<img src="image/rust2.png" alt="" width="400">

## 🌟 Key Features

  1. ⚡ Math-Level Acceleration (数学级加速)
    
    The Old Way: Standard tools calculate Public = Private * G for every key. This is slow (Scalar Multiplication).
    
    The Hunter Way: We use Public_New = Public_Old + Stride_Point. Adding points on the elliptic curve is 3x-5x faster than multiplying.

  2. 🧠 Smart Strategy Modes (智能策略模式)

    Random Mode (High Entropy): Uses a Random Base + Random Stride strategy. Every thread picks a random spot, then sprints forward using a random stride. This ensures maximum coverage and unpredictability.
    
    Range Mode (Exhaustive): Uses a Sequential Stride (+1) strategy to exhaustively search every single key in a specific range (e.g., for puzzle solving).
    
  3. 🖥️ Hardware Awareness (硬件感知)

    Physical Core Detection: Automatically detects Physical Cores vs. Logical Threads. It prevents Hyper-Threading (SMT) from diluting the ALU (Arithmetic Logic Unit) power, ensuring each core runs at 100% efficiency.
    
  4. 🛡️ Security & Efficiency (安全与效率)

    Bloom Filters: Handles millions of target addresses with $O(1)$ lookup time and minimal memory.
    Entropy Reseeding: Automatically refreshes the random number generator from the OS entropy pool every 60 seconds.

## 🚀 Usage

    RUSTFLAGS="-C target-cpu=native" cargo run --release -- --target-file BTC_Puzzle_Address_71.tsv --output-file found.tsv --cores 8 --range 400000000000000000:7fffffffffffffffff

    RUSTFLAGS="-C target-cpu=native" cargo run --release -- --target-file BTC_Puzzle_Address_1-35.tsv --output-file found.tsv --cores 8 --range 1:ffffffff

## ⚖️ Disclaimer

    This software is for educational and research purposes only, or for recovering lost private keys to addresses you own. The author assumes no responsibility for any illegal use of this tool.

# Support me!

    BTC：
    bc1q8np6jeglpgju7ex5z6mvsmllzwhxqzytymwlv7
    
    LTC：
    LTzSaAtCvAhjRYJHSFPjmqustpYRCypXxL
    
    USDT、USDC:
    
    TRC20:
    TXdmK7Dd5UjWbfutoiHDGLBub4hYjbWteg
    
    Arbitrum One:
    0xceF4D9ae284AB6f836dB20C851c3631fe2eCCc72
    
    Aptos：
    0x3f7d7a503dcd26915d93af18f3deaf7108a29b7e517e627782882d313835f00b
