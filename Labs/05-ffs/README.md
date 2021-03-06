# Lab 5

## Preparation tasks (done before the lab at home)

1. Characteristic equations and truth tables for D, JK, T flip-flops where `q(n)` represents main output value before the clock edge and `q(n+1)` represents output value after the clock edge.

   ![](images/equation.png)
   
   **D-type FF**
   | **clk** | **d** | **q(n)** | **q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-- |
   | ![rising](images/up.png) | 0 | 0 | 0 | `q(n+1)` has the same level as `d` |
   | ![rising](images/up.png) | 0 | 1 | 0 | Output did not change |
   | ![rising](images/up.png) | 1 | 0 | 1 | `q(n+1)` has the same level as `d` |
   | ![rising](images/up.png) | 1 | 1 | 1 | Output did not change |

   **JK-type FF**
   | **clk** | **j** | **k** | **q(n)** | **q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-: | :-- |
   | ![rising](images/up.png) | 0 | 0 | 0 | 0 | Output did not change |
   | ![rising](images/up.png) | 0 | 0 | 1 | 1 | Output did not change |
   | ![rising](images/up.png) | 0 | 1 | 0 | 0 | Reset output value |
   | ![rising](images/up.png) | 0 | 1 | 1 | 0 | Reset output value |
   | ![rising](images/up.png) | 1 | 0 | 0 | 1 | Set output value |
   | ![rising](images/up.png) | 1 | 0 | 1 | 1 | Set output value |
   | ![rising](images/up.png) | 1 | 1 | 0 | 1 | Toggle output value |
   | ![rising](images/up.png) | 1 | 1 | 1 | 0 | Toggle output value |

   **T-type FF**
   | **clk** | **t** | **q(n)** | **q(n+1)** | **Comments** |
   | :-: | :-: | :-: | :-: | :-- |
   | ![rising](images/up.png) | 0 | 0 | 0 | Output did not change |
   | ![rising](images/up.png) | 0 | 1 | 1 | Output did not change |
   | ![rising](images/up.png) | 1 | 0 | 1 | Toggle output value |
   | ![rising](images/up.png) | 1 | 1 | 0 | Toggle output value |

<a name="part1"></a>

### Flip-flops

1. Listing of VHDL architecture for T-type flip-flop:

```vhdl
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity t_ff_rst is
    Port ( clk   : in  STD_LOGIC;
           rst   : in  STD_LOGIC;
           t     : in  STD_LOGIC;
           q     : out STD_LOGIC;
           q_bar : out STD_LOGIC);
end t_ff_rst;

architecture Behavioral of t_ff_rst is
    signal s_q : std_logic;
begin

    p_t_ff_rst : process(clk)
    begin
        if rising_edge(clk) then  -- Synchronous process

            -- USE HIGH-ACTIVE RESET HERE
            if (rst = '1') then
                s_q <= '0';
            elsif (t = '0') then
                s_q <= s_q;
            else
                s_q <= not s_q;
            end if;
        end if;
    end process p_t_ff_rst;
    
    q     <= s_q;
    q_bar <= not s_q;
end architecture Behavioral;
```

2. Screenshot with simulated time waveforms. Try to simulate both flip-flops in a single testbench with a maximum duration of 200 ns, including reset. Always display all inputs and outputs (display the inputs at the top of the image, the outputs below them) at the appropriate time scale!

   ![](images/sim1.PNG)
   
   OR
   
   ![](images/sim2.png)

### Shift register

1. Image of the shift register `top` level schematic by hand:

   ![](images/top.png)
