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
manual — [Руководство.md](Руководство.md). The screenshots show what the
windows actually look like; the same text in Russian follows below.

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

<div align="center">— • —</div>

# EMzonar

**Проволочные антенны методом моментов.** Вы описываете антенну — файлом NEC
или просто замыслом, — а в ответ получаете числа и картинки: входной импеданс
и КСВ, токи по проводам, диаграмму направленности, полосу по частоте и то, что
наведёт на антенне приходящая волна.

![EMzonar](Screenshots/диаграмма-яги.png)

Ядро — семейства NEC-2, написано с нуля на C++20; интерфейс свой. Над
настоящей землёй импеданс считается **точно**, интегралами Зоммерфельда — в том
числе у антенны, СТОЯЩЕЙ на грунте, где обычное приближение образом ломается.

| | |
|---|---|
| ![развёртка](Screenshots/развёртка-полоса.png) | ![этажерка](Screenshots/этажерка.png) |
| **Полоса числом.** `--sweep --swr 2` рисует R, X, КСВ и усиление по частоте и печатает, где КСВ не хуже порога: здесь 133…147 МГц, 10 % от середины. | **Решётки.** Строки и столбцы одинаковых антенн, питаются все; импеданс печатается для КАЖДОЙ — крайние видят соседей с одной стороны, средние с обеих. |

## Запуск

```sh
./emzonar                          пустое окно
./emzonar антенна.nec              окно: структура, карточки, состояние
./emzonar антенна.nec --check      провода, сегменты, габариты, частота
./emzonar антенна.nec --impedance  входной импеданс, КСВ, КПД
./emzonar антенна.nec --pattern    диаграмма направленности
./emzonar --generate вых.nec --kind yagi --elements 3 --freq 145 --wire 0.004
```

Нужен Linux x86-64 и SDL2. Рядом с бинарём должен лежать каталог `assets` —
из него берётся шрифт. Как всем этим пользоваться — **[Руководство.md](Руководство.md)**.

## Готовые антенны

В `Examples/` лежит 6 файлов: волновой канал, двойной квадрат, штырь над
идеальной землёй и он же СТОЯЩИЙ на настоящем грунте с радиалами, решётка 4×1 и
развёртка по частоте. У каждого в первых строках `CM` сказано, зачем он и на
что смотреть.

## Лицензия

MIT — [LICENSE](LICENSE). Канонический текст MIT говорит о «программе **и
сопутствующих файлах документации**», поэтому руководство, снимки и примеры —
на тех же условиях.

Всего 1,7M. Бинарь обрезан (`strip`), 1,4M.

Собрано 07.09.2026.
