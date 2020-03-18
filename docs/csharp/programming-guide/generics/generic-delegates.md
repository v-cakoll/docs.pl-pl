---
title: Delegaci ogólny — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 4e57256328fc81a485670b47fcf8fd1c38e26fac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712224"
---
# <a name="generic-delegates-c-programming-guide"></a>Delegaty ogólne (Przewodnik programowania w języku C#)
[Pełnomocnik](../../language-reference/builtin-types/reference-types.md) może zdefiniować własne parametry typu. Kod, który odwołuje się do delegata ogólnego można określić argument typu, aby utworzyć zamknięty typ konstruowany, podobnie jak podczas tworzenia wystąpienia klasy ogólnej lub wywoływania metody ogólnej, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 C# w wersji 2.0 ma nową funkcję o nazwie konwersja grupy metod, która ma zastosowanie do konkretnych, jak i ogólnych typów delegatów i umożliwia zapisanie poprzedniego wiersza z tej uproszczonej składni:  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 Delegaci zdefiniowane w klasie ogólnej można użyć parametrów typu klasy ogólnej w taki sam sposób, jak metody klasy zrobić.  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 Kod, który odwołuje się do delegata musi określać argument typu zawierającej klasę, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 Delegaci rodzajowy są szczególnie przydatne w definiowaniu zdarzeń na podstawie typowego wzorca projektu, ponieważ argument nadawcy może być silnie wpisany i nie musi być już rzutowane do iz <xref:System.Object>.  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- [Przewodnik programowania języka C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [Metody ogólne](./generic-methods.md)
- [Klasy ogólne](./generic-classes.md)
- [Interfejsy ogólne](./generic-interfaces.md)
- [Delegaty](../delegates/index.md)
- [Typy ogólne](../../../standard/generics/index.md)
