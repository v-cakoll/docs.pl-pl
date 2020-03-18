---
title: Jak połączyć delegatów (delegatów multiemisji) - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705382"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a>Łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)
W tym przykładzie pokazano, jak utworzyć delegatów multiemisji. Przydatną właściwością obiektów [delegowanych](../../language-reference/builtin-types/reference-types.md) jest, że wiele obiektów można przypisać `+` do jednego wystąpienia delegata za pomocą operatora. Pełnomocnik multiemisji zawiera listę przydzielonych delegatów. Gdy delegat multiemisji jest wywoływana, wywołuje delegatów na liście, w kolejności. Można łączyć tylko delegatów tego samego typu.  
  
 Operator `-` może służyć do usuwania delegata składnika z delegata multiemisji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.MulticastDelegate>
- [Przewodnik programowania języka C#](../index.md)
- [Zdarzenia](../events/index.md)
