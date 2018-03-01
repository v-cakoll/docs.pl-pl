---
title: "checked (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ae77894cdc94e41dfa281b92ed3304e0dc25731
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="checked-c-reference"></a>checked (odwołanie w C#)
`checked` Słowo kluczowe jest używane do jawnie włączyć sprawdzanie operacji arytmetycznych typem całkowitym i konwersje przepełnienia.  
  
 Domyślnie wyrażenie, które zawiera tylko wartości stałych powoduje wystąpi błąd kompilatora, jeśli wyrażenie zwraca wartość, która jest poza zakresem typu docelowego. Jeśli wyrażenie zawiera jedną lub więcej wartości niż stała, kompilator nie wykrywa przeciążenia. Obliczenie wyrażenia przypisane do `i2` w poniższym przykładzie nie powoduje błąd kompilatora.  
  
 [!code-csharp[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 Domyślnie wyrażenia te z systemem innym niż stała nie są sprawdzane dla przepełnienie w czasie wykonywania albo, a nie wywołuj wyjątków przepełnienia. Poprzedni przykład przedstawia-2,147,483,639 jako suma wartości dwie dodatnie liczby całkowite.  
  
 Sprawdzanie przepełnienia można włączyć opcji kompilatora, konfiguracji środowiska lub użycie `checked` — słowo kluczowe. W poniższych przykładach pokazano, jak używać `checked` wyrażenie lub `checked` bloku, aby wykryć przepełnienie, wytworzonego przez poprzednie sum w czasie wykonywania. Oba przykłady zgłosić wyjątek przepełnienia.  
  
 [!code-csharp[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 [Niezaznaczone](../../../csharp/language-reference/keywords/unchecked.md) — słowo kluczowe może służyć do zapobiec sprawdzanie przepełnienia.  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia sposób użycia `checked` umożliwiające przepełnienie sprawdzenie w czasie wykonywania.  
  
 [!code-csharp[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Zaznaczony i niezaznaczony](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md)
