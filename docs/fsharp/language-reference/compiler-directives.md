---
title: Dyrektywy kompilatora
description: Dowiedz się więcej o F# dyrektywy preprocesora języka, dyrektywy kompilacji warunkowej, dyrektywy line i dyrektywy kompilatora.
ms.date: 12/10/2018
ms.openlocfilehash: 3fade7407f84b00163bd5b3d7774104bce8a25af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766106"
---
# <a name="compiler-directives"></a>Dyrektywy kompilatora

W tym temacie opisano procesora dyrektywy i dyrektywy kompilatora.

## <a name="preprocessor-directives"></a>Dyrektywy preprocesora

Dyrektywy preprocesora jest poprzedzony symbolem # i pojawia się w wierszu samodzielnie. Jest interpretowany przez preprocesor, który jest uruchamiany zanim kompilator sam.

W poniższej tabeli wymieniono dyrektywy preprocesora, które są dostępne w F#.

|— Dyrektywa|Opis|
|---------|-----------|
|`#if` *symbol*|Obsługuje kompilację warunkową. Kod w sekcji po `#if` jest dołączona, jeśli *symbol* jest zdefiniowana. Symbol również może być ujemna z `!`.|
|`#else`|Obsługuje kompilację warunkową. Oznacza sekcji kodu do dołączenia, jeśli symbol jest używany z poprzedniego `#if` nie został zdefiniowany.|
|`#endif`|Obsługuje kompilację warunkową. Oznacza koniec warunkowego sekcji kodu.|
|`#`[wiersz] *int*,<br/>`#`[wiersz] *int* *ciąg*,<br/>`#`[wiersz] *int* *ciąg verbatim*|Wskazuje oryginalnego źródła kodu wiersza i nazwa pliku, do debugowania. Ta funkcja jest dostępna dla narzędzi, które generują F# kodu źródłowego.|
|`#nowarn` *warningcode*|Wyłącza ostrzeżenie kompilatora lub ostrzeżenia. Aby wyłączyć ostrzeżenia, Znajdź jego numer w danych wyjściowych kompilatora i uwzględnić go w znaki cudzysłowu. Pominięcie prefiksu "FS". Aby wyłączyć wiele numerów ostrzeżeń, w tym samym wierszu, obejmują każdej liczby w znaki cudzysłowu i Oddziel poszczególne ciągi spacjami. Na przykład:

`#nowarn "9" "40"`

Wpływ wyłączenia ostrzeżenie ma zastosowanie do całego pliku, w tym części pliku, które poprzedzają dyrektywy. |

## <a name="conditional-compilation-directives"></a>Dyrektywy kompilacji warunkowej

Kod, który jest dezaktywowany za pomocą jednej z tych dyrektyw jest wyszarzony w edytorze kodu programu Visual Studio.

> [!NOTE]
> Zachowanie dyrektywy kompilacji warunkowej nie jest taka sama jak w innych językach. Na przykład nie można używać wyrażeń logicznych obejmujących symbole, i `true` i `false` nie mają specjalnego znaczenia. Symbole, których używasz w `if` dyrektywy muszą być zdefiniowane przy użyciu wiersza polecenia lub w ustawieniach projektu; jest nie `define` dyrektywy preprocesora.

Poniższy kod ilustruje sposób korzystania z `#if`, `#else`, i `#endif` dyrektywy. W tym przykładzie kod zawiera dwie wersje definicji `function1`. Podczas `VERSION1` jest definiowana za pomocą [-define — opcja kompilatora](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), kod między `#if` dyrektywy i `#else` dyrektywa została aktywowana. W przeciwnym razie kod między `#else` i `#endif` została aktywowana.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Istnieje nie `#define` dyrektywy preprocesora w F#. Należy użyć ustawienia kompilatora opcji lub projektu do definiowania symbole używane przez `#if` dyrektywy.

Dyrektywy kompilacji warunkowej, mogą być zagnieżdżone. Wcięcia nie ma znaczenia dla dyrektywy preprocesora.

Można również negate — symbol `!`. W tym przykładzie wartość ciągu jest coś tylko wtedy, gdy _nie_ debugowania:

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a>Dyrektywy line

Podczas kompilowania, kompilator zgłasza błędy w F# kodu, odwołując się do wiersza liczby, w którym występuje każdy z błędów. Te numery wierszy są liczone od 1 dla pierwszego wiersza w pliku. Jednak jeśli jest generowany F# kodu źródłowego z innego narzędzia, numery wierszy w wygenerowanym kodzie zazwyczaj nie są przedmiotem zainteresowania, ponieważ błędy w wygenerowanym F# kodu, które prawdopodobnie wynikają z innego źródła. `#line` Dyrektywy, umożliwia autorom narzędzia, które generują F# źródła kodu do przekazania informacji o wierszu, oryginalnym liczb i pliki źródłowe do wygenerowany F# kodu.

Kiedy używasz `#line` dyrektywy, nazwy plików muszą być ujęte w znaki cudzysłowu. Chyba że verbatim token (`@`) pojawia się przed ciągu, musisz wyjść ukośnik odwrotny znaków przy użyciu dwóch znaków ukośnika odwrotnego zamiast jednego, aby można było używać ich w ścieżce. Poniżej przedstawiono prawidłowe wiersza tokenów. W tym przykładzie przyjęto założenie, że oryginalny plik `Script1` skutkuje automatycznie generowanych F# plik kodu, gdy jest uruchamiany przy użyciu narzędzia, a kod w lokalizacji te dyrektywy jest generowany na podstawie niektórych tokenów w wierszu 25 w pliku `Script1`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Tokeny te wskazują, że F# kod wygenerowany w tej lokalizacji jest tworzony na podstawie niektórych konstrukcji w lub w pobliżu wiersza `25` w `Script1`.

## <a name="compiler-directives"></a>Dyrektywy kompilatora

Dyrektywy kompilatora przypominają dyrektywy preprocesora, ponieważ są one poprzedzone znakiem #, ale zamiast interpretowane przez preprocesor są pozostawiane przez kompilator interpretacji i postępowania zajmującym się.

W poniższej tabeli wymieniono dyrektywy kompilatora, który jest dostępny w F#.

|— Dyrektywa|Opis|
|---------|-----------|
|`#light` ["on"&#124;"off"]|Włącza lub wyłącza uproszczone składni, na potrzeby utrzymywania zgodności z innymi wersjami języka ML. Domyślnie lightweight — składnia jest włączona. Pełna składnia jest zawsze włączona. W związku z tym można użyć zarówno w przypadku składni lekkiej, jak i Pełna składnia. Dyrektywa `#light` samodzielnie jest odpowiednikiem `#light "on"`. Jeśli określisz `#light "off"`, należy użyć składni pełne dla wszystkich konstrukcji językowych. Składnia w dokumentacji dotyczącej F# zobaczy przy założeniu, że używasz składni lekkiej. Aby uzyskać więcej informacji, zobacz [Pełna składnia](verbose-syntax.md).|

Dyrektywy interpreter (fsi.exe), można zobaczyć [interaktywne programowanie za pomocą F# ](../tutorials/fsharp-interactive/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Opcje kompilatora](compiler-options.md)