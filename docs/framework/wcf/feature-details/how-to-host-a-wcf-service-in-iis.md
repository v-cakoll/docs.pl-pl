---
title: 'Instrukcje: Hostowanie usługi WCF w programie IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 580b380a6c6349c6a4efa26e3eefe38bd660fa1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184924"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="ecfaa-102">Instrukcje: Hostowanie usługi WCF w programie IIS</span><span class="sxs-lookup"><span data-stu-id="ecfaa-102">How to: Host a WCF Service in IIS</span></span>
<span data-ttu-id="ecfaa-103">W tym temacie opisano podstawowe kroki wymagane do utworzenia usługi Windows Communication Foundation (WCF), która jest hostowana w internetowych usługach informacyjnych (IIS).</span><span class="sxs-lookup"><span data-stu-id="ecfaa-103">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="ecfaa-104">W tym temacie założono, że użytkownik jest zaznajomiony z usługami IIS i jak używać narzędzia do zarządzania usługami IIS do tworzenia aplikacji usług IIS i zarządzania nimi.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-104">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="ecfaa-105">Aby uzyskać więcej informacji o usługach IIS, zobacz [Internetowe usługi informacyjne](https://www.iis.net/).</span><span class="sxs-lookup"><span data-stu-id="ecfaa-105">For more information about IIS see [Internet Information Services](https://www.iis.net/).</span></span> <span data-ttu-id="ecfaa-106">Usługa WCF, która działa w środowisku usług IIS, w pełni wykorzystuje funkcje usług IIS, takie jak recykling procesów, bezczynne zamykanie systemu, monitorowanie kondycji procesu i aktywacja oparta na wiadomościach.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-106">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="ecfaa-107">Ta opcja hostingu wymaga prawidłowej konfiguracji usług IIS, ale nie wymaga, aby każdy kod hostingu był zapisywany jako część aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-107">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="ecfaa-108">Hostingi iis można używać tylko z transportem HTTP.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-108">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="ecfaa-109">Aby uzyskać więcej informacji o tym, jak WCF i ASP.NET współdziałają, zobacz [Usługi WCF i ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="ecfaa-109">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="ecfaa-110">Aby uzyskać więcej informacji na temat konfigurowania zabezpieczeń, zobacz [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md).</span><span class="sxs-lookup"><span data-stu-id="ecfaa-110">For more information about configuring security, see [Security](../../../../docs/framework/wcf/feature-details/security.md).</span></span>  
  
 <span data-ttu-id="ecfaa-111">Aby zapoznać się z kopią źródłową tego przykładu, zobacz [Hosting IIS przy użyciu kodu wbudowanego](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="ecfaa-111">For the source copy of this example, see [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="ecfaa-112">Aby utworzyć usługę obsługiwaną przez usługi IIS</span><span class="sxs-lookup"><span data-stu-id="ecfaa-112">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="ecfaa-113">Upewnij się, że usługi IIS są zainstalowane i uruchomione na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-113">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="ecfaa-114">Aby uzyskać więcej informacji na temat instalowania i konfigurowania usługi IIS, zobacz [Instalowanie i konfigurowanie usługi IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span><span class="sxs-lookup"><span data-stu-id="ecfaa-114">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span></span>  
  
2. <span data-ttu-id="ecfaa-115">Utwórz nowy folder dla plików aplikacji o nazwie "IISHostedCalcService", upewnij się, że ASP.NET ma dostęp do zawartości folderu, a narzędzie do zarządzania usługami IIS służy do tworzenia nowej aplikacji usług IIS, która fizycznie znajduje się w tym katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-115">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="ecfaa-116">Podczas tworzenia aliasu dla katalogu aplikacji użyj "IISHostedCalc".</span><span class="sxs-lookup"><span data-stu-id="ecfaa-116">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="ecfaa-117">Utwórz nowy plik o nazwie "service.svc" w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-117">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="ecfaa-118">Edytuj ten plik, @ServiceHost dodając następujący element.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-118">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="ecfaa-119">Utwórz podkatalog App_Code w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-119">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="ecfaa-120">Utwórz plik kodu o nazwie Service.cs w podkatalogu App_Code.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-120">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="ecfaa-121">Dodaj następujące instrukcje do górnej części pliku Service.cs.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-121">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="ecfaa-122">Dodaj następującą deklarację obszaru nazw po using instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-122">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="ecfaa-123">Zdefiniuj umowę serwisową wewnątrz deklaracji obszaru nazw, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-123">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="ecfaa-124">Zaimplementuj umowę serwisową po definicji umowy serwisowej, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-124">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="ecfaa-125">Utwórz plik o nazwie "Web.config" w katalogu aplikacji i dodaj do pliku następujący kod konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-125">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="ecfaa-126">W czasie wykonywania WCF infrastruktury używa informacji do konstruowania punktu końcowego, który aplikacje klienckie mogą komunikować się z.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-126">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     <span data-ttu-id="ecfaa-127">W tym przykładzie jawnie określa punkty końcowe w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-127">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="ecfaa-128">Jeśli nie dodać żadnych punktów końcowych do usługi, środowisko wykonawcze dodaje domyślne punkty końcowe dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="ecfaa-129">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="ecfaa-129">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="ecfaa-130">Aby upewnić się, że usługa jest obsługiwana poprawnie, otwórz wystąpienie programu Internet Explorer i przejdź do adresu URL usługi:`http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="ecfaa-130">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecfaa-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="ecfaa-131">Example</span></span>  
 <span data-ttu-id="ecfaa-132">Poniżej znajduje się pełna lista kodu usługi kalkulatora hostowanego usług IIS.</span><span class="sxs-lookup"><span data-stu-id="ecfaa-132">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="ecfaa-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecfaa-133">See also</span></span>

- [<span data-ttu-id="ecfaa-134">Hostowanie przez Internetowe usługi informacyjne</span><span class="sxs-lookup"><span data-stu-id="ecfaa-134">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [<span data-ttu-id="ecfaa-135">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="ecfaa-135">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="ecfaa-136">Usługi WCF i platforma ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ecfaa-136">WCF Services and ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [<span data-ttu-id="ecfaa-137">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="ecfaa-137">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
- <span data-ttu-id="ecfaa-138">[Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ecfaa-138">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
