---
title: Zabezpieczenia
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: f47b75fa1fd345869f560326861ebc31e6b5e1a9
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045310"
---
# <a name="security"></a>Zabezpieczenia
Magazyn wystąpień przepływu pracy SQL używa następujących ról zabezpieczeń bazy danych w celu zabezpieczenia dostępu do informacji o stanie wystąpienia w bazie danych trwałości.  
  
- **System. Activities. DurableInstancing. InstanceStoreUsers**. Ta rola ma dostęp do odczytu i zapisu do widoków publicznych i praw wykonywania w procedurach składowanych, które są wykorzystywane do tworzenia, ładowania i zapisywania wystąpień.  
  
- **System. Activities. DurableInstancing. InstanceStoreObservers**. Ta rola ma dostęp tylko do odczytu do widoków publicznych.  
  
- **System.Activities.DurableInstancing.WorkflowActivationUsers**. Ta rola ma prawa wykonywania do procedur składowanych, które są uwzględnione w procesie aktywacji wystąpienia. Aby uzyskać więcej informacji na temat aktywacji wystąpienia, zobacz [Aktywacja wystąpienia](instance-activation.md). Konto użytkownika, na którym są uruchamiane hosty ogólne (takie jak usługa zarządzania przepływami pracy z funkcjami hostingu systemu Windows Server AppFabric), należy dodać do tej roli bazy danych.  
  
 Aby uzyskać więcej informacji o zabezpieczeniach magazynów trwałości przy użyciu sieci szkieletowej aplikacji systemu Windows Server, zobacz [Konfiguracja zabezpieczeń dla magazynów trwałości w usłudze App Fabric](https://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
> Klient, który ma dostęp do swoich własnych danych wystąpienia w magazynie wystąpień, ma dostęp do wszystkich innych wystąpień w tym samym magazynie wystąpień. Magazyn wystąpień nie obsługuje określania uprawnień zabezpieczeń na poziomie wystąpienia. Należy utworzyć oddzielne magazyny wystąpień i zmapować różne grupy/użytkowników, aby mieli dostęp do różnych magazynów.
