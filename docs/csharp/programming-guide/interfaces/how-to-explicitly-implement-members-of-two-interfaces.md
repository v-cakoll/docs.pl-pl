---
title: Jak jawnie implementować członków dwóch interfejsów - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c7adc08f62a7f8a14b8e10f8b5ecdd6e37db811d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75701241"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Jak jawnie implementować członków dwóch interfejsów (C# Programming Guide)
Implementacja [interfejsu](../../language-reference/keywords/interface.md) jawnego umożliwia również programisty zaimplementować dwa interfejsy, które mają te same nazwy elementów członkowskich i nadać każdemu członkowi interfejsu oddzielną implementację. W tym przykładzie są wyświetlane wymiary pola zarówno w jednostkach metrycznych, jak i angielskich. [Klasa](../../language-reference/keywords/class.md) Box implementuje dwa interfejsy IEnglishDimensions i IMetricDimensions, które reprezentują różne systemy pomiarowe. Oba interfejsy mają identyczne nazwy elementów członkowskich, Długość i Szerokość.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli chcesz wprowadzić domyślne pomiary w jednostkach angielskich, należy zaimplementować metody Długość i szerokość normalnie i jawnie zaimplementować length and width metody z iMetricDimensions interfejsu:  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 W takim przypadku można uzyskać dostęp do jednostek angielskich z wystąpienia klasy i uzyskać dostęp do jednostek metryk z wystąpienia interfejsu:  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](../classes-and-structs/index.md)
- [Interfejsy](./index.md)
- [Jawne implementowanie elementów interfejsu](./how-to-explicitly-implement-interface-members.md)
