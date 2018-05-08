---
title: unchecked (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: d7a48950b7158be3cd589c20fbfe0661f3c9c5af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="unchecked-c-reference"></a>unchecked (odwołanie w C#)
`unchecked` Słowo kluczowe jest używane do pomijania sprawdzania przepełnienia dla operacji arytmetycznych typem całkowitym i konwersje.  
  
 W kontekście zaznaczenie opcji Jeśli wyrażenie zwraca wartość, która jest poza zakresem typu docelowego przeciążenia nie jest oznaczony. Na przykład obliczeń w poniższym przykładzie jest wykonywana w `unchecked` bloku lub wyrażenie, fakt, że wynik jest za duża dla typu integer jest ignorowana, a `int1` jest przypisywana wartość-2,147,483,639.  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 Jeśli `unchecked` środowiska zostanie usunięty, występuje błąd kompilacji. Mogą być wykrywane przepełnienie w czasie kompilacji, ponieważ wszystkie warunki wyrażenie stałe.  
  
 Wyrażeń, które zawierają postanowienia z systemem innym niż stała jest zaznaczony domyślnie w czasie kompilacji i czasu wykonywania. Zobacz [zaznaczone](../../../csharp/language-reference/keywords/checked.md) informacji na temat włączania zaznaczone środowiska.  
  
 Ponieważ sprawdzania przepełnienia jest czasochłonne, użycie niezaznaczone kodu w sytuacjach, gdy istnieje niebezpieczeństwo z przepełnienie może zwiększyć wydajność. Jednak jeśli przepełnienia jest możliwość, można użyć środowiska zaznaczenia.  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia sposób użycia `unchecked` — słowo kluczowe.  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Checked i Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [checked](../../../csharp/language-reference/keywords/checked.md)
