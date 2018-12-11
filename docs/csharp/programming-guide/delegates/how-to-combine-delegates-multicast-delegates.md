---
title: 'Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji)- C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d835f9b22fef550d6e73cbd620a283bd71e393ec
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237795"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji) (C# Programming Guide)
W tym przykładzie pokazano, jak utworzyć obiekty delegowane multiemisji. Przydatne właściwość [delegować](../../../csharp/language-reference/keywords/delegate.md) obiektów jest, że wiele obiektów można przypisać do wystąpienia jednego delegata za pomocą `+` operatora. Delegat multiemisji zawiera listę przypisanych delegatów. Po wywołaniu delegata multiemisji wywołuje delegatów na liście w kolejności. Można łączyć tylko obiektów delegowanych z tego samego typu.  
  
 `-` Operator może służyć do usuwania delegata składnika delegatów multiemisji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.MulticastDelegate>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
