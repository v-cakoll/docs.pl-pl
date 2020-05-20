---
title: 'Instrukcje: Włączanie stanów trwałych dla przepływów pracy i usług przepływu pracy'
description: Dowiedz się, jak skonfigurować magazyn wystąpień przepływu pracy SQL, aby zapewnić trwałość dla przepływów pracy i usług przepływu pracy programowo oraz przy użyciu pliku konfiguracji.
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 31fe6e3f06989e9a42254747565342cf97e4b9f1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421517"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Instrukcje: Włączanie stanów trwałych dla przepływów pracy i usług przepływu pracy

W tym temacie opisano sposób włączania trwałości dla przepływów pracy i usług przepływu pracy.

## <a name="enable-persistence-for-workflows"></a>Włącz trwałość dla przepływów pracy

Można skojarzyć magazyn wystąpień z obiektem **WorkflowApplication** przy użyciu <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwości <xref:System.Activities.WorkflowApplication> klasy. <xref:System.Activities.WorkflowApplication.Persist%2A>Metoda zapisuje lub utrzymuje przepływ pracy w magazynie wystąpień skojarzonym z aplikacją. <xref:System.Activities.WorkflowApplication.Unload%2A>Metoda utrzymuje przepływ pracy w magazynie wystąpień, a następnie zwalnia wystąpienie z pamięci. Metoda **Load** ładuje przepływ pracy do pamięci przy użyciu danych przepływu pracy przechowywanych w magazynie trwałości wystąpienia.

Metoda **utrwalania** wykonuje następujące czynności:

1. Wstrzymuje harmonogram przepływu pracy i czeka, aż przepływ pracy przejdzie do stanu bezczynności.

2. Zachowuje lub zapisuje przepływ pracy w magazynie trwałości.

3. Wznawia harmonogram przepływu pracy.

 Metoda **Unload** wykonuje następujące czynności:

1. Wstrzymuje harmonogram przepływu pracy i czeka, aż przepływ pracy przejdzie do stanu bezczynności.

2. Zachowuje lub zapisuje przepływ pracy w magazynie trwałości.

3. Usuwa wystąpienie przepływu pracy w pamięci.

Metody **utrwalania** i **zwalniania** będą blokowane, gdy przepływ pracy jest w strefie no-utrwalania, dopóki przepływ pracy nie spowoduje zakończenia strefy braku trwałej. Metoda kontynuuje działanie z operacją utrwalania lub zwalniania po zakończeniu strefy No-utrwalania. Jeśli strefa braku utrwalania nie zostanie zakończona przed upływem limitu czasu lub jeśli proces trwałości trwa zbyt długo, zostanie zgłoszony limit czasu.

## <a name="enable-persistence-for-workflow-services-in-code"></a>Włącz trwałość dla usług przepływu pracy w kodzie

Element członkowski **DurableInstancingOptions** <xref:System.ServiceModel.WorkflowServiceHost> klasy ma właściwość o nazwie **InstanceStore** , której można użyć do skojarzenia magazynu wystąpień z obiektem **WorkflowServiceHost**.

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

Gdy obiekt **WorkflowServiceHost** jest otwarty, trwałość jest włączana automatycznie, jeśli **DurableInstancingOptions. InstanceStore** nie ma wartości null.

Zwykle zachowanie usługi zapewnia konkretny magazyn wystąpień do użycia z hostem usługi przepływu pracy przy użyciu właściwości **InstanceStore** . Na przykład SqlWorkflowInstanceStoreBehavior tworzy wystąpienie **obiekt SqlWorkflowInstanceStore**, konfiguruje je i przypisuje go do **DurableInstancingOptions. InstanceStore**.

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Włącz trwałość dla usług przepływu pracy przy użyciu pliku konfiguracji aplikacji

Trwałości można włączyć za pomocą pliku konfiguracji aplikacji, dodając następujący kod do pliku App. config lub Web. config:

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <sqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```
