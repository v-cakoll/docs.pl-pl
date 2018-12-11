---
title: 'Instrukcje: Jawne Implementowanie elementów dwóch interfejsów - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: 3e03e80279db8c36cb975715f390ff6899d593cb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238328"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a>Instrukcje: Jawne Implementowanie elementów dwóch interfejsów (C# Programming Guide)
Jawne [interfejsu](../../../csharp/language-reference/keywords/interface.md) implementacji umożliwia także programisty należy zaimplementować dwa interfejsy, które mają te same nazwy składników i nadaj każdej składowej interfejsu oddzielne implementacji. Ten przykład wyświetla rozmiary pola w metryki i jednostek w języku angielskim. Pole [klasy](../../../csharp/language-reference/keywords/class.md) implementuje dwa interfejsy IEnglishDimensions i IMetricDimensions, którą reprezentują różne systemy miary. Oba interfejsy mają identyczne nazwy elementów członkowskich, długość i szerokość.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInheritance#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_1.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli chcesz wprowadzić odpowiednie wartości domyślne w języku angielskim jednostkach, zwykle implementują metody długości i szerokości i jawnie implementować metody długości i szerokości przy użyciu interfejsu IMetricDimensions:  
  
 [!code-csharp[csProgGuideInheritance#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_2.cs)]  
  
 W takim przypadku można uzyskiwać dostęp do jednostki angielskiego z wystąpienia klasy i uzyskać dostęp do metryk jednostki z wystąpienia interfejsu:  
  
 [!code-csharp[csProgGuideInheritance#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-members-of-two-interfaces_3.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)  
- [Instrukcje: Jawne Implementowanie elementów interfejsu](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)
