---
title: 'Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji'
description: Dowiedz się, jak hostować usługę WCF w zarządzanej aplikacji przez utworzenie samohostowanej usługi i przetestowanie jej.
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: 7d1d61b683f60a6c643d2a2f03d367a6ae6c6c15
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246171"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a><span data-ttu-id="dbc05-103">Instrukcje: Hostowanie usługi WCF w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="dbc05-103">How to: Host a WCF service in a managed app</span></span>

<span data-ttu-id="dbc05-104">Aby hostować usługę wewnątrz zarządzanej aplikacji, należy osadzić kod usługi w kodzie zarządzanej aplikacji, zdefiniować punkt końcowy usługi w sposób bezwzględny w kodzie, deklaratywnie za pośrednictwem konfiguracji lub użyć domyślnych punktów końcowych, a następnie utworzyć wystąpienie <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="dbc05-104">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="dbc05-105">Aby rozpocząć otrzymywanie komunikatów, wywołaj polecenie <xref:System.ServiceModel.ICommunicationObject.Open%2A> <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="dbc05-105">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="dbc05-106">Spowoduje to utworzenie i otwarcie odbiornika dla usługi.</span><span class="sxs-lookup"><span data-stu-id="dbc05-106">This creates and opens the listener for the service.</span></span> <span data-ttu-id="dbc05-107">Hosting usługi w ten sposób jest często określany jako "hosting samodzielny", ponieważ zarządzana aplikacja wykonuje działania hostingowe.</span><span class="sxs-lookup"><span data-stu-id="dbc05-107">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="dbc05-108">Aby zamknąć usługę, wywołaj <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> polecenie <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="dbc05-108">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="dbc05-109">Usługa może być również hostowana w usłudze zarządzanej systemu Windows, w Internet Information Services (IIS) lub w usłudze aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="dbc05-109">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="dbc05-110">Aby uzyskać więcej informacji na temat opcji hostingu dla usługi, zobacz [usługi hostingu](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="dbc05-110">For more information about hosting options for a service, see [Hosting Services](hosting-services.md).</span></span>

<span data-ttu-id="dbc05-111">Hostowanie usługi w aplikacji zarządzanej jest najbardziej elastyczną opcją, ponieważ wymaga ona najmniejszej infrastruktury do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="dbc05-111">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="dbc05-112">Aby uzyskać więcej informacji na temat usług hostingu w zarządzanych aplikacjach, zobacz [hosting w aplikacji zarządzanej](./feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="dbc05-112">For more information about hosting services in managed applications, see [Hosting in a Managed Application](./feature-details/hosting-in-a-managed-application.md).</span></span>

<span data-ttu-id="dbc05-113">Poniższa procedura przedstawia sposób implementacji usługi samodzielnej w aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="dbc05-113">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>

## <a name="create-a-self-hosted-service"></a><span data-ttu-id="dbc05-114">Tworzenie usługi samodzielnej</span><span class="sxs-lookup"><span data-stu-id="dbc05-114">Create a self-hosted service</span></span>

1. <span data-ttu-id="dbc05-115">Utwórz nową aplikację konsolową:</span><span class="sxs-lookup"><span data-stu-id="dbc05-115">Create a new console application:</span></span>

   1. <span data-ttu-id="dbc05-116">Otwórz program Visual Studio i wybierz pozycję **Nowy**  >  **projekt** z menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="dbc05-116">Open Visual Studio and select **New** > **Project** from the **File** menu.</span></span>

   2. <span data-ttu-id="dbc05-117">Na liście **zainstalowane szablony** wybierz pozycję **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **Windows Desktop**.</span><span class="sxs-lookup"><span data-stu-id="dbc05-117">In the **Installed Templates** list, select **Visual C#** or **Visual Basic**, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="dbc05-118">Wybierz szablon **aplikacja konsoli** .</span><span class="sxs-lookup"><span data-stu-id="dbc05-118">Select the **Console App** template.</span></span> <span data-ttu-id="dbc05-119">Wpisz `SelfHost` w polu **Nazwa** , a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="dbc05-119">Type `SelfHost` in the **Name** box and then choose **OK**.</span></span>

2. <span data-ttu-id="dbc05-120">Kliknij prawym przyciskiem myszy pozycję **SelfHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="dbc05-120">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="dbc05-121">Wybierz **System. ServiceModel** z karty **.NET** , a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="dbc05-121">Select **System.ServiceModel** from the **.NET** tab and then choose **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="dbc05-122">Jeśli okno **Eksplorator rozwiązań** nie jest widoczne, wybierz pozycję **Eksplorator rozwiązań** z menu **Widok** .</span><span class="sxs-lookup"><span data-stu-id="dbc05-122">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="dbc05-123">Kliknij dwukrotnie pozycję **program.cs** lub **Module1. vb** w **Eksplorator rozwiązań** , aby otworzyć ją w oknie kodu, jeśli nie jest jeszcze otwarta.</span><span class="sxs-lookup"><span data-stu-id="dbc05-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window, if it's not already open.</span></span> <span data-ttu-id="dbc05-124">Dodaj następujące instrukcje w górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="dbc05-124">Add the following statements at the top of the file:</span></span>

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. <span data-ttu-id="dbc05-125">Zdefiniuj i zaimplementuj kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="dbc05-125">Define and implement a service contract.</span></span> <span data-ttu-id="dbc05-126">Ten przykład definiuje `HelloWorldService` , która zwraca komunikat na podstawie danych wejściowych usługi.</span><span class="sxs-lookup"><span data-stu-id="dbc05-126">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > <span data-ttu-id="dbc05-127">Aby uzyskać więcej informacji na temat sposobu definiowania i implementowania interfejsu usługi, zobacz [How to: define a Service Contract](how-to-define-a-wcf-service-contract.md) and [How to: Implementuj kontrakt usługi](how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="dbc05-127">For more information about how to define and implement a service interface, see [How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](how-to-implement-a-wcf-contract.md).</span></span>

5. <span data-ttu-id="dbc05-128">W górnej części `Main` metody Utwórz wystąpienie <xref:System.Uri> klasy z adresem podstawowym dla usługi.</span><span class="sxs-lookup"><span data-stu-id="dbc05-128">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <span data-ttu-id="dbc05-129">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy, przekazując element <xref:System.Type> reprezentujący typ usługi i adres podstawowy Uniform Resource Identifier (URI) do <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29> .</span><span class="sxs-lookup"><span data-stu-id="dbc05-129">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="dbc05-130">Włącz Publikowanie metadanych, a następnie Wywołaj <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodę w <xref:System.ServiceModel.ServiceHost> celu zainicjowania usługi i przygotuj ją do odbierania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="dbc05-130">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > <span data-ttu-id="dbc05-131">W tym przykładzie są stosowane domyślne punkty końcowe i plik konfiguracji nie jest wymagany dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="dbc05-131">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="dbc05-132">Jeśli nie skonfigurowano żadnych punktów końcowych, środowisko uruchomieniowe tworzy jeden punkt końcowy dla każdego adresu podstawowego dla każdego kontraktu usługi zaimplementowanego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="dbc05-132">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="dbc05-133">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="dbc05-133">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

7. <span data-ttu-id="dbc05-134">Naciśnij **klawisze CTRL** + **SHIFT** + **B** , aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="dbc05-134">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="test-the-service"></a><span data-ttu-id="dbc05-135">Testowanie usługi</span><span class="sxs-lookup"><span data-stu-id="dbc05-135">Test the service</span></span>

1. <span data-ttu-id="dbc05-136">Naciśnij klawisz **Ctrl** + **F5** , aby uruchomić usługę.</span><span class="sxs-lookup"><span data-stu-id="dbc05-136">Press **Ctrl**+**F5** to run the service.</span></span>

2. <span data-ttu-id="dbc05-137">Otwórz **klienta testowego WCF**.</span><span class="sxs-lookup"><span data-stu-id="dbc05-137">Open **WCF Test Client**.</span></span>

    > [!TIP]
    > <span data-ttu-id="dbc05-138">Aby otworzyć **klienta testowego WCF**, Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio i wykonaj **WcfTestClient.exe**.</span><span class="sxs-lookup"><span data-stu-id="dbc05-138">To open **WCF Test Client**, open Developer Command Prompt for Visual Studio and execute **WcfTestClient.exe**.</span></span>

3. <span data-ttu-id="dbc05-139">Wybierz pozycję **Dodaj usługę** z menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="dbc05-139">Select **Add Service** from the **File** menu.</span></span>

4. <span data-ttu-id="dbc05-140">Wpisz tekst `http://localhost:8080/hello` w polu adres i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="dbc05-140">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="dbc05-141">Upewnij się, że usługa jest uruchomiona, lub w przeciwnym razie ten krok nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="dbc05-141">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="dbc05-142">Jeśli zmieniono adres podstawowy w kodzie, należy użyć zmodyfikowanego adresu podstawowego w tym kroku.</span><span class="sxs-lookup"><span data-stu-id="dbc05-142">If you have changed the base address in the code, then use the modified base address in this step.</span></span>

5. <span data-ttu-id="dbc05-143">Kliknij dwukrotnie pozycję **sayHello** w węźle **Moje projekty usług** .</span><span class="sxs-lookup"><span data-stu-id="dbc05-143">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="dbc05-144">Wpisz swoją nazwę w kolumnie **wartość** na liście **żądanie** , a następnie kliknij pozycję **Wywołaj**.</span><span class="sxs-lookup"><span data-stu-id="dbc05-144">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span>

   <span data-ttu-id="dbc05-145">Na liście **odpowiedzi** zostanie wyświetlony komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="dbc05-145">A reply message appears in the **Response** list.</span></span>

## <a name="example"></a><span data-ttu-id="dbc05-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="dbc05-146">Example</span></span>

<span data-ttu-id="dbc05-147">Poniższy przykład tworzy <xref:System.ServiceModel.ServiceHost> obiekt do hostowania usługi typu `HelloWorldService` , a następnie wywołuje <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodę w <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="dbc05-147">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="dbc05-148">Adres podstawowy jest podany w kodzie, funkcja publikowania metadanych jest włączona, a domyślne punkty końcowe są używane.</span><span class="sxs-lookup"><span data-stu-id="dbc05-148">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="dbc05-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dbc05-149">See also</span></span>

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [<span data-ttu-id="dbc05-150">Instrukcje: hostowanie usługi WCF w programie IIS</span><span class="sxs-lookup"><span data-stu-id="dbc05-150">How to: Host a WCF Service in IIS</span></span>](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [<span data-ttu-id="dbc05-151">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="dbc05-151">Self-Host</span></span>](./samples/self-host.md)
- [<span data-ttu-id="dbc05-152">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="dbc05-152">Hosting Services</span></span>](hosting-services.md)
- [<span data-ttu-id="dbc05-153">Instrukcje: definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="dbc05-153">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="dbc05-154">Instrukcje: implementowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="dbc05-154">How to: Implement a Service Contract</span></span>](how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="dbc05-155">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="dbc05-155">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="dbc05-156">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="dbc05-156">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="dbc05-157">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="dbc05-157">System-Provided Bindings</span></span>](system-provided-bindings.md)
