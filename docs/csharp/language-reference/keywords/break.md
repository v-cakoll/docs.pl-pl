---
title: "break (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords: break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b533d325be41683ed6f56e9e63b3c11ddde9cb17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="break-c-reference"></a>break (odwołanie w C#)
`break` Instrukcji kończy najbliższej otaczającej pętli lub [przełącznika](../../../csharp/language-reference/keywords/switch.md) instrukcji, w której znajduje się. Kontrola jest przekazywana do instrukcji następującej instrukcji zakończone, jeśli istnieje.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie instrukcji warunkowej zawiera licznika, który ma zostać liczba z zakresu od 1 do 100; jednak `break` instrukcji pętli kończy się po liczby 4.  
  
 [!code-csharp[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie `break` używana jest instrukcja break poza wewnętrzny pętli zagnieżdżonych i zwrócić kontrolkę do zewnętrznego pętli.  
  
 [!code-csharp[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono użycie `break` w [przełącznika](../../../csharp/language-reference/keywords/switch.md) instrukcji.  
  
 [!code-csharp[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 Jeśli wprowadzono `4`, będą dane wyjściowe:  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Przełącznik](../../../csharp/language-reference/keywords/switch.md)  
 [Instrukcje skoku](../../../csharp/language-reference/keywords/jump-statements.md)  
 [Iteracja — instrukcje](../../../csharp/language-reference/keywords/iteration-statements.md)
