---
title: Dodaj odwołanie do usługi sieci Web WCF
description: Przegląd narzędzia Microsoft WCF Web Service Reference Provider, które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobnie jak Dodaj odwołanie do usługi dla projektów .NET Framework.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: feecf374e1af48f349495c13ea91b810c6b0a1c3
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191897"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="d4a0f-103">Korzystanie z narzędzia dostawcy odwołań usługi sieci Web programu WCF</span><span class="sxs-lookup"><span data-stu-id="d4a0f-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="d4a0f-104">W ciągu lat wiele deweloperów programu Visual Studio korzystało z wydajności, którą zapewnia narzędzie [**Dodaj odwołanie do usługi**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) , gdy .NET Framework projekty potrzebują dostępu do usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="d4a0f-105">Narzędzie **referencyjne usługi sieci Web WCF** to rozszerzenie usługi połączonej z programem Visual Studio, które zapewnia środowisko, takie jak Dodaj odwołanie do usługi funkcje dla projektów .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="d4a0f-106">To narzędzie pobiera metadane z usługi sieci Web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub z pliku WSDL i generuje plik źródłowy zgodny z programem .NET Core zawierający kod serwera proxy klienta Windows Communication Foundation (WCF), którego można użyć w celu uzyskania dostępu do sieci Web. usługi.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4a0f-107">Należy tylko odwoływać się do usług z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="d4a0f-108">Dodanie odwołań z niezaufanego źródła może spowodować naruszenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4a0f-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d4a0f-109">Prerequisites</span></span>

- <span data-ttu-id="d4a0f-110">[Visual Studio 2017 w wersji 15,5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) lub nowszej</span><span class="sxs-lookup"><span data-stu-id="d4a0f-110">[Visual Studio 2017 version 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="d4a0f-111">Jak używać rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="d4a0f-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="d4a0f-112">Opcja **odwołania do usługi sieci Web programu WCF** ma zastosowanie do projektów utworzonych przy użyciu następujących szablonów projektu:</span><span class="sxs-lookup"><span data-stu-id="d4a0f-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
>
> - <span data-ttu-id="d4a0f-113">**Visual C#**   >  **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="d4a0f-113">**Visual C#** > **.NET Core**</span></span>
> - <span data-ttu-id="d4a0f-114">**Visual C#**   >  **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="d4a0f-114">**Visual C#** > **.NET Standard**</span></span>
> - <span data-ttu-id="d4a0f-115">**Aplikacja internetowa**  **C# programu Visual**  > **Web**  >  ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d4a0f-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="d4a0f-116">Korzystając z szablonu projektu **ASP.NET Core aplikacji sieci Web** , w tym artykule opisano sposób dodawania do projektu odwołania do usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="d4a0f-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="d4a0f-117">W Eksplorator rozwiązań kliknij dwukrotnie węzeł **usługi połączone** w projekcie (dla projektu .NET Core lub .NET Standard, ta opcja jest dostępna po kliknięciu prawym przyciskiem myszy węzła **zależności** projektu w Eksplorator rozwiązań).</span><span class="sxs-lookup"><span data-stu-id="d4a0f-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="d4a0f-118">Zostanie wyświetlona strona **połączone usługi** , jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="d4a0f-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![Karta usługi połączone programu Visual Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="d4a0f-120">Na stronie **podłączone usługi** kliknij pozycję **Microsoft WCF Web Service Reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="d4a0f-121">Spowoduje to wyświetlenie kreatora **konfiguracji odwołania usługi sieci Web programu WCF** :</span><span class="sxs-lookup"><span data-stu-id="d4a0f-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![Karta punktu końcowego usługi Visual Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="d4a0f-123">Wybierz usługę.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-123">Select a service.</span></span>

    <span data-ttu-id="d4a0f-124">art.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-124">3a.</span></span> <span data-ttu-id="d4a0f-125">W kreatorze **konfiguracji odwołania usługi sieci Web programu WCF** dostępne są kilka opcji wyszukiwania usług:</span><span class="sxs-lookup"><span data-stu-id="d4a0f-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="d4a0f-126">Aby wyszukać usługi zdefiniowane w bieżącym rozwiązaniu, kliknij przycisk **odkryj** .</span><span class="sxs-lookup"><span data-stu-id="d4a0f-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="d4a0f-127">Aby wyszukać usługi hostowane w określonym adresie, wprowadź adres URL usługi w polu **adres** , a następnie kliknij przycisk **Przejdź** .</span><span class="sxs-lookup"><span data-stu-id="d4a0f-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="d4a0f-128">Aby wybrać plik WSDL zawierający informacje o metadanych usługi sieci Web, kliknij przycisk **Przeglądaj** .</span><span class="sxs-lookup"><span data-stu-id="d4a0f-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="d4a0f-129">3b.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-129">3b.</span></span> <span data-ttu-id="d4a0f-130">Wybierz usługę z listy wyników wyszukiwania w polu **usługi** .</span><span class="sxs-lookup"><span data-stu-id="d4a0f-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="d4a0f-131">W razie potrzeby wprowadź przestrzeń nazw dla wygenerowanego kodu w polu tekstowym odpowiadające mu **przestrzeń nazw** .</span><span class="sxs-lookup"><span data-stu-id="d4a0f-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="d4a0f-132">3C.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-132">3c.</span></span> <span data-ttu-id="d4a0f-133">Kliknij przycisk **dalej** , aby otworzyć **Opcje typu danych** i strony **Opcje klienta** .</span><span class="sxs-lookup"><span data-stu-id="d4a0f-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="d4a0f-134">Alternatywnie kliknij przycisk **Zakończ** , aby użyć opcji domyślnych.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="d4a0f-135">Formularz **Opcje typu danych** umożliwia uściślenie ustawień konfiguracji wygenerowanych odwołań do usługi:</span><span class="sxs-lookup"><span data-stu-id="d4a0f-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![Karta Opcje typu danych programu Visual Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="d4a0f-137">Opcja **Użyj ponownie typów w przywoływanych zestawach** jest przydatna, gdy typy danych potrzebne do generowania kodu odwołania do usługi są zdefiniowane w jednym z zestawów, do których się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="d4a0f-138">Ważne jest, aby ponownie użyć istniejących typów danych, aby uniknąć konfliktów typu czas kompilacji lub problemów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="d4a0f-139">Podczas ładowania informacji o typie może wystąpić opóźnienie, w zależności od liczby zależności projektu i innych czynników wydajności systemu.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="d4a0f-140">Przycisk **Zakończ** jest wyłączony podczas ładowania, chyba że pole wyboru **ponowne używanie typów w przywoływanych zestawach** nie jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="d4a0f-141">Po zakończeniu kliknij przycisk **Zakończ** .</span><span class="sxs-lookup"><span data-stu-id="d4a0f-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="d4a0f-142">Podczas wyświetlania postępu narzędzie:</span><span class="sxs-lookup"><span data-stu-id="d4a0f-142">While displaying progress, the tool:</span></span>

- <span data-ttu-id="d4a0f-143">Pobiera metadane z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-143">Downloads metadata from the WCF service.</span></span>
- <span data-ttu-id="d4a0f-144">Generuje kod odwołania do usługi w pliku o nazwie *Reference.cs*i dodaje go do projektu w węźle **usługi połączone** .</span><span class="sxs-lookup"><span data-stu-id="d4a0f-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span>
- <span data-ttu-id="d4a0f-145">Aktualizuje plik projektu (. csproj) odwołania do pakietów NuGet wymagane do kompilowania i uruchamiania na platformie docelowej.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Okno postępu programu Visual Studio](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="d4a0f-147">Po zakończeniu tych procesów można utworzyć wystąpienie wygenerowanego typu klienta WCF i wywołać operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4a0f-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4a0f-148">See also</span></span>

- [<span data-ttu-id="d4a0f-149">Wprowadzenie do aplikacji Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d4a0f-149">Get started with Windows Communication Foundation applications</span></span>](../../framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="d4a0f-150">Usługi Windows Communication Foundation i usługi danych programu WCF w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d4a0f-150">Windows Communication Foundation services and WCF data services in Visual Studio</span></span>](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [<span data-ttu-id="d4a0f-151">Funkcje obsługiwane przez program WCF na platformie .NET Core</span><span class="sxs-lookup"><span data-stu-id="d4a0f-151">WCF supported features on .NET Core</span></span>](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a><span data-ttu-id="d4a0f-152">Opinie & pytania</span><span class="sxs-lookup"><span data-stu-id="d4a0f-152">Feedback & questions</span></span>

<span data-ttu-id="d4a0f-153">Jeśli masz jakieś pytania lub opinie, zgłoś je w [społeczności deweloperów](https://developercommunity.visualstudio.com/) za pomocą narzędzia [Zgłoś problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) .</span><span class="sxs-lookup"><span data-stu-id="d4a0f-153">If you have any questions or feedback, report it at [Developer Community](https://developercommunity.visualstudio.com/) using the [Report a problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) tool.</span></span>

## <a name="release-notes"></a><span data-ttu-id="d4a0f-154">Uwagi do wersji</span><span class="sxs-lookup"><span data-stu-id="d4a0f-154">Release notes</span></span>

- <span data-ttu-id="d4a0f-155">Zapoznaj się z informacjami o [wersji](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) dotyczącymi zaktualizowanych informacji o wersji, w tym znanych problemów.</span><span class="sxs-lookup"><span data-stu-id="d4a0f-155">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>
