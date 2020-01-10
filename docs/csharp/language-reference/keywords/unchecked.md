---
title: unchecked — C# odwołanie
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 6dad0dfd508fb390dd0a52d1b48d70b4c5725513
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713004"
---
# <a name="unchecked-c-reference"></a>unchecked (odwołanie w C#)

Słowo kluczowe `unchecked` służy do pomijania sprawdzania przepełnienia dla operacji arytmetycznych i konwersji typu całkowitego.

W niesprawdzonym kontekście, jeśli wyrażenie generuje wartość spoza zakresu typu docelowego, przepełnienie nie jest oflagowane. Na przykład, ponieważ obliczenia w poniższym przykładzie są wykonywane w bloku `unchecked` lub wyrażeniu, fakt, że wynik jest za duży dla liczby całkowitej, jest ignorowany, a `int1` ma przypisaną wartość-2 147 483 639.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

Jeśli środowisko `unchecked` zostanie usunięte, wystąpi błąd kompilacji. Przepełnienie można wykryć w czasie kompilacji, ponieważ wszystkie warunki wyrażenia są stałymi.

Wyrażenia zawierające warunki niestałe są domyślnie niezaznaczone w czasie kompilacji i w czasie wykonywania. Zobacz [zaewidencjonowano](checked.md) , aby uzyskać informacje na temat włączania sprawdzonego środowiska.

Ze względu na to, że sprawdzanie przepełnienia jest czasochłonne, użycie niesprawdzonego kodu w sytuacjach, gdy nie ma żadnych niebezpieczeństwa przepełnienia może zwiększyć wydajność. Jeśli jednak przepełnienie jest możliwe, należy użyć zaznaczonego środowiska.

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak używać słowa kluczowego `unchecked`.

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Checked i Unchecked](checked-and-unchecked.md)
- [checked](checked.md)
