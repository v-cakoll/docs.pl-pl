---
title: 'Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji)- C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: ebfcba4d2ebebe2697aa01b7109bbf50b8f144e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631558"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji) (C# Programming Guide)
W tym przykładzie pokazano, jak utworzyć obiekty delegowane multiemisji. Przydatne właściwość [delegować](../../../csharp/language-reference/keywords/delegate.md) obiektów jest, że wiele obiektów można przypisać do wystąpienia jednego delegata za pomocą `+` operatora. Delegat multiemisji zawiera listę przypisanych delegatów. Po wywołaniu delegata multiemisji wywołuje delegatów na liście w kolejności. Można łączyć tylko obiektów delegowanych z tego samego typu.  
  
 `-` Operator może służyć do usuwania delegata składnika delegatów multiemisji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.MulticastDelegate>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
