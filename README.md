# EMzonar

**Wire antennas by the method of moments.** You describe an antenna — as a NEC
file or simply by intent — and get numbers and pictures back: the feedpoint
impedance and SWR, the currents along the wires, the radiation pattern, the
band over frequency, and what an incoming wave induces on it.

![EMzonar](Screenshots/диаграмма-яги.png)

The kernel is of the NEC-2 family, written from scratch in C++20; the interface
is its own. Over real ground the impedance is computed **exactly**, by
Sommerfeld integrals — including for an antenna standing directly **on** the
soil, where the usual image approximation breaks down.

| | |
|---|---|
| ![sweep](Screenshots/развёртка-полоса.png) | ![array](Screenshots/этажерка.png) |
| **The band as a number.** `--sweep --swr 2` plots R, X, SWR and gain over frequency and prints where the SWR stays below the limit — here 133…147 MHz, 10 % of the centre. | **Arrays.** Rows and columns of identical antennas, all fed; the impedance of EACH one is printed, because the outer ones see neighbours on one side and the inner ones on both. |

## Running it

```sh
./emzonar                          an empty window
./emzonar antenna.nec              the window: structure, cards, state
./emzonar antenna.nec --check      wires, segments, extents, frequency
./emzonar antenna.nec --impedance  feedpoint impedance, SWR, efficiency
./emzonar antenna.nec --pattern    radiation pattern
./emzonar --generate out.nec --kind yagi --elements 3 --freq 145 --wire 0.004
```

Linux x86-64 and SDL2. The `assets` directory must sit beside the binary — the
font is taken from it.

**Note on language:** the program's interface is **in Russian**, and so is the
manual — [Руководство.md](Руководство.md). This page is the only English text
here.

## Ready-made antennas

`Examples/` holds 6 files — a Yagi, a two-element quad, a whip over perfect
ground and the same whip standing on real soil with radials, a 4×1 array, and a
frequency sweep. Each says in its first `CM` lines what it is for and what to
look at.

## License

MIT — see [LICENSE](LICENSE). The MIT text covers "the Software **and
associated documentation files**", so the manual, the screenshots and the
example antennas are under the same terms.

1,7M in total. The binary is stripped, 1,4M.

Built on 07.09.2026.
