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
# <a name="runnable-instances-detection-period"></a><span data-ttu-id="885c1-102">Okres wykrywania wystąpień możliwych do uruchomienia</span><span class="sxs-lookup"><span data-stu-id="885c1-102">Runnable Instances Detection Period</span></span>
<span data-ttu-id="885c1-103">W magazynie wystąpień przepływu pracy SQL działa wewnętrzny zadanie, które okresowo budzi i wykrywa do uruchomienia lub aktywowalnej wystąpienia w bazie danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="885c1-103">The SQL Workflow Instance Store runs an internal task that periodically wakes up and detects runnable or activatable instances in the persistence database.</span></span> <span data-ttu-id="885c1-104">**Okres wykrywania wystąpień możliwych do uruchomienia** właściwość w magazynie wystąpień przepływu pracy SQL określa okres czasu, po którym w magazynie wystąpień przepływu pracy SQL uruchamia zadanie wykrywania do wykrywania wszelkich do uruchomienia lub aktywowalnej przepływu pracy wystąpienia w bazie danych trwałości od poprzedniego cyklu wykrywania.</span><span class="sxs-lookup"><span data-stu-id="885c1-104">The **Runnable Instances Detection Period** property of the SQL Workflow Instance Store specifies the time period after which the SQL Workflow Instance Store runs a detection task to detect any runnable or activatable workflow instances in the persistence database after the previous detection cycle.</span></span>  
  
 <span data-ttu-id="885c1-105">Ustawienie krótszy interwał dla tej właściwości skraca czas między wygaśnięcia czasomierz skojarzony z wystąpieniem przepływu pracy i sygnalizowania zdarzenia oraz kolejnych ładowanie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="885c1-105">Setting a shorter interval for this property reduces the time between the expiration of a timer associated with a workflow instance and the signaling of the event and subsequent loading of the instance.</span></span> <span data-ttu-id="885c1-106">Jednak również zwiększa obciążenie przetwarzania na hoście i nie może być wskazane w scenariuszach, w których występują rzadko trwałe czasomierze i/lub awarii hosta.</span><span class="sxs-lookup"><span data-stu-id="885c1-106">However, it also increases the processing load on a host and may not be desirable in scenarios where durable timers and/or host failures are rare.</span></span> <span data-ttu-id="885c1-107">Typ właściwości jest TimeSpan i wartość właściwości zgodne z formatem: hh: mm:.</span><span class="sxs-lookup"><span data-stu-id="885c1-107">The type of the property is TimeSpan and the value of the property follows the format: hh:mm:ss.</span></span> <span data-ttu-id="885c1-108">Minimalna wartość dla tej właściwości to 00:00:01.</span><span class="sxs-lookup"><span data-stu-id="885c1-108">The minimum value for this property is 00:00:01.</span></span> <span data-ttu-id="885c1-109">Wartość domyślna właściwości to 00:00:05.</span><span class="sxs-lookup"><span data-stu-id="885c1-109">The default value for the property is 00:00:05.</span></span>  
  
 <span data-ttu-id="885c1-110">Aby uzyskać więcej informacji zobacz wykrywanie i aktywowanie wystąpienia przepływu pracy do uruchomienia i aktywowalnej [aktywacji wystąpienia](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="885c1-110">For more information detecting and activating runnable and activatable workflow instances, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span>
