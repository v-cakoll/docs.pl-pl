---
title: 'Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: e3adcad6ba70aa64b797325cd45a043301d7e680
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320977"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a><span data-ttu-id="996f7-102">Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="996f7-102">How to: Host a WCF service in a managed app</span></span>

<span data-ttu-id="996f7-103">Aby hostować usługę wewnątrz zarządzanej aplikacji, należy osadzić kod usługi w kodzie zarządzanej aplikacji, zdefiniować punkt końcowy usługi w sposób bezwzględny w kodzie, deklaratywnie za pośrednictwem konfiguracji lub użyć domyślnych punktów końcowych, a następnie utworzyć wystąpienie <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="996f7-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="996f7-104">Aby rozpocząć otrzymywanie komunikatów, wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> w <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="996f7-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="996f7-105">Spowoduje to utworzenie i otwarcie odbiornika dla usługi.</span><span class="sxs-lookup"><span data-stu-id="996f7-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="996f7-106">Hosting usługi w ten sposób jest często określany jako "hosting samodzielny", ponieważ zarządzana aplikacja wykonuje działania hostingowe.</span><span class="sxs-lookup"><span data-stu-id="996f7-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="996f7-107">Aby zamknąć usługę, wywołaj <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> w <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="996f7-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="996f7-108">Usługa może być również hostowana w usłudze zarządzanej systemu Windows, w Internet Information Services (IIS) lub w usłudze aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="996f7-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="996f7-109">Aby uzyskać więcej informacji na temat opcji hostingu dla usługi, zobacz [usługi hostingu](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="996f7-109">For more information about hosting options for a service, see [Hosting Services](hosting-services.md).</span></span>

<span data-ttu-id="996f7-110">Hostowanie usługi w aplikacji zarządzanej jest najbardziej elastyczną opcją, ponieważ wymaga ona najmniejszej infrastruktury do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="996f7-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="996f7-111">Aby uzyskać więcej informacji na temat usług hostingu w zarządzanych aplikacjach, zobacz [hosting w aplikacji zarządzanej](./feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="996f7-111">For more information about hosting services in managed applications, see [Hosting in a Managed Application](./feature-details/hosting-in-a-managed-application.md).</span></span>

<span data-ttu-id="996f7-112">Poniższa procedura przedstawia sposób implementacji usługi samodzielnej w aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="996f7-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>

## <a name="create-a-self-hosted-service"></a><span data-ttu-id="996f7-113">Tworzenie usługi samodzielnej</span><span class="sxs-lookup"><span data-stu-id="996f7-113">Create a self-hosted service</span></span>

1. <span data-ttu-id="996f7-114">Utwórz nową aplikację konsolową:</span><span class="sxs-lookup"><span data-stu-id="996f7-114">Create a new console application:</span></span>

   1. <span data-ttu-id="996f7-115">Otwórz program Visual Studio i wybierz pozycję **Nowy** **projekt**  >  z menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="996f7-115">Open Visual Studio and select **New** > **Project** from the **File** menu.</span></span>

   2. <span data-ttu-id="996f7-116">Na liście **zainstalowane szablony** wybierz pozycję **Visual C#**  lub **Visual Basic**, a następnie wybierz pozycję **Windows Desktop**.</span><span class="sxs-lookup"><span data-stu-id="996f7-116">In the **Installed Templates** list, select **Visual C#** or **Visual Basic**, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="996f7-117">Wybierz szablon **aplikacja konsoli** .</span><span class="sxs-lookup"><span data-stu-id="996f7-117">Select the **Console App** template.</span></span> <span data-ttu-id="996f7-118">Wpisz `SelfHost` w polu **Nazwa** , a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="996f7-118">Type `SelfHost` in the **Name** box and then choose **OK**.</span></span>

2. <span data-ttu-id="996f7-119">Kliknij prawym przyciskiem myszy pozycję **SelfHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="996f7-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="996f7-120">Wybierz **System. ServiceModel** z karty **.NET** , a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="996f7-120">Select **System.ServiceModel** from the **.NET** tab and then choose **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="996f7-121">Jeśli okno **Eksplorator rozwiązań** nie jest widoczne, wybierz pozycję **Eksplorator rozwiązań** z menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="996f7-121">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="996f7-122">Kliknij dwukrotnie pozycję **program.cs** lub **Module1. vb** w **Eksplorator rozwiązań** , aby otworzyć ją w oknie kodu, jeśli nie jest jeszcze otwarta.</span><span class="sxs-lookup"><span data-stu-id="996f7-122">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window, if it's not already open.</span></span> <span data-ttu-id="996f7-123">Dodaj następujące instrukcje w górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="996f7-123">Add the following statements at the top of the file:</span></span>

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. <span data-ttu-id="996f7-124">Zdefiniuj i zaimplementuj kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="996f7-124">Define and implement a service contract.</span></span> <span data-ttu-id="996f7-125">W tym przykładzie zdefiniowano `HelloWorldService`, która zwraca komunikat na podstawie danych wejściowych usługi.</span><span class="sxs-lookup"><span data-stu-id="996f7-125">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > <span data-ttu-id="996f7-126">Aby uzyskać więcej informacji na temat sposobu definiowania i implementowania interfejsu usługi, zobacz [How to: define a Service Contract](how-to-define-a-wcf-service-contract.md) and [How to: Implementuj kontrakt usługi](how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="996f7-126">For more information about how to define and implement a service interface, see [How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](how-to-implement-a-wcf-contract.md).</span></span>

5. <span data-ttu-id="996f7-127">W górnej części metody `Main` Utwórz wystąpienie klasy <xref:System.Uri> z adresem podstawowym usługi.</span><span class="sxs-lookup"><span data-stu-id="996f7-127">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <span data-ttu-id="996f7-128">Utwórz wystąpienie klasy <xref:System.ServiceModel.ServiceHost>, przekazując <xref:System.Type> reprezentujące typ usługi i adres podstawowy Uniform Resource Identifier (URI) do <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="996f7-128">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="996f7-129">Włącz Publikowanie metadanych, a następnie Wywołaj metodę <xref:System.ServiceModel.ICommunicationObject.Open%2A> na <xref:System.ServiceModel.ServiceHost> w celu zainicjowania usługi i przygotowania jej do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="996f7-129">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > <span data-ttu-id="996f7-130">W tym przykładzie są stosowane domyślne punkty końcowe i plik konfiguracji nie jest wymagany dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="996f7-130">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="996f7-131">Jeśli nie skonfigurowano żadnych punktów końcowych, środowisko uruchomieniowe tworzy jeden punkt końcowy dla każdego adresu podstawowego dla każdego kontraktu usługi zaimplementowanego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="996f7-131">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="996f7-132">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="996f7-132">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

7. <span data-ttu-id="996f7-133">Naciśnij **klawisze Ctrl**+**SHIFT**+**B** , aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="996f7-133">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="test-the-service"></a><span data-ttu-id="996f7-134">Testowanie usługi</span><span class="sxs-lookup"><span data-stu-id="996f7-134">Test the service</span></span>

1. <span data-ttu-id="996f7-135">Naciśnij **klawisze Ctrl**+**F5** , aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="996f7-135">Press **Ctrl**+**F5** to run the service.</span></span>

2. <span data-ttu-id="996f7-136">Otwórz **klienta testowego WCF**.</span><span class="sxs-lookup"><span data-stu-id="996f7-136">Open **WCF Test Client**.</span></span>

    > [!TIP]
    > <span data-ttu-id="996f7-137">Aby otworzyć **klienta testowego WCF**, Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio i wykonaj **WcfTestClient. exe**.</span><span class="sxs-lookup"><span data-stu-id="996f7-137">To open **WCF Test Client**, open Developer Command Prompt for Visual Studio and execute **WcfTestClient.exe**.</span></span>

3. <span data-ttu-id="996f7-138">Wybierz pozycję **Dodaj usługę** z menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="996f7-138">Select **Add Service** from the **File** menu.</span></span>

4. <span data-ttu-id="996f7-139">Wpisz `http://localhost:8080/hello` w polu adres i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="996f7-139">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="996f7-140">Upewnij się, że usługa jest uruchomiona, lub w przeciwnym razie ten krok nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="996f7-140">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="996f7-141">Jeśli zmieniono adres podstawowy w kodzie, należy użyć zmodyfikowanego adresu podstawowego w tym kroku.</span><span class="sxs-lookup"><span data-stu-id="996f7-141">If you have changed the base address in the code, then use the modified base address in this step.</span></span>

5. <span data-ttu-id="996f7-142">Kliknij dwukrotnie pozycję **sayHello** w węźle **Moje projekty usług** .</span><span class="sxs-lookup"><span data-stu-id="996f7-142">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="996f7-143">Wpisz swoją nazwę w kolumnie **wartość** na liście **żądanie** , a następnie kliknij pozycję **Wywołaj**.</span><span class="sxs-lookup"><span data-stu-id="996f7-143">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span>

   <span data-ttu-id="996f7-144">Na liście **odpowiedzi** zostanie wyświetlony komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="996f7-144">A reply message appears in the **Response** list.</span></span>

## <a name="example"></a><span data-ttu-id="996f7-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="996f7-145">Example</span></span>

<span data-ttu-id="996f7-146">Poniższy przykład tworzy obiekt <xref:System.ServiceModel.ServiceHost> w celu hostowania usługi typu `HelloWorldService`, a następnie wywołuje metodę <xref:System.ServiceModel.ICommunicationObject.Open%2A> w <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="996f7-146">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="996f7-147">Adres podstawowy jest podany w kodzie, funkcja publikowania metadanych jest włączona, a domyślne punkty końcowe są używane.</span><span class="sxs-lookup"><span data-stu-id="996f7-147">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="996f7-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="996f7-148">See also</span></span>

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [<span data-ttu-id="996f7-149">Instrukcje: hostowanie usługi WCF w programie IIS</span><span class="sxs-lookup"><span data-stu-id="996f7-149">How to: Host a WCF Service in IIS</span></span>](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [<span data-ttu-id="996f7-150">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="996f7-150">Self-Host</span></span>](./samples/self-host.md)
- [<span data-ttu-id="996f7-151">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="996f7-151">Hosting Services</span></span>](hosting-services.md)
- [<span data-ttu-id="996f7-152">Instrukcje: definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="996f7-152">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="996f7-153">Instrukcje: implementowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="996f7-153">How to: Implement a Service Contract</span></span>](how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="996f7-154">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="996f7-154">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="996f7-155">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="996f7-155">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="996f7-156">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="996f7-156">System-Provided Bindings</span></span>](system-provided-bindings.md)
