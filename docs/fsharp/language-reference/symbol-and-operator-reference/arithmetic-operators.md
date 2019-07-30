---
title: Operatory arytmetyczne
description: Dowiedz się więcej na temat operatorów arytmetycznych dostępnych F# w języku programowania.
ms.date: 04/04/2018
ms.openlocfilehash: b783a0134541f11f06dde83af97676699b797da1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630784"
---
# <a name="arithmetic-operators"></a>Operatory arytmetyczne

W tym temacie opisano operatory arytmetyczne, które są F# dostępne w języku.

## <a name="summary-of-binary-arithmetic-operators"></a>Podsumowanie binarnych operatorów arytmetycznych

Poniższa tabela zawiera podsumowanie binarnych operatorów arytmetycznych, które są dostępne dla nieopakowanych typów całkowitych i zmiennoprzecinkowych.

|Operator binarny|Uwagi|
|---------------|-----|
|`+`(dodatkowo i)|Unchecked. Możliwy warunek przepełnienia, gdy liczby są dodawane razem, a suma przekracza maksymalną wartość bezwzględną obsługiwaną przez typ.|
|`-`(odejmowanie, minus)|Unchecked. Możliwy warunek nadmiarowy w przypadku odejmowania niepodpisanych typów lub gdy wartości zmiennoprzecinkowe są zbyt małe, aby były reprezentowane przez typ.|
|`*`(mnożenie, godziny)|Unchecked. Możliwy warunek przepełnienia, gdy liczba jest mnożona, a iloczyn przekracza maksymalną wartość bezwzględną obsługiwaną przez typ.|
|`/`(dzielenie, podzielone przez)|Dzielenie przez zero powoduje <xref:System.DivideByZeroException> dla typów całkowitych. W przypadku typów zmiennoprzecinkowych dzielenie przez zero daje specjalne wartości `+Infinity` zmiennoprzecinkowe lub. `-Infinity` Istnieje również możliwy warunek nadmiarowy, gdy liczba zmiennoprzecinkowa jest zbyt mała do reprezentowania przez typ.|
|`%`(reszta, REM)|Zwraca resztę operacji dzielenia. Znak wyniku jest taki sam jak znak pierwszego operandu.|
|`**`(Potęgowanie do potęgi)|Możliwy warunek przepełnienia, gdy wynik przekracza maksymalną wartość bezwzględną dla tego typu.<br /><br />Operator wykładniczy działa tylko z typami zmiennoprzecinkowymi.|

## <a name="summary-of-unary-arithmetic-operators"></a>Podsumowanie jednoargumentowych operatorów arytmetycznych

Poniższa tabela zawiera podsumowanie jednoargumentowych operatorów arytmetycznych, które są dostępne dla typów całkowitych i zmiennoprzecinkowych.

|Jednoargumentowy operator|Uwagi|
|--------------|-----|
|`+`dodatni|Można zastosować do dowolnego wyrażenia arytmetycznego. Nie zmienia znaku wartości.|
|`-`(Negacja, ujemna)|Można zastosować do dowolnego wyrażenia arytmetycznego. Zmienia znak wartości.|

Zachowanie w przypadku brakujących lub niedopełnienia typów całkowitych jest zawijane wokół. Powoduje to nieprawidłowe wyniki. Przepełnienie całkowite to potencjalnie poważny problem, który może przyczynić się do problemów z bezpieczeństwem, gdy oprogramowanie nie zostało zapisaną do konta. Jeśli jest to problem dla aplikacji, rozważ użycie zaewidencjonowanych operatorów w `Microsoft.FSharp.Core.Operators.Checked`.

## <a name="summary-of-binary-comparison-operators"></a>Podsumowanie operatorów porównywania binarnego

W poniższej tabeli przedstawiono binarne operatory porównywania, które są dostępne dla typów całkowitych i zmiennoprzecinkowych. Te operatory zwracają wartości typu `bool`.

Liczby zmiennoprzecinkowe nigdy nie powinny być porównywane bezpośrednio ze względu na równość, ponieważ reprezentacja zmiennoprzecinkowa IEEE nie obsługuje dokładnej operacji równości. Dwie liczby, które można łatwo zweryfikować, aby były równe, sprawdzając kod może faktycznie mieć różne reprezentacje bitowe.

|Operator|Uwagi|
|--------|-----|
|`=`(równość, równa się)|To nie jest operator przypisania. Jest on używany tylko do porównania. Jest to operator generyczny.|
|`>`(większe niż)|Jest to operator generyczny.|
|`<`(mniejsze niż)|Jest to operator generyczny.|
|`>=`(większe niż lub równe)|Jest to operator generyczny.|
|`<=`(mniejsze niż lub równe)|Jest to operator generyczny.|
|`<>`(nie równa się)|Jest to operator generyczny.|

## <a name="overloaded-and-generic-operators"></a>Operatory przeciążone i generyczne

Wszystkie operatory omówione w tym temacie są zdefiniowane w przestrzeni nazw **Microsoft. FSharp. Core. Operators** . Niektóre operatory są zdefiniowane przy użyciu statycznie rozpoznanych parametrów typu. Oznacza to, że istnieją oddzielne definicje dla każdego określonego typu, który działa z tym operatorem. Wszystkie operatory jednoargumentowe i arytmetyczne i bitowe są w tej kategorii. Operatory porównania są ogólne i w związku z tym pracują z dowolnym typem, a nie tylko typami arytmetycznymi pierwotnymi. Typ Unii rozłącznych i typów rekordów mają własne Implementacje niestandardowe, które są generowane F# przez kompilator. Typy klas używają metody <xref:System.Object.Equals%2A>.

Operatory ogólne można dostosowywać. Aby dostosować funkcje porównania, Przesłoń <xref:System.Object.Equals%2A> , aby zapewnić własne niestandardowe porównanie równości, a następnie zaimplementować <xref:System.IComparable>. Interfejs ma pojedynczą metodę <xref:System.IComparable.CompareTo%2A> , metodę. <xref:System.IComparable?displayProperty=nameWithType>

## <a name="operators-and-type-inference"></a>Operatory i wnioskowanie typów

Użycie operatora w wyrażeniu ogranicza wnioskowanie typu do tego operatora. Ponadto użycie operatorów zapobiega automatycznym uogólnieniu, ponieważ użycie operatorów oznacza typ arytmetyczny. W przypadku braku jakichkolwiek innych informacji F# kompilator wnioskuje `int` jako typ wyrażeń arytmetycznych. To zachowanie można zastąpić, określając inny typ. `function1` W ten sposób typy argumentów i zwracany typ w poniższym kodzie są wywnioskowane `int`jako, ale typy dla `function2` są wywnioskowane `float`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]

## <a name="see-also"></a>Zobacz także

- [Odwołanie do symboli i operatorów](index.md)
- [Przeładowanie operatora](../operator-overloading.md)
- [Operatory bitowe](bitwise-operators.md)
- [Operatory logiczne](boolean-operators.md)
