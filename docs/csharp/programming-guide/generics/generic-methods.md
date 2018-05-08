---
title: Metody ogólne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 04bc59d41eb7883e08138382b396bc737c7f11bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="generic-methods-c-programming-guide"></a>Metody ogólne (Przewodnik programowania w języku C#)
Metoda rodzajowa jest to metoda, która jest zadeklarowana z parametrami typu, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 Poniższy przykładowy kod przedstawia sposób wywołania metody przy użyciu `int` argumentu typu:  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 Można również pominąć argument typu i kompilator wywnioskuje go. Następujące wywołanie do `Swap` jest odpowiednikiem poprzedniego wywołania:  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 Wnioskowanie o typie te same zasady dotyczą metody statyczne i metody wystąpienia. Kompilator może wnioskować parametrów typu w oparciu argumenty metody, które przekazujesz Nie można go wywnioskować parametrów typu tylko z ograniczeniem ani zwracanej wartości. Wnioskowanie o typie w związku z tym nie działa z metod, które nie mają parametrów. Wnioskowanie o typie występuje w czasie kompilacji przed kompilator próbuje rozpoznać podpisy przeciążonej metody. Kompilator dotyczy wszystkich metod ogólnych, które ma taką samą nazwę logiki wnioskowania typu. W kroku rozpoznawanie przeciążenia kompilator obejmuje tylko metody ogólne na których wnioskowanie o typie zakończyło się pomyślnie.  
  
 W klasie ogólnej metody nieogólnego mogą uzyskiwać dostęp do parametrów typu poziomie klasy, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 Po zdefiniowaniu Metoda ogólna, który przyjmuje takie same parametry typu jako klasa zawierająca kompilator generuje ostrzeżenie CS0693, ponieważ w zakresie metody argument dostarczony dla wewnętrznej `T` ukrywa argument dostarczony dla zewnętrznego `T`. Jeśli potrzebujesz elastyczność podczas wywoływania metody ogólnej klasy z argumentami typu innych niż podany przy wywołaniu metody wystąpienia klasy, rozważ podanie inny identyfikator dla parametru typu metody, jak pokazano w `GenericList2<T>` poniżej przykład.  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 Użyj ograniczenia, aby włączyć wyspecjalizowanego operacje dotyczące parametrów typu w metodach. Ta wersja `Swap<T>`teraz nazwanego `SwapIfGreater<T>`, można używać tylko z argumentami typu, które implementują <xref:System.IComparable%601>.  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 Metody ogólne można przeciążać na kilka parametrów typu. Na przykład następujących metod można wszystkie znajdować się w tej samej klasy:  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)
