---
title: 'Porady: jawne implementowanie elementów dwóch interfejsów (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c73089fdbf1350c1aff68ac3e8e78be00e21b931
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Porady: jawne implementowanie elementów dwóch interfejsów (Przewodnik programowania w języku C#)
Jawne [interfejsu](../../../csharp/language-reference/keywords/interface.md) implementacji umożliwia również programisty do zaimplementowania dwa interfejsy tej samej nazwy elementów członkowskich, które zapewniają każdy element członkowski interfejsu oddzielne implementacji. W tym przykładzie wyświetla rozmiary pola w metryki i jednostki w języku angielskim. Pole [klasy](../../../csharp/language-reference/keywords/class.md) implementuje dwa interfejsy IEnglishDimensions i IMetricDimensions, reprezentujące różne systemy miary. Oba interfejsy mają nazwy identyczne elementu członkowskiego, długość i szerokość.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli mają być pomiarów domyślne w angielskiej wersji językowej jednostki, zwykle implementuje metody długości i szerokości i jawnie implementować metody długości i szerokości przy użyciu interfejsu IMetricDimensions:  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 W takim przypadku angielskiej wersji językowej jednostki z wystąpienia klasy i dostępne uzyskiwać dostęp do jednostki metryki z wystąpienia interfejsu:  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)  
 [Instrukcje: jawne implementowanie elementów interfejsu](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
