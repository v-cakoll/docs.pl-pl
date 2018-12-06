---
title: Operatory arytmetyczne (F#)
description: Dowiedz się więcej o operatorów arytmetycznych, które są dostępne w F# języka programowania.
ms.date: 04/04/2018
ms.openlocfilehash: 2c0e2e25a4f79d00455d978e235e4bef16b52586
ms.sourcegitcommit: 6ae7cdd0437a32884556dd4826ca90e957b7a4e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2018
ms.locfileid: "45597442"
---
# <a name="arithmetic-operators"></a>Operatory arytmetyczne

W tym temacie opisano operatorów arytmetycznych, które są dostępne w F# języka.

## <a name="summary-of-binary-arithmetic-operators"></a>Podsumowanie binarne operatory arytmetyczne

Poniższa tabela zawiera podsumowanie binarne operatorów arytmetycznych, które są dostępne dla rozpakowany typów całkowitych i zmiennoprzecinkowych.

|Operator binarny|Uwagi|
|---------------|-----|
|`+` (oprócz plus)|Niezaznaczone. Możliwe przepełnienia, gdy liczby są sumowane i suma przekracza maksymalną wartość bezwzględna obsługiwany przez typ.|
|`-` (odejmowania, minus)|Niezaznaczone. Możliwe niedopełnienie warunku, gdy są odejmowane typy bez znaku lub różne wartości zmiennoprzecinkowe są zbyt małe, aby mogły być reprezentowane przez typ.|
|`*` (mnożenia, razy)|Niezaznaczone. Możliwe przepełnienie warunek pomnożona liczb i produktu przekracza maksymalną wartość bezwzględna obsługiwany przez typ.|
|`/` (dział, podzielona przez)|Dzielenie przez zero powoduje, że <xref:System.DivideByZeroException> w przypadku typów całkowitych. Dla typów zmiennopozycyjnych, dzielenie przez zero zapewnia specjalnych wartości zmiennoprzecinkowych `+Infinity` lub `-Infinity`. Istnieje również warunek niedopełnienie możliwe, gdy liczba zmiennoprzecinkowa jest zbyt mały, aby mogły być reprezentowane przez typ.|
|`%` (resztę, rem)|Zwraca resztę z operacji dzielenia. Znak wyniku jest taki sam, jak znak pierwszego operandu.|
|`**` (do potęgi równej potęgowania)|Możliwe przepełnienie warunek, gdy wynik przekracza maksymalną wartość bezwzględna dla typu.<br /><br />Operator potęgowania działa tylko z typów zmiennoprzecinkowych.|

## <a name="summary-of-unary-arithmetic-operators"></a>Podsumowanie jednoargumentowe operatory arytmetyczne

Poniższa tabela zawiera podsumowanie jednoargumentowe operatory arytmetyczne, które są dostępne dla typów całkowitych i zmiennoprzecinkowych.

|Jednoargumentowy operator|Uwagi|
|--------------|-----|
|`+` (pozytywna)|Mogą być stosowane do dowolnego wyrażenia arytmetyczne. Nie zmienia znak wartości.|
|`-` (Negacja, ujemna)|Mogą być stosowane do dowolnego wyrażenia arytmetyczne. Zmienia znak wartości.|

Zachowanie na przepełnienie lub niedopełnienie w przypadku typów całkowitych jest otacza. Powoduje to, że niepoprawny wynik. Przepełnienie liczby całkowitej jest potencjalnie poważny problem, który może przyczynić się do problemów z zabezpieczeniami, gdy oprogramowanie nie jest zapisywany na konto dla niego. Jeśli jest to istotna dla aplikacji, należy wziąć pod uwagę przy użyciu operatorów zaznaczone w `Microsoft.FSharp.Core.Operators.Checked`.

## <a name="summary-of-binary-comparison-operators"></a>Podsumowanie operatory binarne porównania

W poniższej tabeli przedstawiono operatory binarne porównania, które są dostępne dla typów całkowitych i zmiennoprzecinkowych. Te operatory zwracają wartości typu `bool`.

Liczby zmiennoprzecinkowe powinny być nigdy nie porównywane bezpośrednio pod kątem równości, ponieważ odwzorowanie liczby zmiennoprzecinkowej IEEE nie obsługuje operacji dokładnie równości. Dwóch liczb, który możesz łatwo zweryfikować za równe, sprawdzając kod faktycznie mogą mieć różnych bitowej reprezentacji.

|Operator|Uwagi|
|--------|-----|
|`=` (równości, równa się)|Nie jest to operator przypisania. Jest on używany tylko do porównania. To jest ogólny operator.|
|`>` (większe niż)|To jest ogólny operator.|
|`<` (mniejsze niż)|To jest ogólny operator.|
|`>=` (większa niż lub równe)|To jest ogólny operator.|
|`<=` (mniej niż lub równe)|To jest ogólny operator.|
|`<>` (nie równa się)|To jest ogólny operator.|

## <a name="overloaded-and-generic-operators"></a>Operatory przeciążone i ogólne

Wszystkie operatory omówione w tym temacie są zdefiniowane w **Microsoft.FSharp.Core.Operators** przestrzeni nazw. Niektóre operatory są definiowane za pomocą parametrów typu statycznie rozpoznanych. Oznacza to, że nie istnieją oddzielne definicje dla każdego określonego typu, która współdziała z tego operatora. Wszystkie jednoargumentowy i operatory dwuargumentowe arytmetyczne i bitowe znajdują się w tej kategorii. Operatory porównania są ogólne, a więc pracować z dowolnego typu, a nie po prostu pierwotnych typów arytmetycznych. Złożenia dyskryminowanego i typy rekordów mają własnych niestandardowych implementacji, które są generowane przez F# kompilatora. Typy klas należy użyć metody <xref:System.Object.Equals%2A>.

Ogólny operatory są możliwe do dostosowania. Aby dostosować funkcje porównania, należy zastąpić <xref:System.Object.Equals%2A> można podać własne niestandardowe porównania, a następnie wdrożyć <xref:System.IComparable>. <xref:System.IComparable?displayProperty=nameWithType> Interfejs zawiera jedną metodę, <xref:System.IComparable.CompareTo%2A> metody.

## <a name="operators-and-type-inference"></a>Operatory i wnioskowanie o typie

Użycie operatora w wyrażeniu ogranicza wnioskowanie o typie na tego operatora. Ponadto użycie operatorów zapobiega automatyczna Generalizacja, ponieważ użycie operatorów oznacza typ arytmetyczny. W przypadku braku innych informacji F# kompilator wnioskuje `int` jako typ wyrażenia arytmetyczne. To zachowanie można zastąpić, określając innego typu. Dlatego typy argumentów i zwracanego typu `function1` w poniższym kodzie są wywnioskowana `int`, ale typy dla `function2` są wywnioskowana `float`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]

## <a name="see-also"></a>Zobacz także

- [Odwołanie do symboli i operatorów](index.md)
- [Przeładowanie operatora](../operator-overloading.md)
- [Operatory bitowe](bitwise-operators.md)
- [Operatory logiczne](boolean-operators.md)
