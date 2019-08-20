---
title: 'Instrukcje: Jawne implementowanie elementów członkowskich dwóch interfejsów C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 1d4dd0485be1d859e3e9594ab1558a907b8f1f7a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589193"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Instrukcje: Jawne implementowanie elementów członkowskich dwóch interfejsówC# (Przewodnik programowania)
Implementacja [interfejsu](../../language-reference/keywords/interface.md) jawnego pozwala programistom zaimplementować dwa interfejsy, które mają te same nazwy elementów członkowskich i nadać każdemu elementowi członkowskiemu interfejsu oddzielną implementację. W tym przykładzie wyświetlane są wymiary pola zarówno w jednostkach metrycznych, jak i w języku angielskim. [Klasa](../../language-reference/keywords/class.md) Box implementuje dwa interfejsy IEnglishDimensions i IMetricDimensions, które reprezentują różne systemy pomiarowe. Oba interfejsy mają identyczne nazwy składowych, długość i szerokość.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli chcesz wprowadzić wartości domyślne w jednostkach w języku angielskim, zaimplementuj normalne wartości długości i szerokości, a następnie jawnie Zaimplementuj metody długości i szerokości z interfejsu IMetricDimensions:  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 W takim przypadku można uzyskać dostęp do jednostek w języku angielskim z wystąpienia klasy i uzyskać dostęp do jednostek metryk z wystąpienia interfejsu:  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](../classes-and-structs/index.md)
- [Interfejsy](./index.md)
- [Instrukcje: Jawnie Implementuj składowe interfejsu](./how-to-explicitly-implement-interface-members.md)
