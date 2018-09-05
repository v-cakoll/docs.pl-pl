---
title: 'Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: e3cc3f9082bd86004a7821b64c01253408c07641
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43535743"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)
W tym przykładzie pokazano, jak utworzyć obiekty delegowane multiemisji. Przydatne właściwość [delegować](../../../csharp/language-reference/keywords/delegate.md) obiektów jest, że wiele obiektów można przypisać do wystąpienia jednego delegata za pomocą `+` operatora. Delegat multiemisji zawiera listę przypisanych delegatów. Po wywołaniu delegata multiemisji wywołuje delegatów na liście w kolejności. Można łączyć tylko obiektów delegowanych z tego samego typu.  
  
 `-` Operator może służyć do usuwania delegata składnika delegatów multiemisji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.MulticastDelegate>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
