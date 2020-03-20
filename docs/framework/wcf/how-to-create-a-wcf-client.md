---
title: 'Samouczek: Tworzenie klienta programu Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184103"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="03da9-102">Samouczek: Tworzenie klienta programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="03da9-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="03da9-103">W tym samouczku opisano czwarte z pięciu zadań wymaganych do utworzenia podstawowej aplikacji Programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="03da9-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="03da9-104">Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Wprowadzenie do aplikacji Programu Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="03da9-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="03da9-105">Następnym zadaniem tworzenia aplikacji WCF jest utworzenie klienta przez pobieranie metadanych z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="03da9-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="03da9-106">Za pomocą programu Visual Studio, aby dodać odwołanie do usługi, która pobiera metadane z punktu końcowego MEX usługi.</span><span class="sxs-lookup"><span data-stu-id="03da9-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="03da9-107">Visual Studio następnie generuje plik kodu źródłowego zarządzanego serwera proxy klienta w wybranym języku.</span><span class="sxs-lookup"><span data-stu-id="03da9-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="03da9-108">Tworzy również plik konfiguracji klienta (*App.config*).</span><span class="sxs-lookup"><span data-stu-id="03da9-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="03da9-109">Ten plik umożliwia aplikacji klienckiej połączyć się z usługą w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="03da9-109">This file enables the client application to connect to the service at an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="03da9-110">Jeśli wywołujesz usługę WCF z projektu biblioteki klas w programie Visual Studio, użyj funkcji Dodaj odwołanie do **usługi,** aby automatycznie wygenerować serwer proxy i skojarzony plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="03da9-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="03da9-111">Ponieważ jednak projekty bibliotek klas nie używają tego pliku konfiguracyjnego, należy dodać ustawienia w wygenerowanym pliku konfiguracyjnym do pliku *App.config* dla pliku wykonywalnego, który wywołuje bibliotekę klas.</span><span class="sxs-lookup"><span data-stu-id="03da9-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="03da9-112">Alternatywnie użyj [narzędzia Narzędzia Metadata ServiceModel](#servicemodel-metadata-utility-tool) zamiast programu Visual Studio do wygenerowania klasy serwera proxy i pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="03da9-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="03da9-113">Aplikacja kliencka używa wygenerowanej klasy proxy do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="03da9-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="03da9-114">Ta procedura jest [opisana w samouczku: Użyj klienta](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="03da9-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="03da9-115">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="03da9-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="03da9-116">Tworzenie i konfigurowanie projektu aplikacji konsoli dla klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="03da9-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="03da9-117">Dodaj odwołanie do usługi WCF do generowania klasy serwera proxy i plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="03da9-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="03da9-118">Tworzenie klienta programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="03da9-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="03da9-119">Tworzenie projektu aplikacji konsoli w programie Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="03da9-119">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="03da9-120">Z menu **Plik** wybierz polecenie **Otwórz** > **projekt/rozwiązanie** i przejdź do utworzonego wcześniej rozwiązania **GettingStarted** (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="03da9-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="03da9-121">Wybierz pozycję **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="03da9-121">Select **Open**.</span></span>

    2. <span data-ttu-id="03da9-122">Z menu **Widok** wybierz pozycję **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="03da9-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="03da9-123">W oknie **Eksplorator rozwiązań** wybierz rozwiązanie GettingStarted (węzeł **górny),** a następnie z menu skrótów wybierz polecenie **Dodaj** > **nowy projekt.**</span><span class="sxs-lookup"><span data-stu-id="03da9-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="03da9-124">W oknie **Dodaj nowy projekt** po lewej stronie wybierz kategorię Pulpit systemu **Windows** w obszarze **Visual C#** lub **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="03da9-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="03da9-125">Wybierz szablon **Aplikacji konsoli (.NET Framework)** i wprowadź *pozycję GettingStartedClient* dla **nazwy**.</span><span class="sxs-lookup"><span data-stu-id="03da9-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="03da9-126">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="03da9-126">Select **OK**.</span></span>

2. <span data-ttu-id="03da9-127">Dodaj odwołanie w projekcie **GettingStartedClient** do <xref:System.ServiceModel> zestawu:</span><span class="sxs-lookup"><span data-stu-id="03da9-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="03da9-128">W oknie **Eksplorator rozwiązań** wybierz folder **Odwołania** w obszarze projektu **GettingStartedClient,** a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="03da9-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="03da9-129">W oknie **Dodaj odwołanie** w obszarze **Zestawy** po lewej stronie okna wybierz pozycję **Framework**.</span><span class="sxs-lookup"><span data-stu-id="03da9-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="03da9-130">Znajdź i wybierz **system.ServiceModel**, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="03da9-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span>

    4. <span data-ttu-id="03da9-131">Zapisz rozwiązanie, wybierając **pozycję Zapisz** > **wszystkie**pliki .</span><span class="sxs-lookup"><span data-stu-id="03da9-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="03da9-132">Dodaj odwołanie do usługi kalkulatora:</span><span class="sxs-lookup"><span data-stu-id="03da9-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="03da9-133">W oknie **Eksplorator rozwiązań** wybierz folder **Odwołania** w ramach projektu **GettingStartedClient,** a następnie wybierz polecenie **Dodaj odwołanie do usługi** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="03da9-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="03da9-134">W oknie **Dodawanie odwołania do usługi** wybierz pozycję **Odnajduj**.</span><span class="sxs-lookup"><span data-stu-id="03da9-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="03da9-135">Uruchomi się usługa CalculatorService, a program Visual Studio wyświetli ją w polu **Usługi.**</span><span class="sxs-lookup"><span data-stu-id="03da9-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="03da9-136">Wybierz **CalculatorService,** aby ją rozwinąć i wyświetlić umowy serwisowe zaimplementowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="03da9-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="03da9-137">Pozostaw domyślny **obszar nazw** i wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="03da9-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="03da9-138">Program Visual Studio dodaje nowy element w folderze **Połączone usługi** w projekcie **GettingStartedClient.**</span><span class="sxs-lookup"><span data-stu-id="03da9-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span>

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="03da9-139">Narzędzie narzędzia Metadata usługi ServiceModel</span><span class="sxs-lookup"><span data-stu-id="03da9-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="03da9-140">Poniższe przykłady pokazują, jak opcjonalnie użyć [narzędzia ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania pliku klasy proxy.</span><span class="sxs-lookup"><span data-stu-id="03da9-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="03da9-141">To narzędzie generuje plik klasy proxy i plik *App.config.*</span><span class="sxs-lookup"><span data-stu-id="03da9-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="03da9-142">Poniższe przykłady pokazują, jak wygenerować serwer proxy w języku C# i Visual Basic, odpowiednio:</span><span class="sxs-lookup"><span data-stu-id="03da9-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="03da9-143">Plik konfiguracji klienta</span><span class="sxs-lookup"><span data-stu-id="03da9-143">Client configuration file</span></span>

<span data-ttu-id="03da9-144">Po utworzeniu klienta program Visual Studio tworzy plik konfiguracyjny **App.config** w projekcie **GettingStartedClient,** który powinien być podobny do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="03da9-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="03da9-145">W sekcji [ \<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) zwróć uwagę na [ \<punkt końcowy>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="03da9-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="03da9-146">Element \*\* &lt;punktu&gt; końcowego\*\* definiuje punkt końcowy, który klient używa do uzyskania dostępu do usługi w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="03da9-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="03da9-147">Adres: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="03da9-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="03da9-148">Adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="03da9-148">The address of the endpoint.</span></span>
- <span data-ttu-id="03da9-149">Umowa serwisowa: `ServiceReference1.ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="03da9-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="03da9-150">Umowa serwisowa obsługuje komunikację między klientem WCF a usługą.</span><span class="sxs-lookup"><span data-stu-id="03da9-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="03da9-151">Visual Studio wygenerował ten kontrakt, gdy był używany jego Dodaj funkcję **odwołania do usługi.**</span><span class="sxs-lookup"><span data-stu-id="03da9-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="03da9-152">Zasadniczo jest to kopia umowy zdefiniowanej w projekcie GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="03da9-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span>
- <span data-ttu-id="03da9-153">Wiązanie: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="03da9-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="03da9-154">Powiązanie określa HTTP jako transport, interoperacyjne zabezpieczenia i inne szczegóły konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="03da9-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="03da9-155">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="03da9-155">Next steps</span></span>

<span data-ttu-id="03da9-156">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="03da9-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="03da9-157">Tworzenie i konfigurowanie projektu aplikacji konsoli dla klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="03da9-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="03da9-158">Dodaj odwołanie do usługi WCF do generowania plików klasy proxy i konfiguracji dla aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="03da9-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="03da9-159">Przejdź do następnego samouczka, aby dowiedzieć się, jak korzystać z wygenerowanego klienta.</span><span class="sxs-lookup"><span data-stu-id="03da9-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="03da9-160">Samouczek: Korzystanie z klienta WCF</span><span class="sxs-lookup"><span data-stu-id="03da9-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
