---
title: as (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 6ea5346119259d70ac1a42f3f72a8b2746b8f536
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 [is](../../../csharp/language-reference/keywords/is.md)  
 [?:, operator](../../../csharp/language-reference/operators/conditional-operator.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)
