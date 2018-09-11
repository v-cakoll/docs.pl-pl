---
title: Typy ogólne i atrybuty (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 0fe2d61001584aa7c175500bfa754b2ae2244660
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272686"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Typy ogólne i atrybuty (Przewodnik programowania w języku C#)
Można można zastosować atrybutów do typów ogólnych w taki sam sposób jak typów innych niż ogólne. Aby uzyskać więcej informacji na temat stosowania atrybutów, zobacz [atrybuty](../../../csharp/programming-guide/concepts/attributes/index.md).  
  
 Atrybuty niestandardowe są dozwolone tylko k odkazu otwartych typów ogólnych, które są typy rodzajowe, dla którego nie podano argumentów i zamkniętych skonstruowany typów ogólnych, które dostarczają argumenty dla wszystkich parametrów typu.  
  
 W poniższych przykładach używane jest to atrybut niestandardowy:  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 To otwarty typ ogólny może odwoływać się do atrybutu:  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 Określ wiele parametrów typu przy użyciu odpowiedniej liczby przecinkami. W tym przykładzie `GenericClass2` ma dwa parametry typu:  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 Atrybut można odwołać się do zamkniętego skonstruowany typ rodzajowy:  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 Atrybut, który odwołuje się do parametru typu ogólnego spowoduje błąd w czasie kompilacji:  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 Typ ogólny nie może dziedziczyć z <xref:System.Attribute>:  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 Aby uzyskać informacje dotyczące typu ogólnego lub parametr typu w czasie wykonywania, można użyć metody <xref:System.Reflection>. Aby uzyskać więcej informacji, zobacz [typy ogólne i odbicie](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Typy ogólne](../../../csharp/programming-guide/generics/index.md)  
- [Atrybuty](../../../../docs/standard/attributes/index.md)
