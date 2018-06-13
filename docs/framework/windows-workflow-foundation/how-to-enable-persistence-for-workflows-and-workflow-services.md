---
title: 'Porady: Włącz trwałość dla przepływów pracy i usług przepływu pracy'
ms.date: 03/30/2017
ms.assetid: 2b1c8bf3-9866-45a4-b06d-ee562393e503
ms.openlocfilehash: 35158c45217e764bc2e27dac26f8d680e5897fa9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514421"
---
# <a name="how-to-enable-persistence-for-workflows-and-workflow-services"></a>Porady: Włącz trwałość dla przepływów pracy i usług przepływu pracy
W tym temacie opisano, jak do włączenia trwałości dla przepływów pracy i usług przepływu pracy.  
  
## <a name="enable-persistence-for-workflows"></a>Włącz trwałość dla przepływów pracy  
 Można skojarzyć magazyn wystąpienia z **WorkflowApplication** za pomocą <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwość <xref:System.Activities.WorkflowApplication> klasy. <xref:System.Activities.WorkflowApplication.Persist%2A> Metody zapisuje lub będzie się powtarzał przepływu pracy do wystąpienia magazynu skojarzone z aplikacją. <xref:System.Activities.WorkflowApplication.Unload%2A> Metoda się powtarza przepływu pracy w magazynie wystąpień, a następnie zwalnia wystąpienie z pamięci. **Obciążenia** metody ładuje przepływu pracy do pamięci za pomocą przepływu pracy danych przechowywanych w magazynie informacji o trwałości wystąpienia.  
  
 **Utrwalanie** metoda wykonuje następujące czynności:  
  
1.  Wstrzymuje harmonogramu przepływu pracy i czeka, aż przepływ pracy wchodzi w stan bezczynności.  
  
2.  Będzie nadal występował lub zapisuje przepływ pracy w magazynie informacji o trwałości.  
  
3.  Wznawia harmonogramu przepływu pracy.  
  
 **Zwolnienie** metoda wykonuje następujące czynności:  
  
1.  Wstrzymuje harmonogramu przepływu pracy i czeka, aż przepływ pracy wchodzi w stan bezczynności.  
  
2.  Będzie nadal występował lub zapisuje przepływ pracy w magazynie informacji o trwałości.  
  
3.  Usuwa wystąpienie przepływu pracy w pamięci.  
  
 Zarówno **utrwalanie** i **zwolnienie** metody zablokuje podczas przepływu pracy jest w strefie no-persist strefy no-persist kończy działanie przepływu pracy. Metody będzie kontynuowane przy użyciu operacji utrwalania lub unload po zakończeniu strefy utrwalania nie. Jeśli strefa no-persist nie zostanie zakończone, zanim upłynie limit czasu lub zbyt długo procesu trwałości, zostanie zgłoszony TimeoutException.  
  
## <a name="enable-persistence-for-workflow-services-in-code"></a>Włącz trwałość dla usług przepływu pracy w kodzie  
 **DurableInstancingOptions** członkiem <xref:System.ServiceModel.WorkflowServiceHost> klasa ma właściwości o nazwie **InstanceStore** której można skojarzyć magazyn wystąpienia z **obiektu WorkflowServiceHost** .  
  
```  
// wsh is an instance of WorkflowServiceHost class  
wsh.DurableInstancingOptions.InstanceStore = new SqlWorkflowInstanceStore();  
```  
  
 Gdy **obiektu WorkflowServiceHost** jest otwarty, trwałości jest włączany automatycznie, jeżeli **DurableInstancingOptions.InstanceStore** nie jest zerowa.  
  
 Zwykle, zachowanie usługi zapewnia magazynu konkretne wystąpienie ma być używany z hosta usługi przepływu pracy przy użyciu **InstanceStore** właściwości. Na przykład SqlWorkflowInstanceStoreBehavior tworzy wystąpienie **SqlWorkflowInstanceStore**, konfiguruje ją i przypisuje go do **DurableInstancingOptions.InstanceStore**.  
  
## <a name="enable-persistence-for-workflow-services-using-an-application-configuration-file"></a>Włącz trwałość dla usług przepływu pracy przy użyciu pliku konfiguracji aplikacji  
 Trwałości można włączyć przy użyciu pliku konfiguracji aplikacji, dodając następujący kod do pliku app.config lub web.config:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="myBehavior">  
          <SqlWorkflowInstanceStore connectionString="Data Source=myDatatbaseServer;Initial Catalog=myPersistenceDatabase">  
        </behavior>  
      </serviceBehaviors>  
    <behaviors>  
  </system.serviceModel>  
</configuration>  
```
