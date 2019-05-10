---
title: Hostowanie usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: dbb5e9b687a735376d720b83607fc67350cd429f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613336"
---
# <a name="hosting-workflow-services"></a>Hostowanie usług przepływu pracy
Usługi przepływu pracy musi być hostowany na jego odpowiadanie na wiadomości przychodzące. Usługi przepływu pracy korzystają z infrastruktury obsługi komunikatów usługi WCF i w związku z tym znajdują się w podobny sposób. Podobnie jak usługi WCF usług przepływu pracy mogą być hostowane w dowolnej aplikacji zarządzanych, w ramach usługi Internet Information Services (IIS) lub w obszarze Windows Process Activation usług (WAS). Ponadto usługi przepływu pracy mogą być hostowane w ramach systemu Windows Server AppFabric. Aby uzyskać więcej informacji na temat systemu Windows Server AppFabric zobacz [dokumentacji systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=193037), [funkcje hostingu programu AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494), i [pojęcia hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=196495). Aby uzyskać więcej informacji na temat różnych sposobów hosta usługi WCF usług zobacz [usług obsługującego](../../../../docs/framework/wcf/hosting-services.md).

## <a name="hosting-in-a-managed-application"></a>Hosting w aplikacji zarządzanej
 Hostowanie usługi przepływu pracy w zarządzanej aplikacji, należy użyć <xref:System.ServiceModel.Activities.WorkflowServiceHost> klasy. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Konstruktor pozwala na określenie pojedyncze wystąpienie usługi przepływu pracy, definicji usługi przepływu pracy lub działaniem używającym wiadomości działania przepływu pracy. Wywoływanie <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> powoduje, że Usługa rozpoczyna nasłuchiwanie przychodzących wiadomości.

## <a name="hosting-under-iis-or-was"></a>Hosting w ramach usług IIS i WAS
 Hostowanie usługi przepływu pracy w ramach usług IIS i WAS obejmuje tworzenie katalogów wirtualnych i umieszczanie plików w katalogu wirtualnym, który definiuje usługę i jego zachowanie. W przypadku hostowanie usługi przepływu pracy w ramach usług IIS i WAS istnieje kilka możliwości:

- Umieść plik .xamlx, który definiuje usługę przepływu pracy w programie IIS / WAS katalogu wirtualnego, wraz z pliku Web.config, który określa zachowania usług, punktów końcowych i innych elementów konfiguracji.

- Umieść plik .xamlx, który definiuje usługę przepływu pracy w programie IIS / WAS katalogu wirtualnego. Plik .xamlx określa punktów końcowych do uwidocznienia. Punkty końcowe są określone w `WorkflowService.Endpoints` elementu, jak pokazano w poniższym przykładzie.

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
    > Nie można określić zachowania w pliku .xamlx, dlatego należy określić ustawienia zachowania, należy użyć pliku Web.config.

- Umieść plik .xamlx, który definiuje usługę przepływu pracy w programie IIS / WAS katalogu wirtualnego. Ponadto umieść plików .svc w katalogu wirtualnym. Plik .svc pozwala określić niestandardowy fabryki hostów usług sieci Web, zastosuj niestandardowe zachowanie lub załadować konfiguracji z lokalizacji niestandardowej.

- Umieszczenie zestawu w usługach IIS / został katalogu wirtualnego, który zawiera działanie, które używa WCF działań dotyczących komunikatów.

 Plik .xamlx, który definiuje usługi przepływu pracy musi zawierać <`Service`> element główny lub element główny, który zawiera dowolny typ pochodną <xref:System.Workflow.ComponentModel.Activity>. Korzystając z szablonu działania programu Visual Studio, tworzony jest plik .xamlx. Korzystając z szablonu usługi przepływu pracy WCF, tworzony jest plik .xamlx.

## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Hostowanie usług przepływu pracy w systemie Windows Server AppFabric
 Hostowanie usługi przepływu pracy w ramach systemu Windows Server AppFabric odbywa się w taki sam sposób jak hostowania w usługach IIS / WAS. Jedyną różnicą jest fakt, że jest zainstalowany system Windows Server AppFabric. AppFabric w systemie Windows Server udostępnia narzędzia, które są dodawane do Menedżera internetowych usług informacyjnych, a także polecenia cmdlet środowiska powershell. Te narzędzia Uproszczenie wdrażania, zarządzania i śledzenia usług przepływu pracy i usług WCF.

## <a name="referencing-custom-activities"></a>Odwołanie do działań niestandardowych
 Odwołania do działania niestandardowe muszą zostać dodane do <`Assemblies`> sekcji <`System.Web.Compilation`> dzięki czemu są one ładowany do domeny aplikacji i Deserializator XAML jest w stanie zlokalizować typów. Te ustawienia mogą się na poziomie aplikacji lub w katalogu głównym pliku Web.config, jeśli stosowane do wszystkich aplikacji na maszynie.

## <a name="deployment"></a>wdrażania
 Narzędzie Web Deployment został utworzony w celu ułatwienia zadania wdrażania. To narzędzie pozwala na migrowanie aplikacji między usługami IIS 6.0 i IIS 7.0, synchronizowanie farm serwerów i pakietów oraz archiwizowanie i wdrażanie aplikacji sieci Web. Aby uzyskać więcej informacji, zobacz [narzędzia wdrażania MS](https://go.microsoft.com/fwlink/?LinkId=178690).

## <a name="see-also"></a>Zobacz także

- [Elementy wewnętrzne hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)
- [Konfigurowanie elementu WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)