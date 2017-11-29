---
title: "Wystąpienie magazynów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c78e5ff1310951defdfaa38a9b63aacb9c27872b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="instance-stores"></a>Wystąpienie magazynów
Magazyn wystąpienia jest kontenerem logicznym wystąpień. Jest to miejsce, gdzie są przechowywane dane wystąpienia i metadanych. Magazyn wystąpienia nie oznacza dedykowanych dla magazynu fizycznego. Magazyn wystąpienia mogą zawierać informacje o stanie nietrwałe w pamięci lub trwałe informacji z bazy danych programu SQL Server. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Jest dostarczany z magazynu wystąpienia SQL przepływu pracy, czyli konkretną implementację magazynu wystąpienia, który umożliwia przepływy pracy, aby zachować dane wystąpienia i metadane do bazy danych programu SQL Server 2005 lub SQL Server 2008. Ponadto AppFabric w systemie Windows Server udostępnia konkretną implementację magazynu wystąpienia. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Sklepu wystąpienia sieci szkieletowej dla systemu Windows Server, zapytań i dostawców kontroli](http://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409).  
  
 Trwałość interfejsu API jest interfejs między hostem i wystąpienie magazynu, umożliwiająca hosta do wysyłania żądań polecenia (na przykład <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> i <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) w magazynie wystąpień. Konkretną implementację tego interfejsu API nosi nazwę dostawcy trwałości. Dostawca trwałości odbiera żądania od hosta i modyfikuje w magazynie wystąpień.  
  
 Hosty i magazyny wystąpienia są podłączane, dzięki czemu hosta może być używany z wielu sklepach wystąpienia i wystąpienie magazynu mogą być używane z wielu hostach. Magazyn wystąpienia zwykle jest zoptymalizowana pod kątem wzorców użycia określonego hosta, mimo że SIS i hosta może się rozwijać na niezależne cyklu. Na przykład **obiektu WorkflowServiceHost** i **SqlWorkflowInstanceStore** zostały zaprojektowane do siebie. Można utworzyć własne wystąpienie magazynu do utrwalenia danych lub metadanych wystąpień usługi przepływu pracy i używanie tego wystąpienia magazynu z **obiektu WorkflowServiceHost**. Na przykład można utworzyć OracleWorkflowInstanceStore umożliwiający przepływy pracy utrwalenia informacji w bazie danych programu Oracle zamiast zapisywania ich w bazie danych programu SQL Server.  
  
 Są często hostom rozszerzony o dodatkowe funkcje, które modyfikuje utrwalonych obiektów. Na przykład system utrwalania wystąpień może mieć hosta przepływu pracy, rozszerzenie, które obsługuje operację "Zawieszania" i magazynu wystąpienia SQL.  Hosta przepływu pracy może wysyłać standardowego polecenia takie jak zapisać lub obciążenia, aby zapisać lub załadować przepływu pracy z magazynu wystąpień lub do zapisywania w magazynie wystąpień przepływu pracy. Rozszerzenia zawieszenia może dodać dodatkowej semantyki do polecenia zapisywanie i ładowanie wystąpienia przepływu pracy, aby nie można załadować wystąpienia Wstrzymany przepływ pracy. Dostawca trwałości w magazynie wystąpień programu SQL rozumie polecenia zapisywanie i ładowanie wystąpienia przepływu pracy i implementuje poleceń, wywołując odpowiednie przechowywane procedury, które zmieniania tabel trwałych obiektów w bazie danych programu SQL Server.  
  
 Host pełni rolę właściciela wystąpienia w magazynie wystąpień. Host mogą działać jako więcej niż jednego właściciela wystąpienia z więcej niż jeden magazyn wystąpienia w tym samym czasie. Host zawiera identyfikatory GUID, na przykład kluczy skojarzonych z wystąpieniami. Klucz wystąpienia jest unikatowego aliasu, który identyfikuje wystąpienia. System utrwalania tworzy, aktualizowanie i usuwanie informacji właściciela wystąpienia, podczas wykonywania polecenia wymaganych przez hosty.  
  
 Poniższa lista zawiera ważne etapy hosta interakcji ze sklepem wystąpienie:  
  
1.  Uzyskaj **InstanceStore** od dostawcy trwałości.  

2.  Uzyskać dojścia do wystąpienia przez wywołanie metody <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> metoda **InstanceStore**.  
  
3.  Wywołanie polecenia przed dojście wystąpienia przez wywołanie metody <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> metoda **InstanceStore**.  
  
4.  Sprawdź <xref:System.Runtime.DurableInstancing.InstanceView> zwrócony przez **wywoływania metody InstanceStore.Execute** do określenia wyników polecenia.
