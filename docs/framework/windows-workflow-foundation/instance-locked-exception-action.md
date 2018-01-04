---
title: "Wystąpienie zablokowane wyjątku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 164a5419-315c-4987-ad72-54cbdb88d402
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b221b0eef1e132789ef04fb59b56126f023bc43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="instance-locked-exception-action"></a>Wystąpienie zablokowane wyjątku
<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> Właściwość w magazynie wystąpień przepływu pracy SQL pozwala określić akcję dostawca trwałości SQL powinien wykonać, gdy odbierze <xref:System.Runtime.DurableInstancing.InstanceLockedException>. Dostawca trwałości odbiera ten wyjątek podczas próby blokady wystąpienia usługi przepływu pracy, który jest zablokowany przez innego hosta usługi. Wartości dla tej właściwości to <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>, <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>, i <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>. Wartość domyślna to <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>. Na poniższej liście opisano trzy opcje:  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>., Host usługi nie jest podejmowana próba blokady wystąpienia usługi przepływu pracy i przekazuje <xref:System.Runtime.DurableInstancing.InstanceLockedException> do obiektu wywołującego.  Jeśli przepływ pracy pozostaje w pamięci na okres przekraczający 60 sekund, użyj <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> jako ponów próbę. Wartość domyślna to <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>.  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>., Host usługi reattempts do zablokowania wystąpienia usługi przepływu pracy o liniowej interwał ponawiania prób i przekazuje <xref:System.Runtime.DurableInstancing.InstanceLockedException> do wywołującego na końcu sekwencji. Jeśli przepływ pracy zostanie pozostaje w pamięci około od 5 do 60 sekund i nadchodzą komunikaty w partiach gdzie jest bardziej prawdopodobne dla komunikatów są wysyłane do tego samego wystąpienia na tym samym hoście, aby przetworzyć wszystkie komunikaty przed zwolnieniem przepływu pracy, użyj <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> do osiągnąć najlepsze opóźnienia bez marnować zasobów.  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>., Host usługi reattempts do zablokowania wystąpienia usługi przepływu pracy wykładniczego wycofywania interwał między ponownymi próbami i przekazuje wyjątek do wywołującego na końcu sekwencji. Jeśli przepływ pracy pozostaje w pamięci na bardzo krótkim czasie (mniej niż 5 sekund) lub sieci Web farmy jest duży i nie jest bardzo duże ryzyko kolejną wiadomość dostarczona do tego samego hosta, należy użyć <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> do osiągnięcia najlepsze opóźnienia.  
  
 Funkcja akcji wyjątek zablokowane wystąpienie obsługuje następujące scenariusze. We wszystkich scenariuszach, jeśli ustawiono właściwość instanceLockedExceptionAction obiekt SqlWorkflowInstanceStore <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> lub <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>, host niewidocznie ponawia próbę uzyskania blokady wystąpienia okresowo.  
  
1.  **Włączanie bezpiecznego zamknięcia i nachodzące odtwarzania domen aplikacji.** Załóżmy, że **elementu AppDomain** z hostem usługi uruchamiania przepływu pracy wystąpień usługi jest w trakcie odtwarzania i nowy **elementu AppDomain** jest włączane do obsługi nowych żądań równolegle równocześnie z  **Elementu AppDomain** obniżył jest bezpieczne. Zamknięcie czeka, aż wystąpienie usługi przepływu pracy są w stanie bezczynności, a następnie będzie się powtarzać i zwalnia wystąpienia. Wszystkie próby dostępu hosty w nowym **elementu AppDomain** do zablokowania wystąpienia spowoduje, że <xref:System.Runtime.DurableInstancing.InstanceLockedException>.  
  
2.  **Poziomo skalowanie trwałe przepływy pracy jednorodnych farmie serwerów.** Załóżmy, że węzeł farmy serwerów, na którym działa wystąpienie przepływu pracy awarii (Crash) i hosta przepływu pracy nie można usunąć blokady wystąpienia, który jest uruchomiony. Gdy hosta usługi uruchomione w innym węźle farmy odbiera komunikat dla tego wystąpienia przepływu pracy, próbuje uzyskać blokad w tych wystąpieniach odbieranie <xref:System.Runtime.DurableInstancing.InstanceLockedException>. Blokad wygaśnie po pewnym czasie, ponieważ hosta, który miał odnawiania blokady już istnieje.  
  
     **Poziomo skalowanie trwałe przepływy pracy jednorodnych farmie serwerów.**  Załóżmy, że ma być skalowana w poziomie trwałe przepływu pracy przy użyciu wielu hostach za równoważenia obciążenia Sieciowego (Usługa równoważenia obciążenia sieciowego), hosta przepływów pracy uruchomionych na jednym węźle farmy ładuje wystąpienia przepływu pracy i przetwarza komunikat i następny komunikat do wystąpienia jest kierowany do hosta, który jest uruchomiona w innym węźle, ponieważ Równoważenie obciążenia Sieciowego nie ma algorytmu routingu na dostarczenie wiadomości do hosta, który jest już uruchomione wystąpienie. Po otrzymaniu komunikatu, drugi host próbuje załadować wystąpienia przepływu pracy i odbiera <xref:System.Runtime.DurableInstancing.InstanceLockedException> ponieważ pierwszego hosta jest zablokowany w wystąpieniu. Po zakończeniu przy użyciu przetwarzania do pierwszej wiadomości i drugim hoście uzyskuje blokadę ponawia próbę po następnym, ładuje wystąpienie, a drugi komunikat przetwarza pierwszego hosta umożliwia odblokowanie wystąpienie.
