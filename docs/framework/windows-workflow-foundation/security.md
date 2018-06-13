---
title: Zabezpieczenia
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: b8fd870bcd14b8a80861914448f75fafe6af2863
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518020"
---
# <a name="security"></a>Zabezpieczenia
W magazynie wystąpień przepływu pracy SQL są używane następujące role zabezpieczeń bazy danych do bezpieczny dostęp do informacji o stanie wystąpienie w bazie danych trwałości.  
  
-   **System.Activities.DurableInstancing.InstanceStoreUsers**. Ta rola zapoznał się oraz publicznie do zapisu i wykonywania prawa do przechowywane procedur, które nie są związane z tworzeniem, ładowania i zapisywania wystąpień.  
  
-   **System.Activities.DurableInstancing.InstanceStoreObservers**. Ta rola ma dostęp tylko do odczytu do widoków publicznych.  
  
-   **System.Activities.DurableInstancing.WorkflowActivationUsers**. Ta rola ma prawa wykonywania na procedury składowane, które są zaangażowane w procesie aktywacji wystąpienia. Aby uzyskać więcej informacji o wystąpieniu aktywacji, zobacz [aktywacji wystąpienia](../../../docs/framework/windows-workflow-foundation/instance-activation.md). Konto użytkownika, którego rodzajowego hosta (takich jak przepływ pracy usługi zarządzania [!INCLUDE[dublin](../../../includes/dublin-md.md)]) uruchamia powinni zostać dodani do tej roli bazy danych.  
  
 Aby uzyskać więcej informacji o zabezpieczeniach dla magazynów trwałości z systemu Windows Server AppFabric, zobacz [konfiguracji zabezpieczeń dla magazynów trwałości w aplikacji sieci szkieletowej](http://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Klient, który ma dostęp do danych wystąpienia w magazynie wystąpień ma dostęp do wszystkich innych wystąpień w tym samym magazynie wystąpień. W magazynie wystąpień nie obsługuje określania uprawnień zabezpieczeń na poziomie wystąpienia. Należy utworzyć osobne wystąpienie magazynów i mapowania różnych grup/Użytkownicy mają mieć dostęp do różnych magazynów.
