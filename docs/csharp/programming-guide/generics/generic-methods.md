---
title: Metody ogólne — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 5f066ca39c97b70554886e423c37c4ee47d49158
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712198"
---
# <a name="generic-methods-c-programming-guide"></a>Metody ogólne (Przewodnik programowania w języku C#)
Metoda generyczna jest metodą zadeklarowaną z parametrami typu w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#22)]  
  
 Poniższy przykład kodu przedstawia jeden ze sposobów wywoływania metody przy użyciu `int` dla argumentu typu:  
  
 [!code-csharp[csProgGuideGenerics#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#23)]  
  
 Można również pominąć argument typu i kompilator wywnioskuje go. Następujące wywołanie `Swap` jest równoważne z poprzednim wywołaniem:  
  
 [!code-csharp[csProgGuideGenerics#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#24)]  
  
 Te same reguły wnioskowania o typie mają zastosowanie do metod statycznych i metod wystąpień. Kompilator może wywnioskować parametry typu na podstawie argumentów metody, które są przekazywane; nie można wywnioskować parametrów typu tylko z ograniczenia lub wartości zwracanej. W związku z tym, wnioskowanie typu nie działa z metodami, które nie mają parametrów. Wnioskowanie o typie występuje w czasie kompilacji, zanim kompilator próbuje rozpoznać przeciążone sygnatury metod. Kompilator stosuje logikę wnioskowania typu do wszystkich metod ogólnych, które mają taką samą nazwę. W kroku rozwiązywanie przeciążenia kompilator zawiera tylko te metody ogólne, dla których wnioskowanie typu zostało zakończone powodzeniem.  
  
 W ramach klasy generycznej metody niegeneryczne mogą uzyskać dostęp do parametrów typu poziomu klasy w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#25)]  
  
 W przypadku zdefiniowania metody ogólnej, która przyjmuje takie same parametry typu jak Klasa zawierająca, kompilator generuje ostrzeżenie [CS0693](../../misc/cs0693.md) , ponieważ w zakresie metody argument dostarczony dla wewnętrznego `T` ukrywa argument podany dla `T`zewnętrznych. Jeśli wymagana jest elastyczność wywoływania metody klasy generycznej z argumentami typu innym niż podane podczas tworzenia wystąpienia klasy, należy rozważyć dostarczenie innego identyfikatora dla parametru typu metody, jak pokazano w `GenericList2<T>` w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideGenerics#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#26)]  
  
 Użyj ograniczeń, aby włączyć bardziej wyspecjalizowane operacje dotyczące parametrów typu w metodach. Ta wersja `Swap<T>`, teraz o nazwie `SwapIfGreater<T>`, może być używana tylko z argumentami typu, które implementują <xref:System.IComparable%601>.  
  
 [!code-csharp[csProgGuideGenerics#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#27)]  
  
 Metody generyczne mogą być przeciążone dla kilku parametrów typu. Na przykład następujące metody mogą znajdować się w tej samej klasie:  
  
 [!code-csharp[csProgGuideGenerics#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#28)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](~/_csharplang/spec/classes.md#methods).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [Metody](../classes-and-structs/methods.md)
