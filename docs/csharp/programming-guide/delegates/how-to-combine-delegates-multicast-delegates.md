---
title: Jak łączyć delegatów (delegatów multiemisji) C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705382"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a>Łączenie obiektów delegowanych (obiekty delegowane multiemisji) (Przewodnik programowania w języku C#)
W tym przykładzie pokazano, jak utworzyć delegatów multiemisji. Przydatna właściwość obiektów [delegatów](../../language-reference/builtin-types/reference-types.md) polega na tym, że wiele obiektów może być przypisanych do jednego wystąpienia delegata przy użyciu operatora `+`. Delegat multiemisji zawiera listę przypisanych delegatów. Gdy obiekt delegowany multiemisji jest wywoływany, wywołuje delegatów z listy w kolejności. Łączyć można tylko Delegaty tego samego typu.  
  
 Operatora `-` można użyć do usunięcia delegata składnika z delegata multiemisji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.MulticastDelegate>
- [Przewodnik programowania w języku C#](../index.md)
- [Zdarzenia](../events/index.md)
