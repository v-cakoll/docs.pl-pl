---
title: Zabezpieczenia
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0063497bc500a11d59dd88e0cb7d738d5c4bb6e5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="security"></a>Zabezpieczenia
W magazynie wystąpień przepływu pracy SQL są używane następujące role zabezpieczeń bazy danych do bezpieczny dostęp do informacji o stanie wystąpienie w bazie danych trwałości.  
  
-   **System.Activities.DurableInstancing.InstanceStoreUsers**. Ta rola zapoznał się oraz publicznie do zapisu i wykonywania prawa do przechowywane procedur, które nie są związane z tworzeniem, ładowania i zapisywania wystąpień.  
  
-   **System.Activities.DurableInstancing.InstanceStoreObservers**. Ta rola ma dostęp tylko do odczytu do widoków publicznych.  
  
-   **System.Activities.DurableInstancing.WorkflowActivationUsers**. Ta rola ma prawa wykonywania na procedury składowane, które są zaangażowane w procesie aktywacji wystąpienia. Aby uzyskać więcej informacji o wystąpieniu aktywacji, zobacz [aktywacji wystąpienia](../../../docs/framework/windows-workflow-foundation/instance-activation.md). Konto użytkownika, którego rodzajowego hosta (takich jak przepływ pracy usługi zarządzania [!INCLUDE[dublin](../../../includes/dublin-md.md)]) uruchamia powinni zostać dodani do tej roli bazy danych.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]zabezpieczenia dla magazynów trwałości z systemu Windows Server AppFabric, zobacz [konfiguracji zabezpieczeń dla magazynów trwałości w aplikacji sieci szkieletowej](http://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Klient, który ma dostęp do danych wystąpienia w magazynie wystąpień ma dostęp do wszystkich innych wystąpień w tym samym magazynie wystąpień. W magazynie wystąpień nie obsługuje określania uprawnień zabezpieczeń na poziomie wystąpienia. Należy utworzyć osobne wystąpienie magazynów i mapowania różnych grup/Użytkownicy mają mieć dostęp do różnych magazynów.
