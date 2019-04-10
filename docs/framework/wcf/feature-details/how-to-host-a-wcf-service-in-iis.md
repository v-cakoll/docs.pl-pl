---
title: 'Instrukcje: hostowanie usługi WCF w usługach IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: f106ce1bca67f8b88df0835496eea0b3297ac946
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309683"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="92905-102">Instrukcje: hostowanie usługi WCF w usługach IIS</span><span class="sxs-lookup"><span data-stu-id="92905-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="92905-103">W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia usługi Windows Communication Foundation (WCF), który znajduje się w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="92905-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="92905-104">W tym temacie przyjęto założenie, są zaznajomieni z usług IIS i dowiedzieć się, jak używać narzędzia do zarządzania usług IIS do tworzenia i obsługi aplikacji programu IIS.</span><span class="sxs-lookup"><span data-stu-id="92905-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="92905-105">Aby uzyskać więcej informacji na temat usług IIS zobacz [Internetowe usługi informacyjne](https://go.microsoft.com/fwlink/?LinkId=132449).</span><span class="sxs-lookup"><span data-stu-id="92905-105">For more information about IIS see [Internet Information Services](https://go.microsoft.com/fwlink/?LinkId=132449).</span></span> <span data-ttu-id="92905-106">Usługi WCF, który jest uruchamiany w środowisku usług IIS wykorzystuje pełną funkcje usług IIS, takie jak odtwarzanie procesów, bezczynności zamykania, monitorowania kondycji procesu i aktywacja oparta na komunikatach.</span><span class="sxs-lookup"><span data-stu-id="92905-106">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="92905-107">Ta opcja hostingu wymaga, aby poprawnie skonfigurować usługi IIS, ale nie wymaga się, że każdy kod hostingu zapisywane jako część aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92905-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="92905-108">Umożliwia hostowanie usług IIS tylko w przypadku transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="92905-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="92905-109">Aby uzyskać więcej informacji na temat usługi WCF i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] wchodzić w interakcje, zobacz [usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="92905-109">For more information about how WCF and [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="92905-110">Aby uzyskać więcej informacji na temat konfigurowania zabezpieczeń, zobacz [zabezpieczeń](../../../../docs/framework/wcf/feature-details/security.md).</span><span class="sxs-lookup"><span data-stu-id="92905-110">For more information about configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="92905-111">Źródło kopię w tym przykładzie można zobaczyć [IIS hostingu przy użyciu kodu wbudowanego](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="92905-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="92905-112">Tworzenie usługi hostowanej przez Internetowe usługi informacyjne</span><span class="sxs-lookup"><span data-stu-id="92905-112">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="92905-113">Upewnij się, czy program IIS jest zainstalowana i uruchomiona na komputerze.</span><span class="sxs-lookup"><span data-stu-id="92905-113">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="92905-114">Aby uzyskać więcej informacji na temat instalowania i konfigurowania usług IIS zobacz [Instalowanie i konfigurowanie usług IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=132128)</span><span class="sxs-lookup"><span data-stu-id="92905-114">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=132128)</span></span>  
  
2. <span data-ttu-id="92905-115">Utwórz nowy folder na potrzeby plików aplikacji o nazwie "IISHostedCalcService", upewnij się, że [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ma dostęp do zawartości folderu i użyć narzędzia do zarządzania usług IIS, aby utworzyć nową aplikację usług IIS, która fizycznie znajduje się w tej aplikacji katalog.</span><span class="sxs-lookup"><span data-stu-id="92905-115">Create a new folder for your application files called "IISHostedCalcService", ensure that [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="92905-116">Podczas tworzenia alias do użytku w katalogu aplikacji "IISHostedCalc".</span><span class="sxs-lookup"><span data-stu-id="92905-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="92905-117">Utwórz nowy plik o nazwie "service.svc" w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92905-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="92905-118">Edytuj ten plik, dodając następujące @ServiceHost elementu.</span><span class="sxs-lookup"><span data-stu-id="92905-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4. <span data-ttu-id="92905-119">Utwórz podkatalog App_Code w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92905-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="92905-120">Utwórz plik kodu o nazwie Service.cs w podkatalogu App_Code.</span><span class="sxs-lookup"><span data-stu-id="92905-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="92905-121">Dodaj następujące za pomocą instrukcji na górze pliku Service.cs.</span><span class="sxs-lookup"><span data-stu-id="92905-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="92905-122">Dodaj następującą deklarację przestrzeni nazw, gdy po użyciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="92905-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="92905-123">Definiowanie kontraktu usługi, wewnątrz deklaracji przestrzeni nazw, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="92905-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="92905-124">Implementowanie kontraktu usługi, po usługę definicję kontraktu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="92905-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="92905-125">Utwórz plik o nazwie "Web.config" w katalogu aplikacji, a następnie dodaj następujący kod konfiguracji do pliku.</span><span class="sxs-lookup"><span data-stu-id="92905-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="92905-126">W czasie wykonywania infrastruktura WCF używa tych informacji do utworzenia punktu końcowego, który aplikacje klienckie mogą się komunikować.</span><span class="sxs-lookup"><span data-stu-id="92905-126">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     <span data-ttu-id="92905-127">Ten przykład jawnie określa punkty końcowe w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="92905-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="92905-128">Jeśli nie dodasz żadnych punktów końcowych do usługi, środowiska uruchomieniowego dodaje domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="92905-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="92905-129">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="92905-129">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="92905-130">Aby upewnić się, że usługa jest hostowana poprawnie, otwórz wystąpienie programu Internet Explorer i przejdź do adresu URL usługi:</span><span class="sxs-lookup"><span data-stu-id="92905-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL:</span></span> `http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a><span data-ttu-id="92905-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="92905-131">Example</span></span>  
 <span data-ttu-id="92905-132">Poniżej znajduje się że kalkulatora usługi hostowanej pełną listę kod dla usług IIS.</span><span class="sxs-lookup"><span data-stu-id="92905-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)] 
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)] 
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="92905-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92905-133">See also</span></span>

- [<span data-ttu-id="92905-134">Hostowanie przez Internetowe usługi informacyjne</span><span class="sxs-lookup"><span data-stu-id="92905-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [<span data-ttu-id="92905-135">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="92905-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="92905-136">Usługi WCF i platforma ASP.NET</span><span class="sxs-lookup"><span data-stu-id="92905-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [<span data-ttu-id="92905-137">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="92905-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
- [<span data-ttu-id="92905-138">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="92905-138">Windows Server App Fabric Hosting Features</span></span>](https://go.microsoft.com/fwlink/?LinkId=201276)
