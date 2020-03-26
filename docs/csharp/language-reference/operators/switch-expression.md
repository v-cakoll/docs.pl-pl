---
title: wyrażenie switch - odwołanie do języka C#
description: Dowiedz się, jak używać wyrażenia przełącznika C# do dopasowywania wzorców i introspekcji innych danych
ms.date: 03/19/2020
ms.openlocfilehash: 9e609bcea0f92f492b5f9b07840e47f75c1b71e4
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249789"
---
# <a name="switch-expression-c-reference"></a>wyrażenie switch (odwołanie do języka C#)

W tym `switch` artykule opisano wyrażenie wprowadzone w języku C# 8.0. Aby uzyskać `switch` informacje na temat instrukcji, zobacz artykuł na [ `switch` instrukcji](../keywords/switch.md) w sekcji [instrukcji.](../keywords/index.md)

## <a name="basic-example"></a>Przykład podstawowy

Wyrażenie `switch` zawiera `switch`semantyka -like w kontekście wyrażenia. Zapewnia zwięzłą składnię, gdy ramiona przełącznika wytwarzają wartość. W poniższym przykładzie przedstawiono strukturę wyrażenia przełącznika. Tłumaczy wartości z `enum` reprezentujących kierunków wizualnych na mapie online do odpowiedniego kierunku kardynalnego:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetBasicStructure":::

W poprzednim przykładzie przedstawiono podstawowe elementy wyrażenia switch:

- Wyrażenie *zakresu*: W poprzednim przykładzie `direction` użyto zmiennej jako wyrażenia zakresu.
- Ramiona *wyrażenia przełącznika*: Każde ramię wyrażenia przełącznika zawiera `=>` *wzorzec,* opcjonalną *osłonę przypadków,* token i *wyrażenie.*

Wynikiem wyrażenia *switch* jest wartość wyrażenia pierwszego *ramienia wyrażenia przełącznika,* którego `true` *wzorzec* pasuje do *wyrażenia zakresu* i którego *przyczyna jest chronina*, jeśli jest obecna, ocenia . *Wyrażenie* po prawej stronie `=>` tokenu nie może być instrukcją wyrażenia.

*Ramiona wyrażenia przełącznika* są oceniane w kolejności tekstowej. Kompilator generuje błąd, gdy nie można wybrać *dolnego ramienia wyrażenia przełącznika,* ponieważ wyższe *ramię wyrażenia przełącznika* pasuje do wszystkich jego wartości.

## <a name="patterns-and-case-guards"></a>Wzory i osłony etui

Wiele wzorców są obsługiwane w ramionach wyrażenia przełącznika. W poprzednim przykładzie użyto *wzorca wartości*. *Wzorzec wartości* porównuje wyrażenie zakresu z wartością. Ta wartość musi być stałą czasu kompilacji. *Wzorzec typu* porównuje wyrażenie zakresu do znanego typu. Poniższy przykład pobiera trzeci element z sekwencji. Wykorzystuje różne metody w oparciu o typ sekwencji:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetTypePattern":::

Wzorce mogą być cykliczne, gdzie wzorzec testuje typ, a jeśli ten typ pasuje, wzorzec pasuje do jednej lub więcej wartości właściwości w wyrażeniu zakresu. Można użyć wzorców cyklicznych, aby rozszerzyć poprzedni przykład. Dodano ramiona wyrażenia przełącznika dla tablic, które mają mniej niż 3 elementy. Wzorce cykliczne są pokazane w poniższym przykładzie:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetRecursivePattern":::

Wzorce cykliczne można zbadać właściwości wyrażenia zakresu, ale nie można wykonać dowolny kod. Można użyć *ochrony spraw*, `when` określone w klauzuli, aby zapewnić podobne kontrole dla innych typów sekwencji:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetGuardCase":::

Na koniec można dodać `_` wzorzec i `null` wzorzec, aby złapać argumenty, które nie są przetwarzane przez inne ramię wyrażenia przełącznika. To sprawia, że wyrażenie switch *jest wyczerpujące,* co oznacza, że obsługiwana jest dowolna możliwa wartość wyrażenia zakresu. W poniższym przykładzie dodano te ramiona wyrażenia:

:::code language="csharp" source="snippets/SwitchExpressions.cs" id="SnippetExhaustive":::

W poprzednim przykładzie `null` dodaje wzorzec i zmienia wzorzec `IEnumerable<T>` typu na szyk. `_` Wzorzec `null` zapewnia sprawdzenie wartości null jako ramię wyrażenia przełącznika. Wyrażenie dla tego ramienia <xref:System.ArgumentNullException>rzuca . Wzorzec `_` pasuje do wszystkich danych wejściowych, które nie zostały dopasowane przez poprzednie ramiona. Musi przyjść po `null` czeku lub `null` będzie pasować do danych wejściowych.

Możesz przeczytać więcej w propozycji specyfikacji języka C# dla [wzorców cyklicznych](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Dopasowanie do wzorca](../../pattern-matching.md)
