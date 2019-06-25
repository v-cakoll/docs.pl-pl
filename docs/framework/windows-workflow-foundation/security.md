---
title: Zabezpieczenia
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: cbfb82c2db329725d3445e1a88b54e01d5813f36
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348407"
---
# <a name="security"></a>Zabezpieczenia
Zabezpieczenie dostępu do informacji o stanie wystąpienie w bazie danych trwałości Store wystąpienia przepływu pracy SQL są używane następujące role zabezpieczeń bazy danych.  
  
- **System.Activities.DurableInstancing.InstanceStoreUsers**. Ta rola ma odczytu i widoki publiczne do zapisu i wykonania prawa do procedury składowane, które są zaangażowane w tworzenie, ładowania i zapisywania wystąpień.  
  
- **System.Activities.DurableInstancing.InstanceStoreObservers**. Ta rola ma dostęp tylko do odczytu do widoków publicznych.  
  
- **System.Activities.DurableInstancing.WorkflowActivationUsers**. Ta rola ma uprawnienia wykonywania procedur przechowywanych, które są zaangażowane w proces aktywacji wystąpienia. Aby uzyskać więcej informacji na temat Aktywacja wystąpienia zobacz [Aktywacja wystąpienia](instance-activation.md). Konta użytkownika, na którym działa ogólnego hosta (np. usługi przepływu pracy zarządzania funkcje hostingu programu Windows Server AppFabric) należy dodać do tej roli bazy danych.  
  
 Aby uzyskać więcej informacji na temat zabezpieczeń dla trwałości magazynów z systemem Windows Server AppFabric zobacz [konfiguracji zabezpieczeń dla sklepów trwałości w aplikacji w sieci szkieletowej](https://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Klient, który ma dostęp do danych wystąpienia w sklepie wystąpienia ma dostęp do wszystkich innych wystąpień w tym samym magazynie wystąpienia. Magazyn wystąpień nie obsługuje określania uprawnień zabezpieczeń na poziomie wystąpienia. Należy utworzyć osobne wystąpienie magazynów i mapowania różnych użytkowników/grup mogą mieć dostęp do różnych sklepach.
