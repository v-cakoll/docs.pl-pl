---
title: "Hostowanie usług przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ad4e5af26291c210f4f46f20e5b9585e3e095ae7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-workflow-services"></a>Hostowanie usług przepływu pracy
Usługi przepływu pracy musi być hostowany na jej odpowiadanie na przychodzące wiadomości. Użyj usługi przepływu pracy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiadomości w związku z tym infrastruktury i są hostowane w podobny sposób. Podobnie jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług przepływu pracy usługi może być hostowana w dowolnej aplikacji zarządzanych, w obszarze usługi Internet Information Services (IIS) lub w obszarze usługi aktywacji procesów systemu Windows (WAS). Ponadto usługi przepływu pracy mogą być hostowane w obszarze AppFabric w systemie Windows Server. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Zobacz Windows Server AppFabric [dokumentacji systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193037), [funkcje hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=196494), i [pojęcia Hosting AppFabric](http://go.microsoft.com/fwlink/?LinkId=196495). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]różne sposoby hosta [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług zobacz [Hosting usług](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="hosting-in-a-managed-application"></a>Hosting w aplikacji zarządzanej  
 Aby hosta usługi przepływu pracy w aplikacji zarządzanej, użyj <xref:System.ServiceModel.Activities.WorkflowServiceHost> klasy. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Konstruktor umożliwia określenie pojedyncze wystąpienie usługi przepływu pracy, definicji usługi przepływu pracy lub działanie, które korzysta z przepływu pracy działania dotyczące komunikatów. Wywoływanie <<!--zz xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A--> `System.ServiceModel.Activities.WorkflowServiceHost.Open`> powoduje, że usługa rozpocząć nasłuchiwania dla komunikatów przychodzących.  
  
## <a name="hosting-under-iis-or-was"></a>Hosting w ramach usług IIS lub WAS  
 Hosting usługi przepływu pracy w ramach usług IIS lub WAS obejmuje tworzenie katalogów wirtualnych i umieszczanie plików w katalogu wirtualnym, który definiuje usługę i jego zachowanie. W przypadku hostowania usługi przepływu pracy w ramach usług IIS lub WAS istnieje kilka możliwości:  
  
-   Umieść plik .xamlx, który definiuje usługi przepływu pracy w programie IIS / WAS katalog wirtualny wraz z plikiem Web.config, który określa zachowania usługi, punktów końcowych i innych elementów konfiguracji.  
  
-   Umieść plik .xamlx, który definiuje usługi przepływu pracy w programie IIS / WAS katalogu wirtualnego. Plik .xamlx określa punktów końcowych do udostępnienia. Punkty końcowe zostały określone w `WorkflowService.Endpoints` element, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <WorkflowService xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"  xmlns:p1="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
      <WorkflowService.Endpoints>  
        <Endpoint ServiceContractName="IWorkFlowEchoService" AddressUri="">  
          <Endpoint.Binding>  
            <BasicHttpBinding />  
          </Endpoint.Binding>  
        </Endpoint>  
      </WorkflowService.Endpoints>  
    <!-- ... -->  
    </WorkflowService>  
    ```  
  
    > [!NOTE]
    >  Nie można określić zachowania w pliku .xamlx, dlatego należy określić ustawienia zachowania, należy użyć pliku Web.config.  
  
-   Umieść plik .xamlx, który definiuje usługi przepływu pracy w programie IIS / WAS katalogu wirtualnego. Ponadto należy umieścić plik .svc w katalogu wirtualnym. Plik .svc pozwala określić niestandardowe fabryki hostów usług sieci Web, stosowanie niestandardowych zachowania lub załadować konfiguracji z lokalizacji niestandardowej.  
  
-   Umieść zestawu w programie IIS / został katalogu wirtualnego, który zawiera działania, która używa usługi WCF działań dotyczących komunikatów.  
  
 Plik .xamlx, który definiuje usługi przepływu pracy musi zawierać <`Service`> elementu głównego lub elementu głównego, który zawiera typ pochodny typu <xref:System.Workflow.ComponentModel.Activity>. Korzystając z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] szablon działania zostanie utworzony plik .xamlx. Gdy jest tworzony przy użyciu szablonu usługi przepływu pracy WCF pliku .xamlx.  
  
## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Hostowanie usług przepływu pracy w ramach systemu Windows Server AppFabric  
 Hosting Usługa przepływu pracy systemu Windows Server AppFabric odbywa się w taki sam sposób jak hosting w środowisku usług IIS / WAS. Jedyna różnica polega na fakt, że jest zainstalowany system Windows Server AppFabric. Windows Server AppFabric udostępnia narzędzia, które są dodawane do Menedżera internetowych usług informacyjnych, a także polecenia cmdlet środowiska powershell. Te narzędzia uproszczenia wdrażania, zarządzania i śledzenia usług przepływu pracy i usług WCF. . [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Zobacz Windows Server AppFabric [systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193037)  
  
## <a name="referencing-custom-activities"></a>Odwołanie do działań niestandardowych  
 Odwołania do niestandardowych działań musi zostać dodany do <`Assemblies`> w obszarze <`System.Web.Compilation`>, aby są ładowane do domeny aplikacji i Deserializator XAML jest w stanie zlokalizować typów. Te ustawienia mogą być dokonywane na poziomie aplikacji lub w katalogu głównym pliku Web.config Jeśli ustawienia ma być stosowana do wszystkich aplikacji na komputerze.  
  
## <a name="deployment"></a>wdrażania  
 Aby ułatwić sobie pracę wdrożenia został utworzony narzędzia Web Deployment. Narzędzie pozwala na migrowanie aplikacji między usługami IIS 6.0 i IIS 7.0, synchronizacji farmy serwerów i pakietów oraz archiwizowanie i wdrażanie aplikacji sieci Web. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Narzędzia wdrażania MS](http://go.microsoft.com/fwlink/?LinkId=178690)  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy wewnętrzne hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 [Konfigurowanie elementu WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)
