---
title: wyrażenie Switch — odwołanie w C#
description: Dowiedz się, jak używać wyrażenia przełącznika C# na potrzeby dopasowywania wzorców i innych danych introspekcji
ms.date: 03/19/2020
ms.openlocfilehash: f53cbe873c841271f64496e4e5ff1f11750c7b8a
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140664"
---
# <a name="switch-expression-c-reference"></a>Switch — wyrażenie (odwołanie w C#)

W tym artykule opisano `switch` wyrażenie wprowadzone w języku C# 8,0. Aby uzyskać informacje na `switch` temat instrukcji, zobacz artykuł w [ `switch` instrukcji](../keywords/switch.md) w sekcji [instrukcje](../keywords/index.md) .

## <a name="basic-example"></a>Przykład podstawowy

`switch` Wyrażenie zapewnia `switch`semantykę podobną w kontekście wyrażenia. Zapewnia zwięzłą składnię, gdy broń przełączania wygenerowała wartość. Poniższy przykład pokazuje strukturę wyrażenia przełącznika. Tłumaczy wartości z `enum` reprezentujących kierunków wizualizacji w mapie online na odpowiedni kierunek kardynalny:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetBasicStructure":::

Powyższy przykład pokazuje podstawowe elementy wyrażenia przełącznika:

- *Wyrażenie zakresu*: w poprzednim przykładzie użyta jest zmienna `direction` jako wyrażenie zakresu.
- *Broń wyrażenia przełącznika*: każde wyrażenie Switch ARM zawiera *wzorzec*, opcjonalną ochronę przed *przypadkami*, `=>` token i *wyrażenie*.

Wynik *wyrażenia Switch* jest wartością wyrażenia pierwszego *przełącznika ARM* , którego *wzorzec* dopasowuje *wyrażenie zakresu* i którego funkcja *Case Guard*(jeśli jest obecna) zwraca wartość `true`. *Wyrażenie* po prawej stronie `=>` tokenu nie może być instrukcją wyrażenia.

*Poręcze wyrażeń przełącznika* są oceniane w kolejności tekstu. Kompilator generuje błąd, gdy nie można wybrać dolnego *wyrażenia Switch ARM* , ponieważ wyższe *wyrażenie Switch ARM* dopasowuje wszystkie jego wartości.

## <a name="patterns-and-case-guards"></a>Wzorce i osłony przypadków

Wiele wzorców jest obsługiwanych w przypadku zamiany wyrazów wyrażeń. W poprzednim przykładzie użyto *wzorca wartości*. *Wzorzec wartości* porównuje wyrażenie zakresu z wartością. Ta wartość musi być stałą czasu kompilacji. *Wzorzec typu* porównuje wyrażenie zakresu z znanym typem. Poniższy przykład pobiera trzeci element z sekwencji. Używa różnych metod opartych na typie sekwencji:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetTypePattern":::

Wzorce mogą być cykliczne, gdzie wzorzec testuje typ, a jeśli ten typ pasuje, wzorzec dopasowuje co najmniej jedną wartość właściwości w wyrażeniu zakresu. Możesz użyć wzorców cyklicznych, aby zwiększyć poprzedni przykład. Należy dodać broń wyrażenia przełącznika dla tablic, które mają mniej niż 3 elementy. Wzorce cykliczne są wyświetlane w następującym przykładzie:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetRecursivePattern":::

Wzorce cykliczne mogą przebadać właściwości wyrażenia zakresu, ale nie mogą wykonać dowolnego kodu. Aby zapewnić podobne sprawdzenia *case guard*dla innych typów sekwencji, można `when` użyć funkcji Case, określonej w klauzuli.

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetGuardCase":::

Na koniec można dodać `_` wzorzec i `null` wzorzec do przechwytywania argumentów, które nie są przetwarzane przez żadną inną pozycję wyrażenia Switch ARM. Powoduje to, że wyrażenie Switch jest *wyczerpujące*, co oznacza, że jest obsługiwana jakakolwiek możliwa wartość wyrażenia zakresu. Poniższy przykład dodaje te broń dla wyrażeń:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetExhaustive":::

Poprzedni przykład dodaje `null` wzorzec i zmienia wzorzec `IEnumerable<T>` typu do `_` wzorca. `null` Wzorzec zawiera sprawdzanie wartości null jako rolę Switch ARM. Wyrażenie dla tego ARM zgłasza <xref:System.ArgumentNullException>. `_` Wzorzec dopasowuje wszystkie dane wejściowe, które nie zostały dopasowane przez poprzednie poręcze. Musi występować po sprawdzeniu `null` lub będzie pasować `null` do danych wejściowych.

Więcej informacji można znaleźć w temacie Specyfikacja języka C# dla [wzorców cyklicznych](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Dopasowanie wzorca](../../pattern-matching.md)
