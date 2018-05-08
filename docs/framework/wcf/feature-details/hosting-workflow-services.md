---
title: Hostowanie usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: 02d77b851dcd35108668ee6a42022e9721b84bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-workflow-services"></a>Hostowanie usług przepływu pracy
Usługi przepływu pracy musi być hostowany na jej odpowiadanie na przychodzące wiadomości. Usługi przepływu pracy korzystają z infrastruktury obsługi wiadomości WCF i w związku z tym znajdują się w podobny sposób. Jak usługi WCF usług przepływu pracy mogą być hostowane w dowolnej aplikacji zarządzanych, w obszarze usługi Internet Information Services (IIS) lub w obszarze usługi aktywacji procesów systemu Windows (WAS). Ponadto usługi przepływu pracy mogą być hostowane w obszarze AppFabric w systemie Windows Server. Aby uzyskać więcej informacji na temat systemu Windows Server AppFabric zobacz [dokumentacji systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193037), [funkcje hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=196494), i [pojęcia Hosting AppFabric](http://go.microsoft.com/fwlink/?LinkId=196495). Aby uzyskać więcej informacji na temat różnych sposobów host usługi WCF usług zobacz [Hosting usług](../../../../docs/framework/wcf/hosting-services.md).  
  
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
 Hosting Usługa przepływu pracy systemu Windows Server AppFabric odbywa się w taki sam sposób jak hosting w środowisku usług IIS / WAS. Jedyna różnica polega na fakt, że jest zainstalowany system Windows Server AppFabric. Windows Server AppFabric udostępnia narzędzia, które są dodawane do Menedżera internetowych usług informacyjnych, a także polecenia cmdlet środowiska powershell. Te narzędzia uproszczenia wdrażania, zarządzania i śledzenia usług przepływu pracy i usług WCF. . Aby uzyskać więcej informacji na temat systemu Windows Server AppFabric zobacz [systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=193037)  
  
## <a name="referencing-custom-activities"></a>Odwołanie do działań niestandardowych  
 Odwołania do niestandardowych działań musi zostać dodany do <`Assemblies`> w obszarze <`System.Web.Compilation`>, aby są ładowane do domeny aplikacji i Deserializator XAML jest w stanie zlokalizować typów. Te ustawienia mogą być dokonywane na poziomie aplikacji lub w katalogu głównym pliku Web.config Jeśli ustawienia ma być stosowana do wszystkich aplikacji na komputerze.  
  
## <a name="deployment"></a>wdrażania  
 Aby ułatwić sobie pracę wdrożenia został utworzony narzędzia Web Deployment. Narzędzie pozwala na migrowanie aplikacji między usługami IIS 6.0 i IIS 7.0, synchronizacji farmy serwerów i pakietów oraz archiwizowanie i wdrażanie aplikacji sieci Web. Aby uzyskać więcej informacji, zobacz [narzędzia wdrażania MS](http://go.microsoft.com/fwlink/?LinkId=178690)  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy wewnętrzne hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 [Konfigurowanie elementu WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)
