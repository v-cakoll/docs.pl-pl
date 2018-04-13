---
title: unchecked (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c05e7cb742d8e8f5a7804656a5ec13548d0498b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Zaznaczony i niezaznaczony](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [zaznaczone](../../../csharp/language-reference/keywords/checked.md)
