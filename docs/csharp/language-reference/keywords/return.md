---
title: return (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 29d2b8e28ae6240b9d06b82695efe1736404c5cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33266113"
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
 [return, instrukcja](/cpp/cpp/return-statement-cpp)  
 [Instrukcje skoku](../../../csharp/language-reference/keywords/jump-statements.md)
