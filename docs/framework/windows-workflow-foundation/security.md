---
title: Zabezpieczenia
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: c27ac9cf41436332d560e11987e3ce4b68576895
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004695"
---
# <a name="security"></a>Zabezpieczenia
Zabezpieczenie dostępu do informacji o stanie wystąpienie w bazie danych trwałości Store wystąpienia przepływu pracy SQL są używane następujące role zabezpieczeń bazy danych.  
  
- **System.Activities.DurableInstancing.InstanceStoreUsers**. Ta rola ma odczytu i widoki publiczne do zapisu i wykonania prawa do procedury składowane, które są zaangażowane w tworzenie, ładowania i zapisywania wystąpień.  
  
- **System.Activities.DurableInstancing.InstanceStoreObservers**. Ta rola ma dostęp tylko do odczytu do widoków publicznych.  
  
- **System.Activities.DurableInstancing.WorkflowActivationUsers**. Ta rola ma uprawnienia wykonywania procedur przechowywanych, które są zaangażowane w proces aktywacji wystąpienia. Aby uzyskać więcej informacji na temat Aktywacja wystąpienia zobacz [Aktywacja wystąpienia](instance-activation.md). Konto użytkownika, pod którym ogólnego hosta (takich jak przepływ pracy usługi zarządzania [!INCLUDE[dublin](../../../includes/dublin-md.md)]) uruchamia powinny zostać dodane do tej roli bazy danych.  
  
 Aby uzyskać więcej informacji na temat zabezpieczeń dla trwałości magazynów z systemem Windows Server AppFabric zobacz [konfiguracji zabezpieczeń dla sklepów trwałości w aplikacji w sieci szkieletowej](https://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Klient, który ma dostęp do danych wystąpienia w sklepie wystąpienia ma dostęp do wszystkich innych wystąpień w tym samym magazynie wystąpienia. Magazyn wystąpień nie obsługuje określania uprawnień zabezpieczeń na poziomie wystąpienia. Należy utworzyć osobne wystąpienie magazynów i mapowania różnych użytkowników/grup mogą mieć dostęp do różnych sklepach.
