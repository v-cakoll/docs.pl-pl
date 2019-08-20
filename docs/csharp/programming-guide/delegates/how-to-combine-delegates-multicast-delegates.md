---
title: 'Instrukcje: Łączenie delegatów (delegatów multiemisji C# ) — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d9430021e6a9b438822f1a6dc201f64adf4fdb0f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590663"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Instrukcje: Łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)
W tym przykładzie pokazano, jak utworzyć delegatów multiemisji. Przydatna właściwość obiektów [delegatów](../../language-reference/keywords/delegate.md) polega na tym, że wiele obiektów może być przypisanych do jednego wystąpienia delegata przy użyciu `+` operatora. Delegat multiemisji zawiera listę przypisanych delegatów. Gdy obiekt delegowany multiemisji jest wywoływany, wywołuje delegatów z listy w kolejności. Łączyć można tylko Delegaty tego samego typu.  
  
 `-` Operatora można użyć do usunięcia delegata składnika z delegata multiemisji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.MulticastDelegate>
- [Przewodnik programowania w języku C#](../index.md)
- [Zdarzenia](../events/index.md)
