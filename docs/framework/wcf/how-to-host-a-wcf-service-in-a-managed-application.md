---
title: 'Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: 131d99457427e0818f78076d987f550a99ad7cf0
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46696309"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a><span data-ttu-id="8e31f-102">Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="8e31f-102">How to: Host a WCF service in a managed app</span></span>

<span data-ttu-id="8e31f-103">Aby hostować usługi w ramach zarządzaną aplikację, Osadź kod dla usługi w kodzie aplikacji zarządzanej, albo obowiązkowo w kodzie, w sposób deklaratywny za pośrednictwem konfiguracji lub przy użyciu domyślnych punktów końcowych, definiowanie punktu końcowego usługi, a następnie utwórz wystąpienie <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8e31f-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="8e31f-104">Aby rozpocząć odbieranie komunikatów, należy wywołać <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8e31f-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="8e31f-105">Umożliwia utworzenie i otwiera odbiornika dla usługi.</span><span class="sxs-lookup"><span data-stu-id="8e31f-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="8e31f-106">Usługi w ten sposób hostingu często nazywa się "hostingu samodzielnego", ponieważ aplikacja zarządzana wykonuje utwór hostingu.</span><span class="sxs-lookup"><span data-stu-id="8e31f-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="8e31f-107">Aby zamknąć tę usługę, należy wywołać <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8e31f-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="8e31f-108">Usługa może też być hostowana w zarządzanych usług Windows, w Internet Information Services (IIS) lub w Windows Process Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="8e31f-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="8e31f-109">Aby uzyskać więcej informacji na temat opcji usługi hostingu, zobacz [usług obsługującego](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="8e31f-109">For more information about hosting options for a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>

<span data-ttu-id="8e31f-110">Usługi w zarządzanej aplikacji hosta jest najbardziej elastyczna opcja, ponieważ wymaga co najmniej infrastruktury do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="8e31f-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="8e31f-111">Aby uzyskać więcej informacji o hostingu usług w zarządzanych aplikacjach, zobacz [hostowanie w aplikacji Managed](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="8e31f-111">For more information about hosting services in managed applications, see [Hosting in a Managed Application](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

<span data-ttu-id="8e31f-112">Poniższa procedura demonstruje sposób implementacji usługi samodzielnie hostowanej w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="8e31f-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>

## <a name="create-a-self-hosted-service"></a><span data-ttu-id="8e31f-113">Tworzenie własnego usługi</span><span class="sxs-lookup"><span data-stu-id="8e31f-113">Create a self-hosted service</span></span>

1. <span data-ttu-id="8e31f-114">Utwórz nową aplikację konsoli:</span><span class="sxs-lookup"><span data-stu-id="8e31f-114">Create a new console application:</span></span>

   1. <span data-ttu-id="8e31f-115">Otwórz program Visual Studio i wybierz **New** > **projektu** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="8e31f-115">Open Visual Studio and select **New** > **Project** from the **File** menu.</span></span>

   2. <span data-ttu-id="8e31f-116">W **zainstalowane szablony** listy wybierz **Visual C#** lub **języka Visual Basic**, a następnie wybierz pozycję **pulpitu Windows**.</span><span class="sxs-lookup"><span data-stu-id="8e31f-116">In the **Installed Templates** list, select **Visual C#** or **Visual Basic**, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="8e31f-117">Wybierz **aplikacja Konsolowa** szablonu.</span><span class="sxs-lookup"><span data-stu-id="8e31f-117">Select the **Console App** template.</span></span> <span data-ttu-id="8e31f-118">Typ `SelfHost` w **nazwa** pole, a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e31f-118">Type `SelfHost` in the **Name** box and then choose **OK**.</span></span>

2. <span data-ttu-id="8e31f-119">Kliknij prawym przyciskiem myszy **host własny** w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="8e31f-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="8e31f-120">Wybierz **System.ServiceModel** z **.NET** kartę, a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e31f-120">Select **System.ServiceModel** from the **.NET** tab and then choose **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="8e31f-121">Jeśli **Eksploratora rozwiązań** okno nie jest widoczny, wybierz opcję **Eksploratora rozwiązań** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="8e31f-121">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="8e31f-122">Kliknij dwukrotnie **Program.cs** lub **Module1.vb** w **Eksploratora rozwiązań** aby otworzyć go w oknie kodu, jeśli nie jest jeszcze otwarty.</span><span class="sxs-lookup"><span data-stu-id="8e31f-122">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window, if it's not already open.</span></span> <span data-ttu-id="8e31f-123">Dodaj następujące instrukcje w górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="8e31f-123">Add the following statements at the top of the file:</span></span>

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. <span data-ttu-id="8e31f-124">Definiowanie i implementowanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="8e31f-124">Define and implement a service contract.</span></span> <span data-ttu-id="8e31f-125">Ten przykład definiuje `HelloWorldService` , zwraca komunikat na podstawie danych wejściowych do usługi.</span><span class="sxs-lookup"><span data-stu-id="8e31f-125">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > <span data-ttu-id="8e31f-126">Aby uzyskać więcej informacji o tym, jak definiować ani implementować interfejsu usługi, zobacz [porady: definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) i [porady: Implementowanie kontraktu usługi](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="8e31f-126">For more information about how to define and implement a service interface, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span></span>

5. <span data-ttu-id="8e31f-127">W górnej części `Main` metody, Utwórz wystąpienie obiektu <xref:System.Uri> klasy przy użyciu podstawowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="8e31f-127">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <span data-ttu-id="8e31f-128">Utwórz wystąpienie obiektu <xref:System.ServiceModel.ServiceHost> klasy, przekazując <xref:System.Type> który reprezentuje typ usługi, a podstawą adresu identyfikator (URI) do <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="8e31f-128">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="8e31f-129">Włączanie publikowania metadanych, a następnie wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody <xref:System.ServiceModel.ServiceHost> do inicjowania usługi i przygotować je do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8e31f-129">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > <span data-ttu-id="8e31f-130">W tym przykładzie użyto domyślnych punktów końcowych, a plik konfiguracji nie jest wymagana dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8e31f-130">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="8e31f-131">Jeśli punkty końcowe nie są skonfigurowane, środowisko uruchomieniowe tworzy jeden punkt końcowy dla każdego adresu podstawowego dla każdej umowy serwisowej implementowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="8e31f-131">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="8e31f-132">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="8e31f-132">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

7. <span data-ttu-id="8e31f-133">Naciśnij klawisz **Ctrl**+**Shift**+**B** do skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="8e31f-133">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="test-the-service"></a><span data-ttu-id="8e31f-134">Testowanie usługi</span><span class="sxs-lookup"><span data-stu-id="8e31f-134">Test the service</span></span>

1. <span data-ttu-id="8e31f-135">Naciśnij klawisz **Ctrl**+**F5** do uruchamiania usługi.</span><span class="sxs-lookup"><span data-stu-id="8e31f-135">Press **Ctrl**+**F5** to run the service.</span></span>

2. <span data-ttu-id="8e31f-136">Otwórz **klienta testowego WCF**.</span><span class="sxs-lookup"><span data-stu-id="8e31f-136">Open **WCF Test Client**.</span></span>

    > [!TIP]
    > <span data-ttu-id="8e31f-137">Aby otworzyć **klienta testowego WCF**, otwórz wiersz polecenia dla deweloperów programu Visual Studio i wykonywanie **WcfTestClient.exe**.</span><span class="sxs-lookup"><span data-stu-id="8e31f-137">To open **WCF Test Client**, open Developer Command Prompt for Visual Studio and execute **WcfTestClient.exe**.</span></span>

3. <span data-ttu-id="8e31f-138">Wybierz **Dodaj usługę** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="8e31f-138">Select **Add Service** from the **File** menu.</span></span>

4. <span data-ttu-id="8e31f-139">Typ `http://localhost:8080/hello` w polu adresu i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e31f-139">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="8e31f-140">Upewnij się, że usługa jest uruchomiona. w przeciwnym razie ten krok zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8e31f-140">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="8e31f-141">Jeśli zmienisz adres podstawowy w kodzie, użyj zmodyfikowany adres podstawowy, w tym kroku.</span><span class="sxs-lookup"><span data-stu-id="8e31f-141">If you have changed the base address in the code, then use the modified base address in this step.</span></span>

5. <span data-ttu-id="8e31f-142">Kliknij dwukrotnie **SayHello** w obszarze **Moje projekty usług** węzła.</span><span class="sxs-lookup"><span data-stu-id="8e31f-142">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="8e31f-143">Wpisz nazwę w **wartość** kolumny w **żądania** listy, a następnie kliknij przycisk **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="8e31f-143">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span>

   <span data-ttu-id="8e31f-144">W odpowiedzi zostanie wyświetlony komunikat **odpowiedzi** listy.</span><span class="sxs-lookup"><span data-stu-id="8e31f-144">A reply message appears in the **Response** list.</span></span>

## <a name="example"></a><span data-ttu-id="8e31f-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e31f-145">Example</span></span>

<span data-ttu-id="8e31f-146">Poniższy przykład tworzy <xref:System.ServiceModel.ServiceHost> obiektu do hostowania usługi typu `HelloWorldService`, a następnie wywołuje <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody w <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8e31f-146">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="8e31f-147">Adres podstawowy jest zawarte w kodzie, włączono publikowanie metadanych i domyślne punkty końcowe są używane.</span><span class="sxs-lookup"><span data-stu-id="8e31f-147">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="8e31f-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e31f-148">See also</span></span>

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [<span data-ttu-id="8e31f-149">Instrukcje: hostowanie usługi WCF w programie IIS</span><span class="sxs-lookup"><span data-stu-id="8e31f-149">How to: Host a WCF Service in IIS</span></span>](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [<span data-ttu-id="8e31f-150">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="8e31f-150">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="8e31f-151">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="8e31f-151">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="8e31f-152">Instrukcje: definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="8e31f-152">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="8e31f-153">Instrukcje: implementowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="8e31f-153">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="8e31f-154">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="8e31f-154">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="8e31f-155">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="8e31f-155">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="8e31f-156">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="8e31f-156">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)