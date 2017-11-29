---
title: Dyrektywy kompilatora (F#)
description: "Więcej informacji na temat F # języka dyrektywy preprocesora, dyrektywy warunkowej kompilacji, dyrektywy line i dyrektywy kompilatora."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 93aef07a-6747-4ce4-a10f-a05168978af6
ms.openlocfilehash: b4305d24163f9b23631d5efb6e838f55127cd9f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="compiler-directives"></a>Dyrektywy kompilatora

W tym temacie opisano procesora dyrektywy i dyrektywy kompilatora.


## <a name="preprocessor-directives"></a>Dyrektywy preprocesora
Dyrektywy preprocesora jest poprzedzone symbolem # i pojawia się w wierszu samodzielnie. Jest interpretowany przez preprocesora, uruchamianego przed kompilator samej siebie.

W poniższej tabeli wymieniono dyrektywy preprocesora, które są dostępne w języku F #.


|Dyrektywy|Opis|
|---------|-----------|
|`#if`*symbol*|Obsługuje kompilacji warunkowej. Kod w sekcji po `#if` jest uwzględniona, jeśli *symbol* jest zdefiniowany.|
|`#else`|Obsługuje kompilacji warunkowej. Oznacza sekcji kodu do uwzględnienia, jeśli symbol jest używany z poprzedniej `#if` nie jest zdefiniowany.|
|`#endif`|Obsługuje kompilacji warunkowej. Oznacza koniec warunkowego sekcji kodu.|
|`#`[wiersz] *int*,<br/>`#`[wiersz] *int* *ciąg*,<br/>`#`[wiersz] *int* *ciągu dosłownego wyrażenia*|Wskazuje oryginalnego źródła kodu wiersza i nazwa pliku, do debugowania. Ta funkcja jest dostępna dla narzędzia, które generowanie kodu źródłowego języka F #.|
|`#nowarn`*warningcode*|Wyłącza ostrzeżenia kompilatora lub ostrzeżeń. Aby wyłączyć ostrzeżenia, Znajdź jego numer z danych wyjściowych kompilatora i uwzględnić go w cudzysłowy. Pomiń prefiksu "FS". Aby wyłączyć wiele numerów ostrzeżeń, które w tym samym wierszu, obejmują każdej liczby w znaki cudzysłowu i oddziel każdy ciąg spacją. Na przykład:

`#nowarn "9" "40"`


Wpływ wyłączenia ostrzeżenie dotyczy całego pliku, w tym części pliku, które należy poprzedzić dyrektywy. |

## <a name="conditional-compilation-directives"></a>Dyrektywy kompilacja warunkowa
Kod, który jest dezaktywowana za pomocą jednej z tych dyrektyw jest przyciemnione w edytorze StudioCode Visual.


>[!NOTE] 
Zachowanie dyrektywy kompilacja warunkowa nie jest taka sama jak w innych językach. Na przykład nie można używać wyrażeń logicznych zawierających symbole, i `true` i `false` ma specjalnego znaczenia. Symbole używane w `if` dyrektywa musi być zdefiniowany za pomocą wiersza polecenia lub w ustawieniach projektu; nie istnieje żadne `define` dyrektywy preprocesora.


Poniższy kod przedstawia użycie `#if`, `#else`, i `#endif` dyrektywy. W tym przykładzie kodu zawiera dwie wersje definicji `function1`. Gdy `VERSION1` jest definiowana za pomocą [-define — opcja kompilatora](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04), kodu między `#if` dyrektywy i `#else` dyrektywa jest aktywny. W przeciwnym razie kod między `#else` i `#endif` jest aktywny.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

Brak nie `#define` dyrektywy preprocesora w języku F #. Należy użyć ustawień kompilatora opcji lub projekt do definiowania symbole używane przez `#if` dyrektywy.

Kompilacja warunkowa dyrektywy mogą być zagnieżdżane. Wcięcie nie ma znaczenia dla dyrektywy preprocesora.


## <a name="line-directives"></a>Dyrektywy line
Podczas kompilowania, kompilator raporty błędów w kodzie języka F # za pomocą odwołań do numerów wierszy, na których występuje każdy z błędów. Te numery wierszy są liczone od 1 do pierwszego wiersza w pliku. Jednak przypadku generowania kodu źródłowego języka F # z innego narzędzia, numery wierszy w wygenerowanym kodzie zazwyczaj nie są przydatne, ponieważ błędy w wygenerowanym kodzie języka F # prawdopodobnie wynikają z innego źródła. `#line` Dyrektywy umożliwia autorom narzędzia, które generowanie kodu źródłowego języka F # do przekazywania informacji o wierszu oryginalnego liczb i plikach źródłowych do wygenerowanego kodu języka F #.

Jeśli używasz `#line` dyrektywy, nazwy pliku musi być ujęta w cudzysłów. Jeśli token dosłownego wyrażenia (`@`) pojawi się na początku ciąg, musi wprowadzić odwróconej przy użyciu dwóch znaków ukośnik odwrotny zamiast jeden, aby można było używać ich w ścieżce. Poniżej przedstawiono tokeny prawidłowym wierszem. W tym przykładzie przyjęto założenie, że oryginalny plik `Script1` wynikiem automatycznie wygenerowany plik kodu języka F #, gdy jest uruchamiany przy użyciu narzędzia, a generowania kodu w lokalizacji tych dyrektyw z niektórych tokenów w wierszu 25 w pliku `Script1`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

Tokeny te wskazują w kodzie języka F # wygenerowany w tej lokalizacji jest pochodną niektóre konstrukcje po lub w pobliżu wiersza `25` w `Script1`.


## <a name="compiler-directives"></a>Dyrektywy kompilatora
Dyrektywy kompilatora przypominać dyrektywy preprocesora, ponieważ mają przedrostek znak #, ale zamiast interpretowane przez preprocesora, są pozostawiane dla kompilatora, aby zinterpretować i korzystania z.

W poniższej tabeli wymieniono dyrektywy kompilatora, która jest dostępna w języku F #.


|Dyrektywy|Opis|
|---------|-----------|
|`#light`["on"|"off"]|Włącza lub wyłącza lightweight — składnia, zgodność z innymi wersjami uczenia Maszynowego. Lightweight — składnia jest domyślnie włączone. Pełna składnia jest zawsze włączone. W związku z tym można użyć zarówno lightweight — składnia i Pełna składnia. Dyrektywa `#light` samodzielnie jest odpowiednikiem `#light "on"`. Jeśli określisz `#light "off"`, należy użyć składni pełne dla wszystkich konstrukcji języka. Przy założeniu, że używasz lightweight — składnia zobaczy składni w dokumentacji dotyczącej F #. Aby uzyskać więcej informacji, zobacz [Pełna składnia](verbose-syntax.md).|
Dla dyrektywy interpreter (fsi.exe), zobacz [interakcyjne programowania w języku F #](../tutorials/fsharp-interactive/index.md).


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F #](index.md)

[Opcje kompilatora](compiler-options.md)

