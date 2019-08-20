---
title: Delegaty ogólne C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 46ceca257777455824b6900f3e49999536d6bcad
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589738"
---
# <a name="generic-delegates-c-programming-guide"></a>Delegaty ogólne (Przewodnik programowania w języku C#)
[Delegat](../../language-reference/keywords/delegate.md) może definiować własne parametry typu. Kod, który odwołuje się do delegata generycznego, może określić argument typu, aby utworzyć zamknięty typ skonstruowany, podobnie jak podczas tworzenia wystąpienia klasy generycznej lub wywołania metody ogólnej, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 C#Wersja 2,0 ma nową funkcję, nazywana konwersją grupy metod, która ma zastosowanie do betonu i rodzajowych typów delegatów oraz pozwala napisać poprzedni wiersz z tą uproszczoną składnią:  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 Delegaty zdefiniowane w klasie generycznej mogą używać parametrów typu klasy generycznej w taki sam sposób, jak metody klasy.  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 Kod odwołujący się do delegata musi określać argument typu klasy zawierającej w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 Delegaty ogólne są szczególnie przydatne w definiowaniu zdarzeń na podstawie typowego wzorca projektowego, ponieważ argument nadawcy może być silnie określony i nie musi być już <xref:System.Object>rzutowany do i z.  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../index.md)
- [Wprowadzenie do typów ogólnych](./index.md)
- [Metody ogólne](./generic-methods.md)
- [Klasy ogólne](./generic-classes.md)
- [Interfejsy ogólne](./generic-interfaces.md)
- [Delegaty](../delegates/index.md)
- [Typy ogólne](~/docs/standard/generics/index.md)
