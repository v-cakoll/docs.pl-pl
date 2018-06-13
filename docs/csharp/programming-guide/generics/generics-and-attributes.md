---
title: Typy ogólne i atrybuty (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 3bfb4028fb5efce693abd83b40636b0149962e3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339683"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Typy ogólne i atrybuty (Przewodnik programowania w języku C#)
Atrybuty może odnosić się do typów ogólnych w taki sam sposób jak typy nierodzajową. Aby uzyskać więcej informacji na temat stosowania atrybutów, zobacz [atrybutów](../../../csharp/programming-guide/concepts/attributes/index.md).  
  
 Atrybuty niestandardowe są dozwolone tylko do odwołania Otwórz typów ogólnych, które są typów ogólnych, dla jakiego typu nie podano argumentów i zamknięte skonstruowane typów ogólnych, które dostarczają argumenty dla wszystkich parametrów typu.  
  
 W poniższych przykładach użyto tego atrybutu niestandardowego:  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 Atrybut może odwoływać się otwartym typem ogólnym:  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 Określ wiele parametrów typu przy użyciu odpowiedniej liczby przecinkami. W tym przykładzie `GenericClass2` zawiera dwa parametry typu:  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 Atrybut może odwoływać się zamkniętego skonstruowanego typu ogólnego:  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 Atrybut, który odwołuje się do parametru typu ogólnego spowoduje błąd w czasie kompilacji:  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 Nie może dziedziczyć po typie ogólnym <xref:System.Attribute>:  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 Aby uzyskać informacje o typie ogólnym lub parametru typu w czasie wykonywania, można użyć metody <xref:System.Reflection>. Aby uzyskać więcej informacji, zobacz [typy ogólne i odbicie](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy ogólne](../../../csharp/programming-guide/generics/index.md)  
 [Atrybuty](../../../../docs/standard/attributes/index.md)
