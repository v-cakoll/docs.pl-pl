---
title: Hostowanie usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: 908ef7ebb9bfb1e2c49d96e41c0df1d843c0454d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597283"
---
# <a name="hosting-workflow-services"></a>Hostowanie usług przepływu pracy

Usługa przepływu pracy musi być hostowana, aby mogła reagować na wiadomości przychodzące. Usługi przepływu pracy korzystają z infrastruktury obsługi komunikatów WCF i dlatego są hostowane w podobny sposób. Podobnie jak w przypadku usług WCF usługi przepływu pracy mogą być hostowane w dowolnej aplikacji zarządzanej, w obszarze Internet Information Services (IIS) lub w obszarze usługi aktywacji procesów systemu Windows (WAS). Ponadto usługi przepływu pracy mogą być hostowane w sieci szkieletowej aplikacji systemu Windows Server. Aby uzyskać więcej informacji na temat sieci szkieletowej aplikacji systemu Windows Server, zobacz [dokumentację usługi Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)), [funkcje hostingu programu AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))i [koncepcje hostingu usługi AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677371(v=azure.10)). Aby uzyskać więcej informacji na temat różnych sposobów hostowania usług WCF, zobacz [usługi hostingu](../hosting-services.md).

## <a name="hosting-in-a-managed-application"></a>Hosting w aplikacji zarządzanej
 Aby hostować usługę przepływu pracy w aplikacji zarządzanej, należy użyć <xref:System.ServiceModel.Activities.WorkflowServiceHost> klasy. <xref:System.ServiceModel.Activities.WorkflowServiceHost>Konstruktor umożliwia określenie pojedynczego wystąpienia usługi przepływu pracy, definicji usługi przepływu pracy lub działania korzystającego z działań związanych z obsługą komunikatów przepływu pracy. Wywołanie <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> powoduje, że Usługa uruchamia nasłuchiwanie komunikatów przychodzących.

## <a name="hosting-under-iis-or-was"></a>Hosting w ramach usług IIS lub WAS
 Hostowanie usługi przepływu pracy w ramach usług IIS lub polega na utworzeniu katalogu wirtualnego i umieszczeniu plików w katalogu wirtualnym, które definiują usługę i jej zachowanie. W przypadku hostowania usługi przepływu pracy w ramach usług IIS lub była kilka możliwości:

- Umieść plik. xamlx, który definiuje usługę przepływu pracy w katalogu wirtualnym usług IIS/WAS wraz z plikiem Web. config, który określa zachowania usługi, punkty końcowe i inne elementy konfiguracji.

- Umieść plik. xamlx, który definiuje usługę przepływu pracy w katalogu wirtualnym usług IIS/WAS. Plik. xamlx określa punkty końcowe do udostępnienia. Punkty końcowe są określone w `WorkflowService.Endpoints` elemencie, jak pokazano w poniższym przykładzie.

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
    > Nie można określać zachowań w pliku. xamlx, dlatego należy użyć pliku Web. config, jeśli trzeba określić ustawienia zachowania.

- Umieść plik. xamlx, który definiuje usługę przepływu pracy w katalogu wirtualnym usług IIS/WAS. Ponadto Umieść plik. svc w katalogu wirtualnym. Plik SVC pozwala określić niestandardową fabrykę hosta usługi sieci Web, zastosować zachowanie niestandardowe lub załadować konfigurację z lokalizacji niestandardowej.

- Umieść zestaw w katalogu wirtualnym usługi IIS/WAS zawierający działanie, które korzysta z działań związanych z obsługą komunikatów WCF.

 Plik. xamlx, który definiuje usługę przepływu pracy, musi zawierać `Service` element główny> <lub element główny, który zawiera dowolny typ pochodzący z <xref:System.Workflow.ComponentModel.Activity> . W przypadku korzystania z szablonu działania programu Visual Studio tworzony jest plik XAMLX. W przypadku korzystania z szablonu usługi przepływu pracy WCF tworzony jest plik XAMLX.

## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Hostowanie usług przepływu pracy w sieci szkieletowej aplikacji systemu Windows Server
 Hosting usługi przepływu pracy w ramach sieci szkieletowej aplikacji systemu Windows Server odbywa się w taki sam sposób, jak w przypadku usług IIS/WAS. Jedyną różnicą jest fakt, że zainstalowano aplikację sieci szkieletowej systemu Windows Server. Windows Server App Fabric oferuje narzędzia, które są dodawane do programu Internet Information Services Manager, a także program PowerShell polecenia cmdlet. Narzędzia te upraszczają wdrażanie i śledzenie usług Workflow Services oraz usług WCF oraz zarządzanie nimi.

## <a name="referencing-custom-activities"></a>Odwoływanie się do działań niestandardowych
 Odwołania do działań niestandardowych należy dodać do `Assemblies` sekcji <> w obszarze <`System.Web.Compilation`> tak, aby były one ładowane do domeny aplikacji, a Deserializator XAML będzie mógł zlokalizować typy. Te ustawienia można wykonać na poziomie aplikacji lub w katalogu głównym Web. config, jeśli ustawienia mają być stosowane do wszystkich aplikacji na komputerze.

## <a name="deployment"></a>Wdrożenie
 Narzędzie Web Deployment zostało utworzone w celu ułatwienia wdrażania zadania. Narzędzie to umożliwia Migrowanie aplikacji między usługami IIS 6,0 i IIS 7,0, synchronizowanie farm serwerów oraz pakowanie, archiwizowanie i wdrażanie aplikacji sieci Web. Aby uzyskać więcej informacji, zobacz [Narzędzie wdrażania firmy Microsoft](https://go.microsoft.com/fwlink/?LinkId=178690).

## <a name="see-also"></a>Zobacz też

- [Elementy wewnętrzne hosta usługi przepływu pracy](workflow-service-host-internals.md)
- [Konfigurowanie elementu WorkflowServiceHost](configuring-workflowservicehost.md)
