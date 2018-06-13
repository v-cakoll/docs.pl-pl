---
title: explicit (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: c8a05aef3318eb34242ed1268ea26663592e4d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216480"
---
# <a name="explicit-c-reference"></a>explicit (odwołanie w C#)
`explicit` — Słowo kluczowe deklaruje typ zdefiniowany przez użytkownika operatora konwersji, które muszą być wywoływane z rzutowanie. Na przykład tego operatora konwertuje z klasy o nazwie f do klasy o nazwie c:  
  
 [!code-csharp[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 Można wywołać tego operatora konwersji następująco:  
  
 [!code-csharp[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 Operator konwersji konwertuje typu źródłowego na typ docelowy. Typ źródłowy zawiera operator konwersji. W odróżnieniu od niejawna konwersja operatory jawnej konwersji muszą być wywoływane za pomocą rzutowanie. Jeśli operacja konwersji może spowodować wyjątków lub utratę informacji, należy oznaczyć go `explicit`. Zapobiega to dyskretnie wywoływania operacji konwersji z prawdopodobnie nieprzewidziane skutki przez kompilator.  
  
 Pominięcie rzutowania spowoduje błąd kompilacji CS0266.  
  
 Aby uzyskać więcej informacji, zobacz [przy użyciu operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `Fahrenheit` i `Celsius` klasy, z których każdy zawiera operator jawnej konwersji do innej klasy.  
  
 [!code-csharp[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano strukturę, `Digit`, który reprezentuje pojedynczą cyfrą dziesiętną. Operator jest zdefiniowany dla konwersji z `byte` do `Digit`, ale ponieważ nie wszystkie bajty można przekonwertować na `Digit`, konwersja jest jawne.  
  
 [!code-csharp[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [implicit](../../../csharp/language-reference/keywords/implicit.md)  
 [Operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md)  
 [Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 [Tworzenie łańcucha zdefiniowane przez użytkownika Konwersje jawne w języku C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
