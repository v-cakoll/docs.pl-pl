---
title: 'Samouczek: Tworzenie klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: ddb5167c7f71a263377fb465ec44ee21057fbf4a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928902"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="02864-102">Samouczek: Tworzenie klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="02864-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="02864-103">W tym samouczku opisano czwarte pięć zadań wymaganych do utworzenia aplikacji podstawowej Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="02864-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="02864-104">Aby zapoznać się z omówieniem samouczków, [zobacz Samouczek: Rozpocznij pracę z aplikacjami](getting-started-tutorial.md)Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="02864-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="02864-105">Następnym zadaniem do tworzenia aplikacji WCF jest utworzenie klienta przez pobranie metadanych z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="02864-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="02864-106">Używasz programu Visual Studio, aby dodać odwołanie do usługi, które pobiera metadane z punktu końcowego MEX usługi.</span><span class="sxs-lookup"><span data-stu-id="02864-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="02864-107">Program Visual Studio generuje następnie zarządzany plik kodu źródłowego dla serwera proxy klienta w wybranym języku.</span><span class="sxs-lookup"><span data-stu-id="02864-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="02864-108">Tworzy również plik konfiguracji klienta (*App. config*).</span><span class="sxs-lookup"><span data-stu-id="02864-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="02864-109">Ten plik umożliwia aplikacji klienckiej łączenie się z usługą w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="02864-109">This file enables the client application to connect to the service at an endpoint.</span></span> 

> [!NOTE]
> <span data-ttu-id="02864-110">Jeśli wywołasz usługę WCF z projektu biblioteki klas w programie Visual Studio, użyj funkcji **Dodaj odwołanie do usługi** , aby automatycznie wygenerować serwer proxy i skojarzony plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="02864-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="02864-111">Jednak ponieważ projekty biblioteki klas nie korzystają z tego pliku konfiguracji, należy dodać ustawienia w wygenerowanym pliku konfiguracji do pliku *App. config* dla pliku wykonywalnego, który wywołuje bibliotekę klas.</span><span class="sxs-lookup"><span data-stu-id="02864-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="02864-112">Alternatywnie, aby wygenerować klasę i plik konfiguracji serwera proxy, użyj [Narzędzia metadanych ServiceModel](#servicemodel-metadata-utility-tool) zamiast programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="02864-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="02864-113">Aplikacja kliencka używa wygenerowanej klasy proxy do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="02864-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="02864-114">Ta procedura została opisana w [samouczku: Użyj klienta](how-to-use-a-wcf-client.md)programu.</span><span class="sxs-lookup"><span data-stu-id="02864-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="02864-115">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="02864-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="02864-116">Utwórz i skonfiguruj projekt aplikacji konsoli dla klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="02864-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="02864-117">Dodaj odwołanie do usługi do usługi WCF w celu wygenerowania klasy i plików konfiguracji serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="02864-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="02864-118">Tworzenie klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="02864-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="02864-119">Utwórz projekt aplikacji konsolowej w programie Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="02864-119">Create a console app project in Visual Studio:</span></span> 

    1. <span data-ttu-id="02864-120">Z menu **plik** wybierz pozycję **Otwórz** > **projekt/rozwiązanie** i przejdź do utworzonego wcześniej rozwiązania **GettingStarted** (*GettingStarted. sln*).</span><span class="sxs-lookup"><span data-stu-id="02864-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="02864-121">Wybierz pozycję **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="02864-121">Select **Open**.</span></span>

    2. <span data-ttu-id="02864-122">Z menu **Widok** wybierz pozycję **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="02864-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="02864-123">W oknie **Eksplorator rozwiązań** wybierz rozwiązanie **GettingStarted** (górny węzeł), a następnie wybierz pozycję **Dodaj** > **Nowy projekt** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="02864-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 
    
    4. <span data-ttu-id="02864-124">W oknie **Dodaj nowy projekt** po lewej stronie wybierz kategorię **pulpit systemu Windows** w obszarze **Wizualizacja C#**  lub **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="02864-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="02864-125">Wybierz szablon **aplikacja konsoli (.NET Framework)** , a następnie wprowadź *GettingStartedClient* jako **nazwę**.</span><span class="sxs-lookup"><span data-stu-id="02864-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="02864-126">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="02864-126">Select **OK**.</span></span>

2. <span data-ttu-id="02864-127">Dodaj odwołanie do <xref:System.ServiceModel> zestawu w projekcie **GettingStartedClient** :</span><span class="sxs-lookup"><span data-stu-id="02864-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="02864-128">W oknie **Eksplorator rozwiązań** wybierz folder **odwołania** w projekcie **GettingStartedClient** , a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="02864-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="02864-129">W oknie **Dodaj odwołanie** w obszarze **zestawy** po lewej stronie okna wybierz pozycję **Struktura**.</span><span class="sxs-lookup"><span data-stu-id="02864-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>
    
    3. <span data-ttu-id="02864-130">Znajdź i wybierz **System. ServiceModel**, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="02864-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> 

    4. <span data-ttu-id="02864-131">Zapisz rozwiązanie, wybierając kolejno pozycje **plik** > **Zapisz wszystko**.</span><span class="sxs-lookup"><span data-stu-id="02864-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="02864-132">Dodaj odwołanie do usługi kalkulatora:</span><span class="sxs-lookup"><span data-stu-id="02864-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="02864-133">W oknie **Eksplorator rozwiązań** wybierz folder **odwołania** w projekcie **GettingStartedClient** , a następnie wybierz pozycję **Dodaj odwołanie do usługi** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="02864-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="02864-134">W oknie **Dodaj odwołanie do usługi** wybierz pozycję **odkryj**.</span><span class="sxs-lookup"><span data-stu-id="02864-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="02864-135">Zostanie uruchomiona usługa CalculatorService, a program Visual Studio wyświetli go w polu **usługi** .</span><span class="sxs-lookup"><span data-stu-id="02864-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="02864-136">Wybierz pozycję **CalculatorService** , aby ją rozwinąć i wyświetlić kontrakty usługi zaimplementowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="02864-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="02864-137">Pozostaw domyślną **przestrzeń nazw** i wybierz **przycisk OK**.</span><span class="sxs-lookup"><span data-stu-id="02864-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="02864-138">Program Visual Studio dodaje nowy element w folderze **usługi połączone** w projekcie **GettingStartedClient** .</span><span class="sxs-lookup"><span data-stu-id="02864-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span> 

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="02864-139">Narzędzie do przesyłania metadanych ServiceModel</span><span class="sxs-lookup"><span data-stu-id="02864-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="02864-140">W poniższych przykładach pokazano, jak opcjonalnie użyć [Narzędzia metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) do wygenerowania pliku klasy proxy.</span><span class="sxs-lookup"><span data-stu-id="02864-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="02864-141">To narzędzie generuje plik klasy serwera proxy i plik *App. config* .</span><span class="sxs-lookup"><span data-stu-id="02864-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="02864-142">W poniższych przykładach pokazano, jak wygenerować serwer proxy C# w i Visual Basic odpowiednio:</span><span class="sxs-lookup"><span data-stu-id="02864-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="02864-143">Plik konfiguracji klienta</span><span class="sxs-lookup"><span data-stu-id="02864-143">Client configuration file</span></span>

<span data-ttu-id="02864-144">Po utworzeniu klienta program Visual Studio tworzy plik konfiguracji **App. config** w projekcie **GettingStartedClient** , który powinien być podobny do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="02864-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="02864-145">W sekcji [ \<](../configure-apps/file-schema/wcf/endpoint-element.md) system. [ServiceModel > Zwróć uwagę na element Endpoint >. \<](../configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="02864-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="02864-146">Element **Endpoint&gt;definiuje punkt końcowy, którego klient używa do uzyskiwania dostępu do usługi w następujący sposób: &lt;**</span><span class="sxs-lookup"><span data-stu-id="02864-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="02864-147">Adres: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="02864-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="02864-148">Adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="02864-148">The address of the endpoint.</span></span>
- <span data-ttu-id="02864-149">Kontrakt usługi: `ServiceReference1.ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="02864-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="02864-150">Kontrakt usługi obsługuje komunikację między klientem programu WCF a usługą.</span><span class="sxs-lookup"><span data-stu-id="02864-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="02864-151">Program Visual Studio wygenerował ten kontrakt, gdy użyto funkcji **Dodaj odwołanie do usługi** .</span><span class="sxs-lookup"><span data-stu-id="02864-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="02864-152">Zasadniczo jest to kopia kontraktu, która została zdefiniowana w projekcie GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="02864-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span> 
- <span data-ttu-id="02864-153">Powiązanie: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="02864-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="02864-154">Powiązanie określa protokół HTTP jako Transport, zabezpieczenia interoperacyjności i inne szczegóły konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="02864-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="02864-155">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="02864-155">Next steps</span></span>

<span data-ttu-id="02864-156">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="02864-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="02864-157">Utwórz i skonfiguruj projekt aplikacji konsoli dla klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="02864-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="02864-158">Dodaj odwołanie do usługi do usługi WCF w celu wygenerowania klasy serwera proxy i plików konfiguracji dla aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="02864-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="02864-159">Przejdź do następnego samouczka, aby dowiedzieć się, jak korzystać z wygenerowanego klienta.</span><span class="sxs-lookup"><span data-stu-id="02864-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02864-160">Samouczek: Korzystanie z klienta WCF</span><span class="sxs-lookup"><span data-stu-id="02864-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
