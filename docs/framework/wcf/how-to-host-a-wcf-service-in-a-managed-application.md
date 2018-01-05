---
title: "Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6491faa6134c1e80e07294d8f888200c04fa8704
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-application"></a><span data-ttu-id="4f2bc-102">Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="4f2bc-102">How to: Host a WCF Service in a Managed Application</span></span>
<span data-ttu-id="4f2bc-103">Aby obsługiwać usługę w aplikacji zarządzanej, osadzanie kodu dla usługi w kodzie aplikacji zarządzanych, albo imperatively w kodzie, deklaratywnego za pomocą konfiguracji lub użyciu domyślne punkty końcowe, określić punkt końcowy usługi, a następnie utwórz wystąpienie klasy <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="4f2bc-104">Aby rozpocząć odbieranie komunikatów, należy wywołać <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="4f2bc-105">Tworzy i otwiera odbiornika dla usługi.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="4f2bc-106">Hosting usług w ten sposób jest często określany jako "hostingu samodzielnego" ponieważ wykonuje hostingu pracy samego zarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="4f2bc-107">Aby zamknąć tę usługę, należy wywołać <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="4f2bc-108">Usługi mogą być również obsługiwane w usłudze zarządzanej systemu Windows, w konsoli Internet Information Services (IIS) lub w usługi aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="4f2bc-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="4f2bc-109">hosting opcje dla usługi, zobacz [Hosting usług](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="4f2bc-109"> hosting options for a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
 <span data-ttu-id="4f2bc-110">Usługi w zarządzanej aplikacji hosta jest najbardziej elastycznym opcja, ponieważ wymaga co najmniej infrastruktury do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="4f2bc-111">hosting usług aplikacji zarządzanych, zobacz [Hosting w zarządzanej aplikacji](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="4f2bc-111"> hosting services in managed applications, see [Hosting in a Managed Application](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>  
  
 <span data-ttu-id="4f2bc-112">W poniższej procedurze przedstawiono implementowania samodzielnie hostowana usługa w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>  
  
### <a name="to-create-a-self-hosted-service"></a><span data-ttu-id="4f2bc-113">Aby utworzyć usługę hostowanie Samoobsługowe</span><span class="sxs-lookup"><span data-stu-id="4f2bc-113">To create a self-hosted service</span></span>  
  
1.  <span data-ttu-id="4f2bc-114">Otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] i wybierz **nowy**, **projektu...**  z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-114">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New**, **Project...** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="4f2bc-115">W **zainstalowane szablony** listy, wybierz **Visual C#**, **Windows** lub **Visual Basic**, **Windows**.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-115">In the **Installed Templates** list, select **Visual C#**, **Windows** or **Visual Basic**, **Windows**.</span></span> <span data-ttu-id="4f2bc-116">W zależności od Twojego [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ustawienia, jeden lub oba te mogą być w obszarze **inne języki** w węźle **zainstalowane szablony** listy.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-116">Depending on your [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] settings, one or both of these may be under the **Other Languages** node in the **Installed Templates** list.</span></span>  
  
3.  <span data-ttu-id="4f2bc-117">Wybierz **aplikacji konsoli** z **Windows** listy.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-117">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="4f2bc-118">Typ `SelfHost` w **nazwa** polu i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-118">Type `SelfHost` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="4f2bc-119">Kliknij prawym przyciskiem myszy **SelfHost** w **Eksploratora rozwiązań** i wybierz **Dodawanie odwołania...** . Wybierz **System.ServiceModel** z **.NET** i kliknij polecenie **OK**.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference...**. Select **System.ServiceModel** from the **.NET** tab and click **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="4f2bc-120">Jeśli **Eksploratora rozwiązań** okno nie jest widoczny, wybierz pozycję **Eksploratora rozwiązań** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-120">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="4f2bc-121">Kliknij dwukrotnie **Program.cs** lub **Module1.vb** w **Eksploratora rozwiązań** aby otworzyć go w oknie kodu, jeśli nie jest już otwarty.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-121">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window if it is not already open.</span></span> <span data-ttu-id="4f2bc-122">Dodaj następujące instrukcje w górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-122">Add the following statements at the top of the file.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  <span data-ttu-id="4f2bc-123">Definiowanie i implementowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-123">Define and implement a service contract.</span></span> <span data-ttu-id="4f2bc-124">W tym przykładzie definiuje `HelloWorldService` zwracającą wiadomości na podstawie danych wprowadzonych z usługą.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-124">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="4f2bc-125">Zdefiniuj i zaimplementuj interfejs usługi, zobacz [porady: definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) i [porady: Implementowanie kontraktu usługi](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="4f2bc-125"> how to define and implement a service interface, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span></span>  
  
7.  <span data-ttu-id="4f2bc-126">W górnej części `Main` metody, Utwórz wystąpienie <xref:System.Uri> klasy adres podstawowy usługi.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-126">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  <span data-ttu-id="4f2bc-127">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy, przekazując <xref:System.Type> reprezentująca typu usługi i podstawowym adresów identyfikator URI (Uniform Resource) do <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-127">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="4f2bc-128">Włącz publikowanie metadanych, a następnie wywołać <xref:System.ServiceModel.ICommunicationObject.Open%2A> metoda <xref:System.ServiceModel.ServiceHost> zainicjować usługi i przygotowywania ich do odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-128">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]       
  
    > [!NOTE]
    >  <span data-ttu-id="4f2bc-129">W tym przykładzie używane domyślne punkty końcowe, a nie plik konfiguracji jest wymagany dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-129">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="4f2bc-130">Jeśli nie skonfigurowano żadnych punktów końcowych, środowisko uruchomieniowe tworzy jeden punkt końcowy dla każdego adresu podstawowego dla każdej umowy serwisowej zaimplementowanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-130">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="4f2bc-131">domyślne punkty końcowe, zobacz [uproszczony konfiguracji](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4f2bc-131"> default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="4f2bc-132">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-132">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="to-test-the-service"></a><span data-ttu-id="4f2bc-133">Aby przetestować usługę</span><span class="sxs-lookup"><span data-stu-id="4f2bc-133">To test the service</span></span>  
  
1.  <span data-ttu-id="4f2bc-134">Naciśnij klawisze Ctrl + F5, aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-134">Press Ctrl + F5 to run the service.</span></span>  
  
2.  <span data-ttu-id="4f2bc-135">Otwórz **klienta testowego WCF**.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-135">Open **WCF Test Client**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="4f2bc-136">Aby otworzyć **klienta testowego WCF**, otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] wiersz polecenia i wykonywanie **WcfTestClient.exe**.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-136">To open **WCF Test Client**, open a [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] command prompt and execute **WcfTestClient.exe**.</span></span>  
  
3.  <span data-ttu-id="4f2bc-137">Wybierz **dodawania usługi...**  z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-137">Select **Add Service...** from the **File** menu.</span></span>  
  
4.  <span data-ttu-id="4f2bc-138">Typ `http://localhost:8080/hello` w polu adres i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-138">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="4f2bc-139">Upewnij się, że usługa jest uruchomiona. w przeciwnym razie ten krok nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-139">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="4f2bc-140">Jeśli zmieniono adres podstawowy w kodzie, użyj zmodyfikowanego adres podstawowy w tym kroku.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-140">If you have changed the base address in the code, then use the modified base address in this step.</span></span>  
  
5.  <span data-ttu-id="4f2bc-141">Kliknij dwukrotnie **SayHello** w obszarze **Moje projekty usług** węzła.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-141">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="4f2bc-142">Wpisz nazwę w **wartość** kolumny w **żądania** listy, a następnie kliknij przycisk **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-142">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span> <span data-ttu-id="4f2bc-143">Zostanie wyświetlony komunikat odpowiedzi w **odpowiedzi** listy.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-143">A reply message appears in the **Response** list.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f2bc-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f2bc-144">Example</span></span>  
 <span data-ttu-id="4f2bc-145">Poniższy przykład tworzy <xref:System.ServiceModel.ServiceHost> obiektu do obsługi usługi typu `HelloWorldService`, a następnie wywołuje <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-145">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="4f2bc-146">Adres podstawowy jest zawarte w kodzie, publikowanie metadanych jest włączona i domyślne punkty końcowe są używane.</span><span class="sxs-lookup"><span data-stu-id="4f2bc-146">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4f2bc-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f2bc-147">See Also</span></span>  
 <xref:System.Uri>  
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  
 <xref:System.Configuration.ConfigurationManager>  
 [<span data-ttu-id="4f2bc-148">Instrukcje: hostowanie usługi WCF w programie IIS</span><span class="sxs-lookup"><span data-stu-id="4f2bc-148">How to: Host a WCF Service in IIS</span></span>](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [<span data-ttu-id="4f2bc-149">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="4f2bc-149">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="4f2bc-150">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="4f2bc-150">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="4f2bc-151">Instrukcje: definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="4f2bc-151">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="4f2bc-152">Instrukcje: implementowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="4f2bc-152">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="4f2bc-153">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="4f2bc-153">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="4f2bc-154">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="4f2bc-154">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="4f2bc-155">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="4f2bc-155">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
