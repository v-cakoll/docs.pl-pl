---
title: 'Porady: użycie słownika do przechowywania wystąpień zdarzeń (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: 97a7b0f168e4a1c81ec396f42b731dabb45b3516
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Porady: użycie słownika do przechowywania wystąpień zdarzeń (Przewodnik programowania w języku C#)
Użycie jednego `accessor-declarations` jest do udostępnienia wiele zdarzeń bez przydzielania pola dla każdego zdarzenia, ale zamiast tego za pomocą słownika do przechowywania wystąpień zdarzeń. Jest to przydatne tylko wtedy, jeśli masz wiele zdarzeń, ale oczekuje się, że większość zdarzeń nie będzie zaimplementowana.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
 [Delegaci](../../../csharp/programming-guide/delegates/index.md)
