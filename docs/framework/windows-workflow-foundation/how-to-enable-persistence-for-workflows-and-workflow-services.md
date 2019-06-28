---
title: 'Instrukcje: Włączanie stanów trwałych dla przepływów pracy i usług przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 9357098318342d15ad7eead32cbc7218af095f6e
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425339"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Instrukcje: Włączanie stanów trwałych dla przepływów pracy i usług przepływu pracy

W tym temacie opisano włączanie stanów trwałych dla przepływów pracy i usług przepływu pracy.

## <a name="enable-persistence-for-workflows"></a>Włączanie stanów trwałych dla przepływów pracy

Możesz skojarzyć magazyn wystąpienia z **WorkflowApplication** przy użyciu <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwość <xref:System.Activities.WorkflowApplication> klasy. <xref:System.Activities.WorkflowApplication.Persist%2A> Metody zapisuje lub będzie się powtarzał przepływu pracy do wystąpienia magazynu skojarzone z aplikacją. <xref:System.Activities.WorkflowApplication.Unload%2A> Metoda się powtarza przepływu pracy do magazynu wystąpienia, a następnie zwalnia wystąpienie z pamięci. **Obciążenia** metoda ładuje przepływu pracy do ilości pamięci za pomocą danych przepływu pracy, przechowywane w magazynie w trwałości wystąpienia.

**Utrwalanie** metoda wykonuje następujące czynności:

1. Wstrzymuje harmonogram przepływu pracy i czeka, aż przepływ pracy przejdzie w stan bezczynności.

2. Będzie się powtarzał lub zapisuje przepływ pracy w magazynie w trwałości.

3. Wznawia harmonogram przepływu pracy.

 **Zwolnienie** metoda wykonuje następujące czynności:

1. Wstrzymuje harmonogram przepływu pracy i czeka, aż przepływ pracy przejdzie w stan bezczynności.

2. Będzie się powtarzał lub zapisuje przepływ pracy w magazynie w trwałości.

3. Usuwa wystąpienie przepływu pracy w pamięci.

Zarówno **utrwalanie** i **zwolnienie** metody są blokowane, gdy przepływ pracy jest w strefie no-persist aż przepływ pracy zamyka strefy no-persist. Metody będzie kontynuowane przy użyciu operacji utrwalania lub zwolnij, po zakończeniu strefy utrwalanie nie. Jeśli strefa no-persist nie zostanie zakończone, zanim upłynie limit czasu lub jeśli proces trwałości trwa zbyt długo, zostanie zgłoszony TimeoutException.

## <a name="enable-persistence-for-workflow-services-in-code"></a>Włączanie stanów trwałych dla usług przepływu pracy w kodzie

**DurableInstancingOptions** członkiem <xref:System.ServiceModel.WorkflowServiceHost> klasa ma właściwość o nazwie **objekt InstanceStore** służące do kojarzenia magazyn wystąpienia z **elementu WorkflowServiceHost** .

```csharp
// wsh is an instance of WorkflowServiceHost class
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();
```

Gdy **WorkflowServiceHost** jest otwarty, trwałości jest włączany automatycznie, jeżeli **DurableInstancingOptions.InstanceStore** nie ma wartości null.

Zazwyczaj zachowanie usługi zawiera konkretne wystąpienie magazynu do użycia z hosta usługi przepływu pracy przy użyciu **objekt InstanceStore** właściwości. Na przykład SqlWorkflowInstanceStoreBehavior tworzy wystąpienie **SqlWorkflowInstanceStore**, konfiguruje je i przypisuje go do **DurableInstancingOptions.InstanceStore**.

## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Włączanie stanów trwałych dla przepływów pracy usługi przy użyciu pliku konfiguracji aplikacji

Stan trwały można włączyć za pomocą pliku konfiguracji aplikacji, dodając następujący kod do pliku app.config lub web.config:

```xml
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="myBehavior">
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatabaseServer;Initial Catalog=myPersistenceDatabase">
        </behavior>
      </serviceBehaviors>
    <behaviors>
  </system.serviceModel>
</configuration>
```
