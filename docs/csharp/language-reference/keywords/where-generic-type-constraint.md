---
title: "where — Ograniczenie typu ogólnego (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords: where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2b7b159689aa771d3f9d59e3b1dd340c85b1d79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="where-generic-type-constraint-c-reference"></a>where — Ograniczenie typu ogólnego (odwołanie w C#)
W definicji typu ogólnego `where` klauzuli służy do określania warunków ograniczających dla typów, które mogą być używane jako argumenty dla parametru typu zdefiniowanego w deklaracji ogólnej. Na przykład można zadeklarować klasy ogólnej, `MyGenericClass`, że parametr typu `T` implementuje <xref:System.IComparable%601> interfejsu:  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  Aby uzyskać więcej informacji o tym, gdzie klauzula w wyrażeniu zapytania, zobacz [gdzie klauzuli](../../../csharp/language-reference/keywords/where-clause.md).  
  
 Oprócz ograniczeń interfejsu `where` klauzuli mogą zawierać ograniczenia klasy podstawowej, które stwierdza, że typ musi mieć określony klasy jako klasę podstawową (lub w tej samej klasy), aby można używać jako argumentu typu dla tego typu ogólnego. Jeśli używane jest takie ograniczenie, musi występować przed wszystkimi innymi ograniczeniami dla tego parametru typu.  
  
 [!code-csharp[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 `where` Klauzuli mogą również obejmować ograniczenie konstruktora. Można utworzyć wystąpienia typu parametru za pomocą operatora new; Jednak w tym celu parametr typu musi być ograniczone przez ograniczenie konstruktora `new()`. [Ograniczenia new()](../../../csharp/language-reference/keywords/new-constraint.md) umożliwia kompilatora wiedzieć, że wszelkie argumentu typu dostarczonego musi mieć dostęp bez parametrów--lub konstruktora domyślnego —. Na przykład:  
  
 [!code-csharp[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 `new()` Ograniczenia pojawia się w ostatniej `where` klauzuli.  
  
 Wiele parametrów typu, za pomocą jednego `where` klauzula dla każdego parametru typu, na przykład:  
  
 [!code-csharp[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 Można również dołączyć ograniczenia na parametry metody rodzajowe podobny do tego typu:  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 Zauważ, że opis ograniczenia parametru typu delegatów składni jest takie samo jak w przypadku metod:  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 Informacje ogólne delegatów, zobacz [delegatów](../../../csharp/programming-guide/generics/generic-delegates.md).  
  
 Aby uzyskać więcej informacji o składni i użycia ograniczenia, zobacz [ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [New — ograniczenie](../../../csharp/language-reference/keywords/new-constraint.md)  
 [Ograniczenia dotyczące parametrów typu](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
