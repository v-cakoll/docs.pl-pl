---
title: Metody ogólne — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 5f066ca39c97b70554886e423c37c4ee47d49158
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712198"
---
# <a name="generic-methods-c-programming-guide"></a>Metody ogólne (Przewodnik programowania w języku C#)
Metoda ogólna jest metodą, która jest zadeklarowana z parametrami typu, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 Poniższy przykład kodu pokazuje jeden sposób wywołania metody przy użyciu `int` argumentu typu:  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 Można również pominąć argument typu i kompilator wywnioskuje go. Następujące wywołanie `Swap` jest równoważne z poprzednim wywołaniem:  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 Te same reguły wnioskowania o typie mają zastosowanie do metod statycznych i metod wystąpienia. Kompilator można wywnioskować parametry typu na podstawie argumentów metody, które można przekazać w; nie można wywnioskować parametrów typu tylko z ograniczenia lub wartości zwracanej. W związku z tym wnioskowanie o typie nie działa z metodami, które nie mają parametrów. Wnioskowanie o typie występuje w czasie kompilacji, zanim kompilator spróbuje rozwiązać przeciążone podpisy metody. Kompilator stosuje logikę wnioskowania o typie do wszystkich metod ogólnych, które mają tę samą nazwę. W kroku rozpoznawania przeciążenia kompilator zawiera tylko te metody ogólne, na których wnioskowanie typu powiodło się.  
  
 W klasie ogólnej metody nieogólne mogą uzyskiwać dostęp do parametrów typu na poziomie klasy w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 Jeśli zdefiniujesz metodę rodzajową, która przyjmuje parametry tego samego typu, co klasa zawierająca, kompilator generuje ostrzeżenie `T` [CS0693,](../../misc/cs0693.md) ponieważ w zakresie metody argument podany dla wewnętrznej ukrywa argument dostarczony dla zewnętrznego `T`. Jeśli potrzebujesz elastyczności wywoływania metody klasy ogólnej z argumentami typu innymi niż te podane, gdy klasa została uprzedzona, należy `GenericList2<T>` rozważyć podanie innego identyfikatora parametru typu metody, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 Użyj ograniczeń, aby włączyć bardziej wyspecjalizowane operacje parametrów typu w metodach. Ta wersja `Swap<T>`, `SwapIfGreater<T>`teraz o nazwie , może <xref:System.IComparable%601>być używana tylko z argumentami typu, które implementują .  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 Metody ogólne mogą być przeciążone na kilka parametrów typu. Na przykład wszystkie następujące metody mogą znajdować się w tej samej klasie:  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](~/_csharplang/spec/classes.md#methods).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- [Przewodnik programowania języka C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [Metody](../classes-and-structs/methods.md)
