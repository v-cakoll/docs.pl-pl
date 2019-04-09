---
title: 'Samouczek: Tworzenie klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: a16a0ccabfd0f9fbe69db1ea88d4613185f3c1da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174372"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="4a370-102">Samouczek: Tworzenie klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4a370-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="4a370-103">W tym samouczku opisano czwarty pięć zadania wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4a370-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="4a370-104">Aby zapoznać się z omówieniem samouczków, zobacz [samouczka: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="4a370-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="4a370-105">Następne zadanie do tworzenia aplikacji WCF jest można utworzyć klienta przez pobierania metadanych z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="4a370-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="4a370-106">Dodaj odwołanie do usługi, która pobiera metadane z punktu końcowego MEX usługi przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4a370-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="4a370-107">Program Visual Studio następnie generuje plik kodu źródłowego zarządzanych dla danego języka, który został wybrany serwer proxy klienta.</span><span class="sxs-lookup"><span data-stu-id="4a370-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="4a370-108">Tworzy również plik konfiguracji klienta (*App.config*).</span><span class="sxs-lookup"><span data-stu-id="4a370-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="4a370-109">Plik ten umożliwia aplikacji klienckiej nawiązać połączenie z usługą w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="4a370-109">This file enables the client application to connect to the service at an endpoint.</span></span> 

> [!NOTE]
> <span data-ttu-id="4a370-110">Jeśli usługa WCF jest wywoływana z projekt biblioteki klas w programie Visual Studio, użyj **Dodaj odwołanie do usługi** funkcji w celu automatycznego generowania serwera proxy i skojarzony plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4a370-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="4a370-111">Jednak ponieważ projekty bibliotek klas nie należy używać tego pliku konfiguracji, należy dodać ustawienia w pliku wygenerowaną konfigurację, aby *App.config* pliku dla pliku wykonywalnego, który wywołuje bibliotekę klas.</span><span class="sxs-lookup"><span data-stu-id="4a370-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="4a370-112">Alternatywnie użyj [ServiceModel metadanych narzędzie](#servicemodel-metadata-utility-tool) zamiast programu Visual Studio, aby wygenerować plik klasy i konfiguracji serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="4a370-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="4a370-113">Aplikacja kliencka używa klasy wygenerowany serwer proxy do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="4a370-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="4a370-114">Ta procedura jest opisana w [samouczka: Za pomocą klienta](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="4a370-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="4a370-115">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4a370-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="4a370-116">Utwórz i skonfiguruj projekt aplikacji konsoli dla klienta platformy WCF.</span><span class="sxs-lookup"><span data-stu-id="4a370-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="4a370-117">Dodaj odwołanie do usługi WCF do generowania plików klasy i konfiguracji serwera proxy usługi.</span><span class="sxs-lookup"><span data-stu-id="4a370-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="4a370-118">Tworzenie klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="4a370-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="4a370-119">Utwórz projekt aplikacji konsoli w programie Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="4a370-119">Create a console app project in Visual Studio:</span></span> 

    1. <span data-ttu-id="4a370-120">Z **pliku** menu, wybierz opcję **Otwórz** > **projekt/rozwiązanie** i przejdź do **GettingStarted** rozwiązania możesz wcześniej utworzony (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="4a370-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="4a370-121">Wybierz pozycję **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="4a370-121">Select **Open**.</span></span>

    2. <span data-ttu-id="4a370-122">Z **widoku** menu, wybierz opcję **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="4a370-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="4a370-123">W **Eksploratora rozwiązań** wybierz **GettingStarted** rozwiązania (najwyższy węzeł), a następnie wybierz **Dodaj** > **nowy projekt** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="4a370-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 
    
    4. <span data-ttu-id="4a370-124">W **Dodaj nowy projekt** oknie po lewej stronie wybierz **pulpitu Windows** kategorię w obszarze **Visual C#**  lub **języka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="4a370-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="4a370-125">Wybierz **Aplikacja konsoli (.NET Framework)** szablonu, a następnie wprowadź *GettingStartedClient* dla **nazwa**.</span><span class="sxs-lookup"><span data-stu-id="4a370-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="4a370-126">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="4a370-126">Select **OK**.</span></span>

2. <span data-ttu-id="4a370-127">Dodaj odwołanie w **GettingStartedClient** projekt <xref:System.ServiceModel> zestawu:</span><span class="sxs-lookup"><span data-stu-id="4a370-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1.  <span data-ttu-id="4a370-128">W **Eksploratora rozwiązań** wybierz **odwołania** folderze **GettingStartedClient** projektu, a następnie wybierz **Dodaj odwołanie** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="4a370-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="4a370-129">W **Dodaj odwołanie** okna, w obszarze **zestawy** w lewej części okna wybierz **Framework**.</span><span class="sxs-lookup"><span data-stu-id="4a370-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>
    
    3. <span data-ttu-id="4a370-130">Znajdź i zaznacz **System.ServiceModel**, a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="4a370-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> 

    4. <span data-ttu-id="4a370-131">Zapisz rozwiązanie, wybierając **pliku** > **Zapisz wszystko**.</span><span class="sxs-lookup"><span data-stu-id="4a370-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="4a370-132">Dodaj odwołanie do usługi z usługą Kalkulatora:</span><span class="sxs-lookup"><span data-stu-id="4a370-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="4a370-133">W **Eksploratora rozwiązań** wybierz **odwołania** folderze **GettingStartedClient** projektu, a następnie wybierz **Dodaj odwołanie do usługi**  z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="4a370-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="4a370-134">W **Dodaj odwołanie do usługi** wybierz **odnajdź**.</span><span class="sxs-lookup"><span data-stu-id="4a370-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="4a370-135">CalculatorService usługa zostanie uruchomiona i programu Visual Studio wyświetla go w **usług** pole.</span><span class="sxs-lookup"><span data-stu-id="4a370-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="4a370-136">Wybierz **CalculatorService** aby go rozwinąć i wyświetlić kontraktów usług implementowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="4a370-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="4a370-137">Pozostaw wartość domyślną **Namespace** i wybierz polecenie **OK**.</span><span class="sxs-lookup"><span data-stu-id="4a370-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="4a370-138">Program Visual Studio dodaje nowy element w obszarze **podłączone usługi** folderu w **GettingStartedClient** projektu.</span><span class="sxs-lookup"><span data-stu-id="4a370-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span> 

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="4a370-139">Narzędzie narzędzie metadanych elementu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4a370-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="4a370-140">W poniższych przykładach pokazano sposób użycia opcjonalnie [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) można wygenerować pliku klasy serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="4a370-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="4a370-141">To narzędzie generuje plik klasy serwera proxy i *App.config* pliku.</span><span class="sxs-lookup"><span data-stu-id="4a370-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="4a370-142">W poniższych przykładach pokazano sposób generowania serwera proxy w C# i Visual Basic, odpowiednio:</span><span class="sxs-lookup"><span data-stu-id="4a370-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="4a370-143">Plik konfiguracji klienta</span><span class="sxs-lookup"><span data-stu-id="4a370-143">Client configuration file</span></span>

<span data-ttu-id="4a370-144">Po utworzeniu klienta programu Visual Studio tworzy **App.config** plik konfiguracji w **GettingStartedClient** projektu, który powinien być podobny do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="4a370-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

<span data-ttu-id="4a370-145">W obszarze [ \<system.serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, zwróć uwagę, [ \<punktu końcowego >](../configure-apps/file-schema/wcf/endpoint-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="4a370-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="4a370-146">**&lt;Punktu końcowego&gt;** element definiuje punkt końcowy, który klient używa w celu uzyskania dostępu do usługi w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4a370-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>
- <span data-ttu-id="4a370-147">Adres: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="4a370-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="4a370-148">Adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4a370-148">The address of the endpoint.</span></span>
- <span data-ttu-id="4a370-149">Kontrakt usługi: `ServiceReference1.ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="4a370-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="4a370-150">Kontrakt usługi obsługuje komunikację między klienta platformy WCF a usługą.</span><span class="sxs-lookup"><span data-stu-id="4a370-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="4a370-151">Program Visual Studio generowany ten kontrakt użycia jej **Dodaj odwołanie do usługi** funkcji.</span><span class="sxs-lookup"><span data-stu-id="4a370-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="4a370-152">Jest zasadniczo kopią kontraktu, który zostały zdefiniowane w projekcie GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="4a370-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span> 
- <span data-ttu-id="4a370-153">Powiązanie: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="4a370-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="4a370-154">Powiązanie określa HTTP jako transportu, interoperacyjne zabezpieczeń i inne szczegóły konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4a370-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4a370-155">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4a370-155">Next steps</span></span>

<span data-ttu-id="4a370-156">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="4a370-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="4a370-157">Utwórz i skonfiguruj projekt aplikacji konsoli dla klienta platformy WCF.</span><span class="sxs-lookup"><span data-stu-id="4a370-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="4a370-158">Dodaj odwołanie do usługi WCF do generowania plików klasy i konfiguracji serwera proxy aplikacji klienckiej usługi.</span><span class="sxs-lookup"><span data-stu-id="4a370-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="4a370-159">Przejdź do następnego samouczka, aby dowiedzieć się, jak za pomocą wygenerowanego klienta.</span><span class="sxs-lookup"><span data-stu-id="4a370-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a370-160">Samouczek: Za pomocą klienta WCF</span><span class="sxs-lookup"><span data-stu-id="4a370-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
