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
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244780"
---
# <a name="return-c-reference"></a>return (odwołanie w C#)
`return` Kończy wykonywanie metody, w którym występuje i zwraca kontrolę do metody wywołującej. Może również zwracać wartość opcjonalna. Jeśli metoda jest `void` typu `return` instrukcji, można pominąć.  
  
 Jeśli znajduje się wewnątrz instrukcji return `try` bloku `finally` bloku, jeśli taki istnieje, zostanie wykonana zanim sterowanie powraca do wywoływania metody.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie metoda `CalculateArea()` zwraca zmienna lokalna `area` jako [double](../../../csharp/language-reference/keywords/double.md) wartość.  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [return, instrukcja](/cpp/cpp/return-statement-cpp)  
 [Instrukcje skoku](../../../csharp/language-reference/keywords/jump-statements.md)
