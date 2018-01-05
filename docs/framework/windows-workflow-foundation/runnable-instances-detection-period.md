---
title: "Okres wykrywania wystąpień możliwych do uruchomienia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 561ef96b6f043956822a1290d4a03a2e7411f6f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="runnable-instances-detection-period"></a>Okres wykrywania wystąpień możliwych do uruchomienia
W magazynie wystąpień przepływu pracy SQL działa wewnętrzny zadanie, które okresowo budzi i wykrywa do uruchomienia lub aktywowalnej wystąpienia w bazie danych trwałości. **Okres wykrywania wystąpień możliwych do uruchomienia** właściwość w magazynie wystąpień przepływu pracy SQL określa okres czasu, po którym w magazynie wystąpień przepływu pracy SQL uruchamia zadanie wykrywania do wykrywania wszelkich do uruchomienia lub aktywowalnej przepływu pracy wystąpienia w bazie danych trwałości od poprzedniego cyklu wykrywania.  
  
 Ustawienie krótszy interwał dla tej właściwości skraca czas między wygaśnięcia czasomierz skojarzony z wystąpieniem przepływu pracy i sygnalizowania zdarzenia oraz kolejnych ładowanie wystąpienia. Jednak również zwiększa obciążenie przetwarzania na hoście i nie może być wskazane w scenariuszach, w których występują rzadko trwałe czasomierze i/lub awarii hosta. Typ właściwości jest TimeSpan i wartość właściwości zgodne z formatem: hh: mm:. Minimalna wartość dla tej właściwości to 00:00:01. Wartość domyślna właściwości to 00:00:05.  
  
 Aby uzyskać więcej informacji zobacz wykrywanie i aktywowanie wystąpienia przepływu pracy do uruchomienia i aktywowalnej [aktywacji wystąpienia](../../../docs/framework/windows-workflow-foundation/instance-activation.md).
