---
title: 'Porady: użycie słownika do przechowywania wystąpień zdarzeń (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: c3a804ce1bf1f5ac8db47f0f0c1f37d1ca5f781b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43673739"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Porady: użycie słownika do przechowywania wystąpień zdarzeń (Przewodnik programowania w języku C#)
Jednym z zastosowań `accessor-declarations` na przykład uwidocznić wiele zdarzeń, bez przydzielania pola dla każdego zdarzenia, ale zamiast tego przy użyciu słownika do przechowywania wystąpień zdarzeń. Jest to przydatne tylko wtedy, jeśli masz wiele zdarzeń, ale możesz spodziewać się, że większość zdarzeń nie będzie zaimplementowana.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
- [Delegaci](../../../csharp/programming-guide/delegates/index.md)
