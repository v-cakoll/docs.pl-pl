---
title: Dyrektywy kompilatora
description: Dowiedz F# się więcej o dyrektywach preprocesora języka, dyrektywach kompilacji warunkowej, dyrektywach i dyrektywach kompilatora.
ms.date: 12/10/2018
ms.openlocfilehash: 16db2efb2fee2c2c5e94aa98eb0a13183a4e0e0b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630402"
---
# <a name="compiler-directives"></a>Dyrektywy kompilatora

W tym temacie opisano dyrektywy procesora i dyrektywy kompilatora.

## <a name="preprocessor-directives"></a>Dyrektywy preprocesora

Dyrektywa preprocesora jest poprzedzona znakiem # symbol i jest wyświetlana w wierszu. Jest on interpretowany przez preprocesor, który jest uruchamiany przed samym kompilatorem.

W poniższej tabeli wymieniono dyrektywy preprocesora, które są dostępne w F#programie.

|— Dyrektywa|Opis|
|---------|-----------|
|`#if`*symbol*|Obsługuje kompilację warunkową. Kod w sekcji po `#if` zostanie uwzględniony, jeśli *symbol* jest zdefiniowany. Symbol może być również negacją `!`.|
|`#else`|Obsługuje kompilację warunkową. Oznacza sekcję kodu do dołączenia, jeśli symbol używany z poprzednim `#if` nie został zdefiniowany.|
|`#endif`|Obsługuje kompilację warunkową. Oznacza koniec sekcji warunkowej kodu.|
|`#`liniow *int*,<br/>`#`liniow liczba *całkowita* *ciąg*,<br/>`#`liniow liczba *całkowita* *Verbatim — ciąg*|Wskazuje pierwotny wiersz kodu źródłowego i nazwę pliku na potrzeby debugowania. Ta funkcja jest dostępna dla narzędzi generujących F# kod źródłowy.|
|`#nowarn`*WarningCode*|Wyłącza ostrzeżenie lub ostrzeżenia kompilatora. Aby wyłączyć ostrzeżenie, Znajdź jego numer z danych wyjściowych kompilatora i umieść go w cudzysłowie. Pomiń prefiks "FS". Aby wyłączyć wiele numerów ostrzeżeń w tym samym wierszu, należy uwzględnić każdą liczbę w cudzysłowie i oddzielić każdy ciąg znaków spacją. Na przykład:

`#nowarn "9" "40"`

Efekt wyłączenia ostrzeżenia dotyczy całego pliku, w tym części pliku, który poprzedza dyrektywę. |

## <a name="conditional-compilation-directives"></a>Dyrektywy kompilacji warunkowej

Kod zdezaktywowany przez jedną z tych dyrektyw jest wyszarzony w edytorze Visual Studio Code.

> [!NOTE]
> Zachowanie dyrektyw kompilacji warunkowej nie jest takie samo, jak w innych językach. Na przykład nie można używać wyrażeń logicznych obejmujących symbole i `true` i `false` nie mają specjalnego znaczenia. Symbole, które są `if` używane w dyrektywie, muszą być zdefiniowane w wierszu polecenia lub w ustawieniach projektu; nie `define` istnieje dyrektywa preprocesora.

Poniższy kod ilustruje użycie `#if`dyrektyw, `#else`i `#endif` . W tym przykładzie kod zawiera dwie wersje definicji `function1`. Gdy `VERSION1` jest zdefiniowany przy użyciu [opcji-define kompilatora](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), jest uaktywniany kod między `#if` dyrektywą i `#else` dyrektywą. W przeciwnym razie kod między `#else` i `#endif` jest aktywowany.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Brak `#define` dyrektywy preprocesora w F#. Aby zdefiniować symbole używane przez `#if` dyrektywę, należy użyć opcji kompilatora lub ustawienia projektu.

Dyrektywy kompilacji warunkowej mogą być zagnieżdżane. Wcięcia nie są znaczące w przypadku dyrektyw preprocesora.

Możesz również Negate symbol z `!`. W tym przykładzie wartość ciągu jest coś tylko wtedy, gdy _nie_ jest debugowana:

```fsharp
#if !DEBUG
let str = "Not debugging!"
#else
let str = "Debugging!"
#endif
```

## <a name="line-directives"></a>Dyrektywy linii

Podczas kompilowania kompilator zgłasza błędy w F# kodzie, odwołując się do numerów wierszy, na których występuje każdy błąd. Te numery wierszy zaczynają się od 1 dla pierwszego wiersza w pliku. Jednak w przypadku generowania F# kodu źródłowego za pomocą innego narzędzia numery wierszy w wygenerowanym kodzie nie są generalnie przydatne, ponieważ błędy w generowanym F# kodzie najprawdopodobniej wynikają z innego źródła. Dyrektywa umożliwia autorom narzędzi generujących F# kod źródłowy w celu przekazywania informacji o oryginalnych numerach wierszy i plikach źródłowych do wygenerowanego F# kodu. `#line`

W przypadku używania `#line` dyrektywy nazwy plików muszą być ujęte w cudzysłów. Chyba że token Verbatim (`@`) pojawia się przed ciągiem, należy wypróbować odwrotne ukośniki, używając dwóch ukośników odwrotnych zamiast jednego, aby użyć ich w ścieżce. Poniżej podano prawidłowe tokeny wiersza. W tych przykładach Załóżmy, że oryginalny plik `Script1` powoduje automatyczne wygenerowanie F# pliku kodu, gdy jest uruchamiany za pośrednictwem narzędzia i że kod w lokalizacji tych dyrektyw jest generowany na podstawie niektórych tokenów w wierszu 25 w pliku `Script1`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Te tokeny wskazują, F# że kod wygenerowany w tej lokalizacji pochodzi od niektórych konstrukcji w lub w okolicach `Script1`w wierszu `25` .

## <a name="compiler-directives"></a>Dyrektywy kompilatora

Dyrektywy kompilatora przypominają dyrektywy preprocesora, ponieważ są poprzedzone znakiem #, ale zamiast nie są interpretowane przez preprocesor, są pozostawiane dla kompilatora, który interpretuje i działa.

W poniższej tabeli wymieniono dyrektywy kompilatora, które są dostępne F#w programie.

|— Dyrektywa|Opis|
|---------|-----------|
|`#light` ["on"&#124;"off"]|Włącza lub wyłącza uproszczoną składnię w celu zapewnienia zgodności z innymi wersjami ML. Domyślnie uproszczona składnia jest włączona. Pełna składnia jest zawsze włączona. W związku z tym można użyć składni uproszczonej i pełnej składni. Sama dyrektywa `#light` jest równoważna z `#light "on"`. Jeśli określisz `#light "off"`, musisz użyć pełnej składni dla wszystkich konstrukcji językowych. Składnia w dokumentacji programu F# jest prezentowana z założeniem, że używana jest składnia uproszczona. Aby uzyskać więcej informacji, zobacz [verbose Syntax](verbose-syntax.md).|

Aby poznać dyrektywy interpretera (fsi. exe), zobacz [interaktywne programowanie F#przy użyciu programu ](../tutorials/fsharp-interactive/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Opcje kompilatora](compiler-options.md)
