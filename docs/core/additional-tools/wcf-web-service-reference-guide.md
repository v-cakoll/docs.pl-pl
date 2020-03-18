---
title: Dodawanie odwołania do usługi sieci Web WCF
description: Omówienie narzędzia dostawcy usług sieci Web Microsoft WCF, które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobne do dodawania dokumentacji usługi dla projektów .NET Framework.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc
ms.openlocfilehash: cdd6b457d289dd7b752c97c5645f0797f24b72aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715685"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="bf2c3-103">Korzystanie z narzędzia Dostawcy informacji o usługach sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="bf2c3-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="bf2c3-104">Z biegiem lat wielu deweloperów programu Visual Studio cieszyło się produktywnością, jaką narzędzie [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) zapewniało, gdy ich projekty .NET Framework były potrzebne do uzyskania dostępu do usług sieci web.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="bf2c3-105">Narzędzie **WCF Web Service Reference** to rozszerzenie usługi połączonej z programami Visual Studio, które zapewnia środowisko, takie jak funkcja Dodaj odwołanie do usługi .NET Core i ASP.NET core.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="bf2c3-106">To narzędzie pobiera metadane z usługi sieci web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub z pliku WSDL i generuje plik źródłowy zgodny z .NET Core zawierający kod proxy klienta Windows Communication Foundation (WCF), za pomocą którego można uzyskać dostęp do sieci Web Usługi.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf2c3-107">Należy odwoływać się tylko do usług z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="bf2c3-108">Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bf2c3-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="bf2c3-109">Prerequisites</span></span>

- <span data-ttu-id="bf2c3-110">[Visual Studio 2017 w wersji 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) lub nowszej</span><span class="sxs-lookup"><span data-stu-id="bf2c3-110">[Visual Studio 2017 version 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="bf2c3-111">Jak korzystać z rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="bf2c3-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="bf2c3-112">Opcja **Odwołanie do usługi sieci Web WCF** ma zastosowanie do projektów utworzonych przy użyciu następujących szablonów projektów:</span><span class="sxs-lookup"><span data-stu-id="bf2c3-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
>
> - <span data-ttu-id="bf2c3-113">**Visual C#** > **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-113">**Visual C#** > **.NET Core**</span></span>
> - <span data-ttu-id="bf2c3-114">**Visual C#** > **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-114">**Visual C#** > **.NET Standard**</span></span>
> - <span data-ttu-id="bf2c3-115">**Wizualna aplikacja** > sieci Web ASP.NET**sieci Web** > języka**C#**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="bf2c3-116">Korzystając z szablonu projektu **ASP.NET Core Web Application** jako przykład, w tym artykule przeprowadzi Cię przez dodanie odwołania usługi WCF do projektu:</span><span class="sxs-lookup"><span data-stu-id="bf2c3-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="bf2c3-117">W Eksploratorze rozwiązań kliknij dwukrotnie węzeł **Połączonych usług** projektu (dla projektu .NET Core lub .NET Standard ta opcja jest dostępna po kliknięciu prawym przyciskiem myszy węzła **Zależności** projektu w Eksploratorze rozwiązań).</span><span class="sxs-lookup"><span data-stu-id="bf2c3-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="bf2c3-118">Strona **Połączone usługi** jest wyświetlana w sposób pokazany na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="bf2c3-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![Karta Połączone usługi Visual Studio dla programu .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="bf2c3-120">Na stronie **Połączone usługi** kliknij pozycję **Dostawca dokumentacji usługi sieci Web firmy Microsoft WCF**.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="bf2c3-121">Spowoduje to **wyświetlenie kreatora Konfigurowanie usługi sieci Web WCF:**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![Karta Punkt końcowy usługi Visual Studio dla programu .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="bf2c3-123">Wybierz usługę.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-123">Select a service.</span></span>

    <span data-ttu-id="bf2c3-124">3a.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-124">3a.</span></span> <span data-ttu-id="bf2c3-125">Istnieje kilka opcji wyszukiwania usług dostępnych w kreatorze **Konfigurowanie odwołania do usługi sieci Web WCF:**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="bf2c3-126">Aby wyszukać usługi zdefiniowane w bieżącym rozwiązaniu, kliknij przycisk **Odnajtzej.**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="bf2c3-127">Aby wyszukać usługi hostowane pod określonym adresem, wprowadź adres URL usługi w polu **Adres** i kliknij przycisk **Przejdź.**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="bf2c3-128">Aby wybrać plik WSDL zawierający informacje o metadanych usługi sieci Web, kliknij przycisk **Przeglądaj.**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="bf2c3-129">3b.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-129">3b.</span></span> <span data-ttu-id="bf2c3-130">Wybierz usługę z listy wyników wyszukiwania w polu **Usługi.**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="bf2c3-131">W razie potrzeby wprowadź obszar nazw wygenerowanego kodu w odpowiednim polu tekstowym **Obszar nazw.**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="bf2c3-132">3c.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-132">3c.</span></span> <span data-ttu-id="bf2c3-133">Kliknij przycisk **Dalej,** aby otworzyć **strony Opcje typu danych** i Opcje **klienta.**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="bf2c3-134">Alternatywnie kliknij przycisk **Zakończ,** aby użyć opcji domyślnych.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="bf2c3-135">Formularz **Opcje typu danych** umożliwia zawężenie wygenerowanych ustawień konfiguracji odwołania do usługi:</span><span class="sxs-lookup"><span data-stu-id="bf2c3-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![Karta Opcje typu danych programu Visual Studio dla programu .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="bf2c3-137">Opcja pola wyboru **Ponowne użycie w zestawach, do których istnieje odwołanie,** jest przydatna, gdy typy danych potrzebne do generowania kodu referencyjnego usługi są zdefiniowane w jednym z zestawów, do których odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="bf2c3-138">Ważne jest, aby ponownie użyć tych istniejących typów danych, aby uniknąć kolizji typu kompilacji lub problemy ze środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="bf2c3-139">Może wystąpić opóźnienie podczas ładowania informacji o typie, w zależności od liczby zależności projektu i innych czynników wydajności systemu.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="bf2c3-140">Przycisk **Zakończ** jest wyłączony podczas ładowania, chyba że pole wyboru **Ponowne użycie w zestawach, do których istnieje** odwołanie, nie jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="bf2c3-141">Po zakończeniu kliknij **przycisk Zakończ.**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="bf2c3-142">Podczas wyświetlania postępu, narzędzie:</span><span class="sxs-lookup"><span data-stu-id="bf2c3-142">While displaying progress, the tool:</span></span>

- <span data-ttu-id="bf2c3-143">Pobiera metadane z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-143">Downloads metadata from the WCF service.</span></span>
- <span data-ttu-id="bf2c3-144">Generuje kod odwołania do usługi w pliku o nazwie *reference.cs*i dodaje go do projektu w węźle **Połączone usługi.**</span><span class="sxs-lookup"><span data-stu-id="bf2c3-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span>
- <span data-ttu-id="bf2c3-145">Aktualizuje plik projektu (csproj) z odwołaniami do pakietu NuGet wymaganymi do kompilacji i uruchamiania na platformie docelowej.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Okno Postępu programu Visual Studio](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="bf2c3-147">Po zakończeniu tych procesów można utworzyć wystąpienie wygenerowanego typu klienta WCF i wywołać operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf2c3-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf2c3-148">See also</span></span>

- [<span data-ttu-id="bf2c3-149">Wprowadzenie do aplikacji Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="bf2c3-149">Get started with Windows Communication Foundation applications</span></span>](../../framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="bf2c3-150">Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bf2c3-150">Windows Communication Foundation services and WCF data services in Visual Studio</span></span>](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [<span data-ttu-id="bf2c3-151">Obsługiwane przez WCF funkcje programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="bf2c3-151">WCF supported features on .NET Core</span></span>](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a><span data-ttu-id="bf2c3-152">Opinie & pytania</span><span class="sxs-lookup"><span data-stu-id="bf2c3-152">Feedback & questions</span></span>

<span data-ttu-id="bf2c3-153">Jeśli masz jakiekolwiek pytania lub opinie, zgłoś to w [społeczności deweloperów](https://developercommunity.visualstudio.com/) za pomocą narzędzia [Zgłoś problem.](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)</span><span class="sxs-lookup"><span data-stu-id="bf2c3-153">If you have any questions or feedback, report it at [Developer Community](https://developercommunity.visualstudio.com/) using the [Report a problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) tool.</span></span>

## <a name="release-notes"></a><span data-ttu-id="bf2c3-154">Informacje o wersji</span><span class="sxs-lookup"><span data-stu-id="bf2c3-154">Release notes</span></span>

- <span data-ttu-id="bf2c3-155">Informacje o [wydaniu można znaleźć](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) w informacjach o wydaniu, w tym znanych problemach.</span><span class="sxs-lookup"><span data-stu-id="bf2c3-155">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>
