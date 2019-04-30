---
title: 'Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji)- C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 426b9f91d3e3328522ec5c7ab043d5074ececc43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711023"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)
W tym przykładzie pokazano, jak utworzyć obiekty delegowane multiemisji. Przydatne właściwość [delegować](../../../csharp/language-reference/keywords/delegate.md) obiektów jest, że wiele obiektów można przypisać do wystąpienia jednego delegata za pomocą `+` operatora. Delegat multiemisji zawiera listę przypisanych delegatów. Po wywołaniu delegata multiemisji wywołuje delegatów na liście w kolejności. Można łączyć tylko obiektów delegowanych z tego samego typu.  
  
 `-` Operator może służyć do usuwania delegata składnika delegatów multiemisji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.MulticastDelegate>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
