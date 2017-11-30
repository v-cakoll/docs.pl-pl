---
title: "return (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 90c84b51c6ee57864eac552bc488c9f9c15e9394
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="return-c-reference"></a>return (odwołanie w C#)
`return` Instrukcji kończy wykonywanie metody, w którym pojawi się i zwraca sterowania do wywoływania metody. Może on również zwrócić wartość opcjonalna. Jeśli metoda jest `void` typu `return` instrukcji można pominąć.  
  
 Jeśli znajduje się wewnątrz instrukcji return `try` bloku `finally` bloku, jeśli istnieje, zostanie wykonana przed kontroli zwraca do wywoływania metody.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie metoda `CalculateArea()` zwraca zmiennej lokalnej `area` jako [podwójne](../../../csharp/language-reference/keywords/double.md) wartość.  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Return — instrukcja](/cpp/cpp/return-statement-cpp)  
 [Instrukcje skoku](../../../csharp/language-reference/keywords/jump-statements.md)
