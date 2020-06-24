---
title: 'Instrukcje: Hostowanie usługi WCF w programie IIS'
description: Dowiedz się, jak utworzyć usługę WCF hostowaną w Internet Information Services (IIS). Hostingu usług IIS można używać tylko z transportem HTTP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 63549b85f7bcdd4f246005401694db8827248038
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246912"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="46539-104">Instrukcje: Hostowanie usługi WCF w programie IIS</span><span class="sxs-lookup"><span data-stu-id="46539-104">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="46539-105">W tym temacie przedstawiono podstawowe kroki wymagane do utworzenia usługi Windows Communication Foundation (WCF), która jest hostowana w usłudze Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="46539-105">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="46539-106">W tym temacie założono, że znasz usługi IIS i wiesz, jak używać narzędzia do zarządzania usługami IIS do tworzenia aplikacji usług IIS i zarządzania nimi.</span><span class="sxs-lookup"><span data-stu-id="46539-106">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="46539-107">Aby uzyskać więcej informacji na temat usług IIS, zobacz [Internet Information Services](https://www.iis.net/).</span><span class="sxs-lookup"><span data-stu-id="46539-107">For more information about IIS see [Internet Information Services](https://www.iis.net/).</span></span> <span data-ttu-id="46539-108">Usługa WCF działająca w środowisku usług IIS pełni funkcję usług IIS, taką jak odtwarzanie procesów, zamykanie bezczynności, monitorowanie kondycji procesu i Aktywacja oparta na komunikatach.</span><span class="sxs-lookup"><span data-stu-id="46539-108">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="46539-109">Ta opcja hostingu wymaga poprawnego skonfigurowania usług IIS, ale nie wymaga, aby żaden kod hostingu był zapisywana jako część aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46539-109">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="46539-110">Hostingu usług IIS można używać tylko z transportem HTTP.</span><span class="sxs-lookup"><span data-stu-id="46539-110">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="46539-111">Aby uzyskać więcej informacji o tym, jak działa WCF i ASP.NET, zobacz [usługi WCF i ASP.NET](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="46539-111">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="46539-112">Aby uzyskać więcej informacji o konfigurowaniu zabezpieczeń, zobacz [zabezpieczenia](security.md).</span><span class="sxs-lookup"><span data-stu-id="46539-112">For more information about configuring security, see [Security](security.md).</span></span>  
  
 <span data-ttu-id="46539-113">Aby uzyskać kopię źródła tego przykładu, zobacz [hosting usług IIS przy użyciu kodu wbudowanego](../samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="46539-113">For the source copy of this example, see [IIS Hosting Using Inline Code](../samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="46539-114">Aby utworzyć usługę hostowaną przez usługi IIS</span><span class="sxs-lookup"><span data-stu-id="46539-114">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="46539-115">Upewnij się, że usługi IIS są zainstalowane i uruchomione na komputerze.</span><span class="sxs-lookup"><span data-stu-id="46539-115">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="46539-116">Aby uzyskać więcej informacji na temat instalowania i konfigurowania usług IIS, zobacz [Instalowanie i Konfigurowanie usług iis 7,0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span><span class="sxs-lookup"><span data-stu-id="46539-116">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span></span>  
  
2. <span data-ttu-id="46539-117">Utwórz nowy folder dla plików aplikacji o nazwie "IISHostedCalcService", upewnij się, że ASP.NET ma dostęp do zawartości folderu, a następnie użyj narzędzia do zarządzania usługami IIS, aby utworzyć nową aplikację usług IIS, która znajduje się fizycznie w tym katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46539-117">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="46539-118">Podczas tworzenia aliasu dla katalogu aplikacji użyj polecenia "IISHostedCalc".</span><span class="sxs-lookup"><span data-stu-id="46539-118">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="46539-119">Utwórz nowy plik o nazwie "Service. svc" w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46539-119">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="46539-120">Edytuj ten plik, dodając następujący @ServiceHost element.</span><span class="sxs-lookup"><span data-stu-id="46539-120">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="46539-121">Utwórz podkatalog App_Code w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="46539-121">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="46539-122">Utwórz plik kodu o nazwie Service.cs w podkatalogu App_Code.</span><span class="sxs-lookup"><span data-stu-id="46539-122">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="46539-123">Dodaj następujące instrukcje using na początku pliku Service.cs.</span><span class="sxs-lookup"><span data-stu-id="46539-123">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="46539-124">Dodaj następującą deklarację przestrzeni nazw po instrukcjach using.</span><span class="sxs-lookup"><span data-stu-id="46539-124">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="46539-125">Zdefiniuj kontrakt usługi w deklaracji przestrzeni nazw, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="46539-125">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="46539-126">Zaimplementuj kontrakt usługi po definicji kontraktu usługi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="46539-126">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="46539-127">Utwórz plik o nazwie "Web.config" w katalogu aplikacji i Dodaj następujący kod konfiguracyjny do pliku.</span><span class="sxs-lookup"><span data-stu-id="46539-127">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="46539-128">W czasie wykonywania Infrastruktura WCF używa tych informacji do konstruowania punktu końcowego, z którym mogą komunikować się aplikacje klienckie.</span><span class="sxs-lookup"><span data-stu-id="46539-128">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     <span data-ttu-id="46539-129">Ten przykład jawnie określa punkty końcowe w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="46539-129">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="46539-130">Jeśli nie dodasz żadnych punktów końcowych do usługi, środowisko uruchomieniowe doda domyślne punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="46539-130">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="46539-131">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [uproszczoną konfigurację](../simplified-configuration.md) i [uproszczoną konfigurację dla usług WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="46539-131">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="46539-132">Aby upewnić się, że usługa jest hostowana prawidłowo, Otwórz wystąpienie programu Internet Explorer i przejdź do adresu URL usługi:`http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="46539-132">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="46539-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="46539-133">Example</span></span>  
 <span data-ttu-id="46539-134">Poniżej znajduje się kompletna lista kodu dla usługi hostowanego kalkulatora usług IIS.</span><span class="sxs-lookup"><span data-stu-id="46539-134">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="46539-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46539-135">See also</span></span>

- [<span data-ttu-id="46539-136">Hostowanie przez Internetowe usługi informacyjne</span><span class="sxs-lookup"><span data-stu-id="46539-136">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="46539-137">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="46539-137">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="46539-138">Usługi WCF i platforma ASP.NET</span><span class="sxs-lookup"><span data-stu-id="46539-138">WCF Services and ASP.NET</span></span>](wcf-services-and-aspnet.md)
- [<span data-ttu-id="46539-139">Bezpieczeństwo</span><span class="sxs-lookup"><span data-stu-id="46539-139">Security</span></span>](security.md)
- <span data-ttu-id="46539-140">[Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="46539-140">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
