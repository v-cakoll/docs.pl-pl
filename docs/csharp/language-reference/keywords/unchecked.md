---
title: unchecked — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 44301333f7a36e6b0baa6ea9e089d930bb485a45
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238458"
---
# <a name="unchecked-c-reference"></a>unchecked (odwołanie w C#)

`unchecked` Słowo kluczowe jest używane, aby pominąć sprawdzanie przepełnienia dla typu całkowitego operacje arytmetyczne i konwersje.

W kontekście niesprawdzanym Jeśli wyrażenie generuje wartość, która znajduje się poza zakresem typu docelowego przeciążenia nie jest oznaczony. Na przykład ponieważ obliczenie w poniższym przykładzie jest wykonywane w `unchecked` bloku lub wyrażenie, fakt, że wynik jest za duży dla liczby całkowitej jest ignorowana, a `int1` jest przypisywana wartość-2,147,483,639.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

Jeśli `unchecked` środowiska zostanie usunięty, pojawia się błąd kompilacji. Ponieważ wszystkie warunki wyrażenia są stałe, można wykryć przepełnienie w czasie kompilacji.

Wyrażenia, które zawierają wartość niebędącą stałą warunki nie domyślnie są zaznaczone w czasie kompilacji i czasu wykonywania. Zobacz [zaznaczone](checked.md) informacji na temat włączania środowiska zaznaczone.

Ponieważ sprawdzania dla przepełnienia zajmuje trochę czasu, użycie unchecked kodu w sytuacjach, gdy ma zagrożenia przepełnienia może zwiększyć wydajność. Jednak jeśli przepełnienia jest możliwość, należy użyć środowiska zaznaczone.

## <a name="example"></a>Przykład

Ten przykład ilustruje sposób używania `unchecked` — słowo kluczowe.

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Checked i Unchecked](checked-and-unchecked.md)
- [checked](checked.md)