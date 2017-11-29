---
title: "Porady: użycie słownika do przechowywania wystąpień zdarzeń (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0304f04233151d35c8ee18fe09feac91fbd0879b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Porady: użycie słownika do przechowywania wystąpień zdarzeń (Przewodnik programowania w języku C#)
Użycie jednego `accessor-declarations` jest do udostępnienia wiele zdarzeń bez przydzielania pola dla każdego zdarzenia, ale zamiast tego za pomocą słownika do przechowywania wystąpień zdarzeń. Jest to przydatne tylko wtedy, jeśli masz wiele zdarzeń, ale oczekuje się, że większość zdarzeń nie będzie zaimplementowana.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
 [Obiekty delegowane](../../../csharp/programming-guide/delegates/index.md)
