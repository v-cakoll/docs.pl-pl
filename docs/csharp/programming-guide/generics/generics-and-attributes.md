---
title: Rodzajowe i atrybuty — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 47bf4e8f07a8b6778db8fa675d745d362dc10d7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703029"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Typy ogólne i atrybuty (Przewodnik programowania w języku C#)
Atrybuty mogą być stosowane do typów ogólnych w taki sam sposób jak typy nierodzajowe. Aby uzyskać więcej informacji na temat stosowania atrybutów, zobacz [Atrybuty](../concepts/attributes/index.md).  
  
 Atrybuty niestandardowe są dozwolone tylko do odwoływania się do otwartych typów ogólnych, które są typami ogólnymi, dla których nie są dostarczane żadne argumenty typu, i zamknięte skonstruowane typy ogólne, które dostarczają argumenty dla wszystkich parametrów typu.  
  
 W poniższych przykładach używa się tego atrybutu niestandardowego:  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 Atrybut może odwoływać się do otwartego typu ogólnego:  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 Określ wiele parametrów typu przy użyciu odpowiedniej liczby przecinków. W tym `GenericClass2` przykładzie ma dwa parametry typu:  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 Atrybut może odwoływać się do zamkniętego skonstruowanego typu ogólnego:  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 Atrybut, który odwołuje się do parametru typu ogólnego spowoduje błąd w czasie kompilacji:  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 Typ ogólny nie <xref:System.Attribute>może dziedziczyć z :  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 Aby uzyskać informacje o typie ogólnym lub parametrze typu w <xref:System.Reflection>czasie wykonywania, można użyć metod . Aby uzyskać więcej informacji, zobacz [Generyki i Refleksje](./generics-and-reflection.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Typy ogólne](./index.md)
- [Atrybuty](../../../standard/attributes/index.md)
