---
title: unchecked — C# odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: c31f1243b1394bfe826b02c14c73faf402640849
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608416"
---
# <a name="unchecked-c-reference"></a>unchecked (odwołanie w C#)

`unchecked` Słowo kluczowe jest używane do pomijania sprawdzania przepełnienia dla operacji arytmetycznych i konwersji typu całkowitego.

W niesprawdzonym kontekście, jeśli wyrażenie generuje wartość spoza zakresu typu docelowego, przepełnienie nie jest oflagowane. Na przykład, ponieważ obliczenia w poniższym przykładzie są wykonywane w `unchecked` bloku lub wyrażeniu, fakt, że wynik jest za duży dla liczby całkowitej, jest ignorowany i `int1` ma przypisaną wartość-2 147 483 639.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

`unchecked` Jeśli środowisko zostanie usunięte, wystąpi błąd kompilacji. Przepełnienie można wykryć w czasie kompilacji, ponieważ wszystkie warunki wyrażenia są stałymi.

Wyrażenia zawierające warunki niestałe są domyślnie niezaznaczone w czasie kompilacji i w czasie wykonywania. Zobacz [zaewidencjonowano](checked.md) , aby uzyskać informacje na temat włączania sprawdzonego środowiska.

Ze względu na to, że sprawdzanie przepełnienia jest czasochłonne, użycie niesprawdzonego kodu w sytuacjach, gdy nie ma żadnych niebezpieczeństwa przepełnienia może zwiększyć wydajność. Jeśli jednak przepełnienie jest możliwe, należy użyć zaznaczonego środowiska.

## <a name="example"></a>Przykład

Ten przykład pokazuje, `unchecked` jak używać słowa kluczowego.

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Checked i Unchecked](checked-and-unchecked.md)
- [checked](checked.md)
