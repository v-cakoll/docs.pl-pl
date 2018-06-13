---
title: 'Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: e1214a4d281dbcb9d8186770b68510d3d9a4b15f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327398"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)
W tym przykładzie pokazano, jak utworzyć obiekty delegowane multiemisji. Właściwość przydatne [delegować](../../../csharp/language-reference/keywords/delegate.md) obiektów jest, że wiele obiektów można przypisać do wystąpienia jednego delegata za pomocą `+` operatora. Delegat multiemisji znajduje się lista przydzielonych obiektów delegowanych. Po wywołaniu multiemisji delegata wywołuje delegatów na liście w kolejności. Można połączyć tylko delegatów tego samego typu.  
  
 `-` Operator może służyć do usunięcia delegata składnika z multiemisji delegata.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.MulticastDelegate>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)
