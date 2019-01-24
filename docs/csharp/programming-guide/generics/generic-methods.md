---
title: Metody ogólne — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: a32309af150685ec1e6280b26d82a57082c1bdbd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681238"
---
# <a name="generic-methods-c-programming-guide"></a>Metody ogólne (Przewodnik programowania w języku C#)
Metody ogólnej to metoda, która jest zadeklarowana za pomocą parametrów typu w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 Poniższy przykład kodu przedstawia sposób wywołania metody przy użyciu `int` dla argumentu typu:  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 Można również pominąć argument typu, a kompilator wywnioskuje go. Następujące wywołanie do `Swap` jest odpowiednikiem poprzedniego wywołania:  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 Te same reguły wnioskowania o typie dotyczą metod statycznych i metod wystąpienia. Kompilator może wywnioskować parametry typu, na podstawie argumentów metody, które są przekazywane w; Nie można go wywnioskować parametrów typu tylko z ograniczeniem lub wartość zwracana. Wnioskowanie o typie w związku z tym nie działa z metod, które nie mają parametrów. Wnioskowanie o typie występuje w czasie kompilacji, zanim kompilator próbuje rozpoznać podpisy przeciążonej metody. Kompilator stosuje logikę wnioskowania typu, do wszystkich metod ogólnych, które mają taką samą nazwę. W kroku rozdzielczość przeciążenia kompilator zawiera tylko metod ogólnych na których wnioskowanie o typie zakończyło się pomyślnie.  
  
 W obrębie klasy ogólnej metody nieogólnego mieli dostęp do parametrów typu na poziomie klasy, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 Jeśli zdefiniujesz metody rodzajowej, która przyjmuje te same parametry typu jako klasa zawierająca, kompilator generuje ostrzeżenie CS0693, ponieważ w zakresie metody argument podany dla wewnętrzny `T` ukrywa argument podany dla zewnętrznego `T`. Jeśli wymagana jest elastyczność wywoływania metody rodzajowej klasy z argumentami typu innych niż podany przy wywołaniu metody wystąpienia klasy, rozważ podanie inny identyfikator dla parametru typu metody, jak pokazano na `GenericList2<T>` poniżej przykład.  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 Użyj ograniczeń, aby włączyć bardziej wyspecjalizowane operacje dotyczące parametrów typu w metodzie. Ta wersja `Swap<T>`teraz nazwanego `SwapIfGreater<T>`, należy używać tylko z argumentami typu, które implementują <xref:System.IComparable%601>.  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 Metody ogólne mogą być przeciążane na kilka parametrów typu. Na przykład następujące metody mogą wszystkie znajdować się w tej samej klasy:  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](~/_csharplang/spec/classes.md#methods).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
