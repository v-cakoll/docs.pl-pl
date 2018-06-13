---
title: Operatory arytmetyczne (F#)
description: 'Więcej informacji na temat operatorów arytmetycznych, które są dostępne w języku programowania w języku F #.'
ms.date: 04/04/2018
ms.openlocfilehash: ead0bbd7fdad528b322f99eaf0f73638f060eb51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565941"
---
# <a name="arithmetic-operators"></a>Operatory arytmetyczne

W tym temacie opisano operatory arytmetyczne, które są dostępne w języku F #.

## <a name="summary-of-binary-arithmetic-operators"></a>Podsumowanie binarne operatory arytmetyczne
Poniższa tabela zawiera podsumowanie binarne operatorów arytmetycznych, które są dostępne dla rozpakowany typów całkowitych i zmiennoprzecinkowych.

|Operator binarny.|Uwagi|
|---------------|-----|
|`+` (dodanie, plus)|Zaznaczenie opcji. Możliwe przepełnienie woluminowi numery są ze sobą i suma przekracza maksymalną wartość bezwzględna obsługiwane przez ten typ.|
|`-` (odejmowania, minus)|Zaznaczenie opcji. Możliwe niedopełnienie warunku, po odjęciu są typy bez znaku lub jest za mały, aby mogły być reprezentowane przez typ wartości zmiennoprzecinkowych.|
|`*` (mnożenia, razy)|Zaznaczenie opcji. Możliwe przepełnienie pomnożona liczb i produktu przekracza maksymalną wartość bezwzględna obsługiwane przez ten typ.|
|`/` (dzielenie przez)|Dzielenie przez zero przyczyny <xref:System.DivideByZeroException> dla typów całkowitych. Dla typów zmiennoprzecinkowych dzielenie przez zero umożliwia specjalne wartości zmiennoprzecinkowych `+Infinity` lub `-Infinity`. Istnieje również warunek niedopełnienie możliwe, gdy liczba zmiennoprzecinkowa jest za mały, aby mogły być reprezentowane przez typ.|
|`%` (pozostałą, rem)|Zwraca resztę z operacji dzielenia. Znak wynik jest taka sama jak znak pierwszy argument operacji.|
|`**` (do potęgi równej potęgowania)|Możliwe przepełnienie podczas wynik przekracza maksymalną wartość bezwzględna dla typu.<br /><br />Operator wykładniczy działa tylko z typów zmiennoprzecinkowych.|

## <a name="summary-of-unary-arithmetic-operators"></a>Podsumowanie jednoargumentowe operatory arytmetyczne
Poniższa tabela zawiera podsumowanie jednoargumentowe operatory arytmetyczne, które są dostępne dla typów całkowitych i zmiennoprzecinkowych.


|Operator jednoargumentowy|Uwagi|
|--------------|-----|
|`+` (dodatnia)|Można zastosować do dowolnego wyrażenia arytmetyczne. Nie zmienia się znak wartości.|
|`-` (negacji, ujemna)|Można zastosować do dowolnego wyrażenia arytmetyczne. Zmienia znak wartości.|
Zachowanie na przepełnienie lub niedomiar w przypadku typów całkowitych jest zawijane. Powoduje to niepoprawny wynik. Liczba całkowita przepełnienia jest potencjalnie poważny problem, który może przyczynić się do problemów z zabezpieczeniami, gdy oprogramowanie nie zostanie zapisany w konta dla niego. Jeśli to jest istotny dla aplikacji, należy wziąć pod uwagę przy użyciu operatorów zaznaczone w `Microsoft.FSharp.Core.Operators.Checked`.


## <a name="summary-of-binary-comparison-operators"></a>Podsumowanie dla operatorów porównanie binarne
W poniższej tabeli przedstawiono operatory porównanie binarne, które są dostępne dla typów całkowitych i zmiennoprzecinkowych. Te operatory zwracają wartości typu `bool`.

Liczby zmiennoprzecinkowe należy nigdy nie bezpośrednio porównać pod kątem równości, ponieważ odwzorowanie liczby zmiennoprzecinkowej IEEE nie obsługuje operacji dokładne równości. Dwóch liczb, który można łatwo sprawdzić być taki sam, sprawdzając kod może być faktycznie bit różne oświadczenia.



|Operator|Uwagi|
|--------|-----|
|`=` (równości, jest równe)|To nie jest operatora przypisania. Jest on używany tylko do porównania. To jest ogólny operator.|
|`>` (więcej niż)|To jest ogólny operator.|
|`<` (poniżej)|To jest ogólny operator.|
|`>=` (większe lub równe)|To jest ogólny operator.|
|`<=` (mniej niż lub równe)|To jest ogólny operator.|
|`<>` (różne)|To jest ogólny operator.|

## <a name="overloaded-and-generic-operators"></a>Operatory przeciążone i rodzajowy
Wszystkie operatory omówione w tym temacie są zdefiniowane w **Microsoft.FSharp.Core.Operators** przestrzeni nazw. Niektóre operatory są definiowane za pomocą statycznie rozwiązywane parametry typu. Oznacza to, że są poszczególne definicje dla każdego określonego typu, który współpracuje z tego operatora. Wszystkie jednoargumentowy i operatory arytmetyczne i operatory binarne znajdują się w tej kategorii. Operatory porównania są ogólne, a więc pracować z dowolnego typu, a nie tylko pierwotne typy arytmetyczne. Rozróżnianą Unię i typy rekordów mają własne implementacji niestandardowych, które są generowane przez kompilator języka F #. Typy klas należy użyć metody <xref:System.Object.Equals%2A>.

Operatory ogólne są można dostosowywać. Aby dostosować porównanie funkcji, należy zastąpić <xref:System.Object.Equals%2A> Podaj porównania równości niestandardowe, a następnie wdrożyć to rozwiązanie <xref:System.IComparable>. <xref:System.IComparable?displayProperty=nameWithType> Interfejs zawiera tylko jedną metodę <xref:System.IComparable.CompareTo%2A> metody.


## <a name="operators-and-type-inference"></a>Operatory i wnioskowanie o typie
Używanie operatorów w wyrażeniu ogranicza wnioskowanie o typie na operatora. Korzystanie z operatorów uniemożliwia również, automatyczna Generalizacja, ponieważ typ arytmetyczny oznacza korzystanie z operatorów. W przypadku braku innych informacji wnioskuje kompilator języka F # `int` jako typ wyrażeniach arytmetycznych. To zachowanie można przesłonić, określając innego typu. W związku z tym typy argumentów i typ zwracany `function1` w następującym kodzie są wywnioskować można `int`, ale typy dla `function2` są wywnioskować za `float`.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3501.fs)]
    
## <a name="see-also"></a>Zobacz też
[Odwołanie do symboli i operatorów](index.md)

[Przeładowanie operatora](../operator-overloading.md)

[Operatory bitowe](bitwise-operators.md)

[Operatory logiczne](boolean-operators.md)
