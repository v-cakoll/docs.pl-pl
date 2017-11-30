---
title: "as (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4f2964f32a4139ffeb6d51b761f1176a57c5be6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="as-c-reference"></a>as (odwołanie w C#)
Można użyć `as` operator do wykonania niektórych typów konwersji między typami zgodne odwołanie lub [typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md). Poniższy kod przedstawia przykład.  
  
 [!code-csharp[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a>Uwagi  
 `as` Operator przypomina operacji rzutowania. Jednak jeśli konwersja nie jest możliwe, `as` zwraca `null` zamiast generowanie wyjątków. Rozważmy następujący przykład:  
  
```  
expression as type  
```  
  
 Kod jest odpowiednikiem następującego wyrażenia z wyjątkiem `expression` zmiennej jest oceniane tylko jeden raz.  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 Należy pamiętać, że `as` operator wykonuje konwersji odwołania, konwersji wartości null i konwersje boxing. `as` Operatora nie można wykonać innych konwersji, takich jak konwersje zdefiniowane przez użytkownika, których należy zamiast tego można wykonać za pomocą wyrażenia rzutowania.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [jest](../../../csharp/language-reference/keywords/is.md)  
 [?: — Operator](../../../csharp/language-reference/operators/conditional-operator.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)
