# Funkce

Známe spoustu matematických operací, které se zapisují symboly – třeba plus
a minus.
Python se snaží používat stejné symboly jako matematici:

* 3 + 4
* <var>a</var> - <var>b</var>

S násobením a dělením už je to složitější,
matematický zápis se na běžné klávesnici nedá napsat:

* 3 · 4
* ¾

V Pythonu si ale pořád vystačíme se symbolem, byť trochu jiným – `*`, `/`.

Matematici ale píšou na papír, a tak si můžou dovolit vymýšlet stále
zajímavější klikyháky, které se pak na klávesnici píšou dost špatně:

* <var>x</var>²
* <var>x</var> ≤ <var>y</var>
* sin θ
* Γ(<var>x</var>)
* ∫<var>x</var>
* |<var>s</var>|
* ⌊<var>x</var>⌋
* <var>a</var> ★ <var>b</var>
* <var>a</var> ⨁ <var>b</var>

Ne že by neexistovaly programovací jazyky,
na které je potřeba speciální klávesnice.
Třeba program v jazyce APL laik jednoduše ani nenapíše, ani nepřečte:

<!--z http://catpad.net/michael/apl/ -->
```plain
⍎’⎕’,∈Nρ⊂S←’←⎕←(3=T)∨M∧2=T←⊃+/(V⌽”⊂M),(V⊖”⊂M),(V,⌽V)⌽”(V,V←1¯1)⊖”⊂M’
```

Expert v APL může být vysoce produktivní, ale Python se zaměřuje spíš na to,
aby se dal snadno naučit.
A tak používá symboly jen pro ty nejčastější operace.
Operátorů, které využívají symboly, je tak málo, že už jich zhruba půlku znáš!

> [note]
> Pro zajímavost, tady jsou všechny – i ty co ještě neznáš:
>
> <div>
>     <code>==</code> <code>!=</code>
>     <code>&lt;</code> <code>&gt;</code>
>     <code>&lt;=</code> <code>&gt;=</code>
>     <code class="text-muted">:=</code>
>     <code class="text-muted">|</code> <code class="text-muted">^</code>
>     <code class="text-muted">&amp;</code>
>     <code class="text-muted">&lt;&lt;</code> <code class="text-muted">&gt;&gt;</code>
>     <code>+</code> <code>-</code>
>     <code>*</code> <code class="text-muted">@</code> <code>/</code>
>     <code>//</code> <code>%</code>
>     <code class="text-muted">~</code>
>     <code>**</code>
>     <code class="text-muted">[ ]</code> <code class="text-muted">( )</code>
>     <code class="text-muted">{ }</code>
>     <code class="text-muted">.</code>
> </div>

Všechno ostatní vyjádříme slovně.


## Délka řetězce

Jedna operace, na kterou v Pythonu není symbol, je zjištění délky řetězce.

Místo symolu má název.
Jmenuje se `len` (z angl. *length*, délka):

```python
slovo = 'Ahoj'
delka = len(slovo)      # Vypočítání délky
print(delka)
```

Ono `len(slovo)` je *výraz*, který něco udělá podle hodnoty `slovo`
a výsledek dá k dispozici.

Stejně fungují výrazy s operátorem – třeba výraz `a + b` něco
udělá podle hodnot `a` a `b` a výsledek dá k dispozici.

Výsledek výrazu pak může zbytek programu dál zpracovat:
náš program ho přiřadí do proměnné (pomocí `delka =`).

Název `len` označuje *funkci* a výrazu `len(s)` se říká *volání funkce*.
Pojďme si taková volání popsat trochu zevrubněji.

> [note] Pro matemati{{gnd('', 'č', both='')}}ky
> Máš-li rád{{a}} matematiku, dej pozor!
> Funkce v Pythonu je něco jiného než funkce v matematice,
> i když se stejně jmenují a podobně zapisují.
> Pythonní funkce může např. dávat pro jeden argument různé hodnoty.


## Volání funkcí

Funkci zavoláš *jménem*, například `len`.

Za jméno funkce patří závorky,
do nichž uzavřeš *argument* (neboli *vstup*) funkce.
To je informace, se kterou bude funkce
pracovat – třeba `len` ze svého argumentu vypočítá délku.

Volání funkce je výraz a jeho výsledek, takzvaná *návratová* hodnota
(angl. *return value*) se dá třeba přiřadit do proměnné.

{{ figure(img=static('call-anatomy.svg'), alt="Diagram volání funkce") }}


### Procedury

Možná sis všiml{{a}}, že jednu funkci už voláš déle: `print("Ahoj!")`
je taky volání funkce.
Stejně jako `len` dostává `print` v závorkách argument – hodnotu, se
kterou pracuje.
Liší se ale návratovou hodnotou.

Funkce `print` sice něco *udělá* – vypíše text
na obrazovku – ale nevrátí žádný smysluplný výsledek, který by zbytek programu
mohl dál zpracovat.

Funkcím, které nic nevrací (jen něco udělají) se občas říká *procedury*.
V Pythonu není hranice mezi „normální“ funkcí a procedurou příliš ostrá,
ale přesto se hodí tento koncept znát.
Pár příkladů:

* Funkce, která vybere náhodné číslo, je „normální“.
  Svůj výsledek vrátí; program s ním může dál pracovat.
* Funkce, která vykreslí na obrazovku kolečko, je *procedura*.
  Žádnou zajímavou hodnotu programu nevrací.
* Funkce, která spočítá průměrný věk obyvatelstva podle informací ze sčítání
  lidu je „normální“. Svůj výsledek vrátí a program s ním může dál pracovat.
* Funkce, která přehraje písničku reproduktorem, je *procedura*.
  Nic zajímavého programu nevrací.

> [note]
> Na rozdíl od ostatních termínů, které se tu učíš, není
> „procedura“ v Pythonu zavedený pojem.
> Je vypůjčený z jazyka Pascal.
> Kdybys o něm diskutoval{{a}} s nějakým zkušeným programátorem,
> odkaž ho prosím na tyto materiály.


## Vyhodnocování výrazů

Zaměřme se ale zpátky na funkce, které vrací nějakou hodnotu.
Volání takové funkce se dá použít všude, kde lze použít výraz.
S funkcemi začínají být výrazy trochu složitější, tak se podívejme na to,
jak Python výrazy vyhodnocuje.

Když chceš spočítat matematický výraz, třeba `3 * (5 + 2)`, nejdřív
spočítáš to, co je v závorkách: `(5 + 2)` je `7`.
Výsledek dosadíš do původního výrazu místo závorky: `3 * 7`.
Stejně fungují výrazy v Pythonu.

Možná to zní jednoduše, ale protože budeme tenhle postup používat
i na složitější výrazy, hodí se ho umět „rozepsat“:

```python
vysledek = 3 * (5 + 2)
#              ╰──┬──╯
vysledek = 3 *    7
#          ╰─┬────╯
vysledek =  21
```

Když Python potřebuje vyhodnotit proměnnou, dosadí její hodnotu:

```python
a = 4
b = 5

vysledek = (a + b) / a
#           |    |   |
vysledek = (4 + 5) / 4
#          ╰──┬──╯
vysledek =    9    / 4
#             ╰────┬─╯
vysledek =        2.25
```

Funguje to i u složitých výrazů.

> [note]
> Python se složitými výrazy nemá problém, ale člověk, který program čte či
> píše, se v nich může ztratit.
> Když opravdu potřebuješ napsat složitý výraz, je dobré jej vysvětlit
> pomocí komentáře.

```python
a = 2
b = 5
c = 3


x = -b + (b ** 2 + 4 * a * c) ** 0.5 / (2 * a)
#    |    |            |   |                |
x = -5 + (5 ** 2 + 4 * 2 * 3) ** 0.5 / (2 * 2)
#         ╰──┬─╯   ╰─┬─╯               ╰──┬──╯
x = -5 + (  25   +   8   * 3) ** 0.5 /    4
#                   ╰────┬─╯
x = -5 + (  25   +      24  ) ** 0.5 /    4
#        ╰───────┬──────────╯
x = -5 +         49           ** 0.5 /    4
#                ╰──────┬──────────╯
x = -5 +               7.0           /    4
#                      ╰─────────────┬────╯
x = -5 +                            1.75
#   ╰──────────────┬───────────────────╯
x =              -3.25
```


Nebo se volání funkce dá použít místo čísla v součtu:

```python
delka = len('Ahoj') + len('!')
#        ╰──┬─────╯    ╰─┬───╯
delka =     4       +    1
#           ╰───────┬────╯
delka =             5
```

Nebo v podmínce ifu – třeba u:

```python
if len('Ahoj!') <= 3:
    print('pozdrav je krátký')
```

… se podmínka vyhodnotí jako nepravda:

```python
   len('Ahoj!') <= 3
#  ╰─────┬────╯
         5      <= 3
#        ╰──────┬──╯
              False
```

Nebo dokonce jako argument jiné funkce:

```python
print(len('Ahoj'))
#     ╰────┬────╯
print(     4     )   # vypíše 4
```

Nebo to zkombinovat dohromady:

```python
x = 5
print(len('Ahoj') + x)
#     ╰────┬────╯   |
print(     4      + 5)
#          ╰───┬────╯
print(         9     )
```

… a podobně.


## Argumenty

Argument je to, co funkci dáš k dispozici.
Chceš-li délku řetězce `Ahoj!`, použiješ funkci `len` která umí vypočítat
délku *jakéhokoli* řetězce – a jako argument, v závorkách, jí dáš tu svoji
konkrétní hodnotu: `len('Ahoj!')`.

Podobně funkce `print` umí vypsat jakoukoli hodnotu.
Tu, kterou má vypsat ve tvém konkrétním případě, jí předáš jako argument.

Některým funkcím můžeš předat i více argumentů.
Třeba zrovna funkci `print`, která všechny své argumenty vypíše na řádek.
Jednotlivé argumenty se oddělují čárkami:

```python
print(1, 2, 3)
```

```python
print("Jedna plus dva je", 1 + 2)
```

Některé funkce nepotřebují žádný argument.
Příkladem je zase `print`.
Je ale nutné napsat závorky – i když jsou prázdné.
Hádej, co tohle volání udělá?

```python
print()
```

{% filter solution %}
Funkce `print` zavolaná bez argumentů napíše prázdný řádek.
{% endfilter %}


### Pojmenované argumenty

Některé funkce umí pracovat i s *pojmenovanými* argumenty.
Píšou se podobně jako přiřazení do proměnné,
s rovnítkem, ale uvnitř závorek.

Třeba funkce `print` při výpisu odděluje jednotlivé argumenty mezerou,
ale pomocí argumentu `sep` se dá použít i něco jiného.

```python
print(1, 2, 3, 4, sep=', ')     # Místo mezery odděluj čárkou
```

Dá změnit i to, co `print` udělá na konci výpisu.
Normálně přejde na nový řádek, ale argumentem `sep` můžeš říct co se má vypsat 
*místo toho*.

> [note]
> Tenhle příklad je potřeba napsat do souboru; v interaktivní konzoli
> nebude výstup vypadat tak, jak má.

```python
print('1 + 2', end=' ')     # Místo přechodu na nový řádek jen napiš mezeru
print('=', end=' ')
print(1 + 2, end='!')
print()
```


### Funkce je potřeba volat

Pozor na to, že když nenapíšeš závorky, funkce se nezavolá!
Výraz `len(s)` je *volání funkce*, ale `len` bez závorek označuje
*funkci samotnou*.

Výsledek `len(s)` je číslo; `len` je funkce.

Čísla můžeš sečítat, můžeš tedy napsat `len(s) + 1`.
Funkce ale sečítat nejde – `len + 1` nedává smysl.

Často se ale stane, že závorky prostě zapomeneš.
Zkus si, co dělají následující příklady, a pozorně si přečti výsledky
a chybové hlášky, abys pak podobné chyby poznal{{a}}:

```python
print(len('a'))     # Volání funkce (a vypsání výsledku)
print(len)          # Vypsání samotné funkce
print(len + 1)      # Sečtení funkce a čísla
```


## Užitečné funkce

Nakonec si ukážeme pár základních funkcí, které nám Python nabízí.
Můžeš si stáhnout i
<a href="https://github.com/encukou/cheatsheets/raw/master/basic-functions/basic-functions-cs.pdf">přehled</a>,
který se rozdává na srazech.

### Vstup a výstup

Tyhle funkce už známe.
`print` vypíše nepojmenované argumenty, oddělené mezerou.
Pojmenovaný argument `end` určuje, co se vypíše na konci (místo přechodu
na nový řádek);
`sep` zase, co se vypíše mezi jednotlivými argumenty (místo mezery).

> [note]
> Příklad opět spusť ze souboru, ne interaktivně:

```python
print(1, 'dvě', False)
print(1, end=' ')
print(2, 3, 4, sep=', ')
```

Základní funkce na načtení vstupu, `input`,
vypíše otázku, počká na text od uživatele a ten vrátí jako řetězec.

```python
input('zadej vstup: ')
```

Kontrolní otázky:

* Je `input` „normální“ funkce, nebo procedura?
* Co bere funkce `input` jako argument?
* Jaká je návratová hodnota funkce `input`?

{% filter solution %}
Funkce `input` vrací hodnotu, se kterou může program dál pracovat.
Zařadil bych ji tedy mezi „normální“ funkce.

Jako argument bere `input` otázku, na kterou se uživatele zeptá.

Návratová hodnota funkce `input` je uživatelova odpověď.
{% endfilter %}



### Převádění typů


Co ale když nechceme pracovat s řetězcem, ale třeba s číslem?
Tady nám pomůže skupina funkcí, které umí převádět čísla na řetězce a zpátky.
Každý ze tří <em>typů</em> (angl. <em>types</em>) proměnných, které zatím známe,
má funkci, která vezme nějakou hodnotu a vrátí podobnou hodnotu „svého“ typu.
Na celá čísla je funkce `int` (z angl. *integer*), na reálná čísla je `float`
(z angl. *floating-point*), a pro řetězce `str` (z angl. *string*).

```python
int(x)              # převod na celé číslo
float(x)            # převod na reálné číslo
str(x)              # převod na řetězec
```

Příklady:

```python
3 == int('3') == int(3.0) == int(3.141) == int(3)
8.12 == float('8.12') == float(8.12)
8.0 == float(8) == float('8') == float(8.0)
'3' == str(3) == str('3')
'3.141' == str(3.141) == str('3.141')
```
Ne všechny převody jsou možné:

```python
int('blablabla')    # chyba!
float('blablabla')  # chyba!
int('8.9')          # chyba!
```

…a jak si poradit s chybou, která nastane,
když použiješ špatnou hodnotu, si řekneme později.

#### Převádění a `input`

Převádění typů se často používá při načítání vstupu, třeba jako:

```python
cislo = int(input('Zadej číslo: '))
```

Jak Python vyhodnotí tento výraz?
Zadá-li uživatel <kbd>4</kbd><kbd>2</kbd><kbd>Enter</kbd>,
funkce `input` vrátí řetězec`'42'`.
Ten pak funkce `int` vezme jako argument, udělá z něj číslo a to číslo vrátí:

```python
cislo = int(input('Zadej číslo: '))
      #     ╰─────────┬─────────╯
cislo = int(        '42'          )
      # ╰────────────┬────────────╯
cislo =             42
```



### Matematické funkce

Matematika je občas potřeba, takže se pojďme
podívat, jak v Pythonu pracovat s čísly.

Jedna zajímavá matematická funkce je k dispozici vždy:

```python
round(cislo)    # zaokrouhlení
```

Spousta dalších není k dispozici od začátku programu.
Ne každý má rád matematiku, a ne ve všech druzích programu jsou takové operace
potřeba.
Proto musíš předem – typicky na začátku souboru – říct, že je budeme používat.
To se dělá *naimportováním* z modulu `math`:

```python
from math import sin, cos, tan, sqrt, floor, ceil
```

Naimportované funkce pak můžeš použít:

```python
sin(uhel)       # sinus
cos(uhel)       # kosinus
tan(uhel)       # tangens
sqrt(cislo)     # druhá odmocnina

floor(cislo)    # zaokrouhlení dolů
ceil(cislo)     # zaokrouhlení nahoru
```

> [warning] Import a pojmenování souborů
> Při importování je potřeba si dávat pozor na pojmenování souborů:
> importuješ-li `from math`, nesmí se tvůj program jmenovat `math.py`.
>
> Proč? Když Python v adresáři, ze kterého program pouštíš, najde soubor
> `math.py`, bude se snažit importovat `sin` z něho místo
> z předpřipravené sady matematických funkcí.


### Náhoda

Nakonec si ukážeme dvě funkce, které vrací náhodná čísla.
Jsou užitečné třeba pro hry, ve kterých se hází kostkou nebo tahají
náhodné karty.

Opět nejsou potřeba tak často a je potřeba je *naimportovat*.
Tentokrát z modulu `random`:


```python
from random import randrange, uniform
```

Pak už se dají použít:

```python
randrange(a, b)   # náhodné celé číslo od a do b-1
uniform(a, b)     # náhodné reálné číslo od a do b
```

Pozor na to, že <code>randrange(a, b)</code>
nikdy nevrátí samotné <code>b</code>.
Pokud potřebuješ náhodně vybrat ze tří možností,
použij <code>randrange(0, 3)</code>,
což vrátí <code>0</code>, <code>1</code>, nebo
<code>2</code>:

```python
from random import randrange

cislo = randrange(0, 3)  # číslo je 0, 1, nebo 2
if cislo == 0:
    print('Kolečko')
elif cislo == 1:
    print('Čtvereček')
else:  # tady musí být číslo 2
    print('Trojúhelníček')
```

> [note]
> Pamatuj, když importuješ z modulu `random`, nesmí se tvůj soubor
> jmenovat `random.py`.

### A další
Python dává k dispozici obrovské množství dalších
funkcí a modulů, i když ne všem budeš ze začátku
rozumět.
Všechny jsou – anglicky – popsány v dokumentaci Pythonu, např.
<a href="https://docs.python.org/3/library/functions.html">vestavěné funkce</a>,
<a href="https://docs.python.org/3/library/math.html">matematika</a>.
