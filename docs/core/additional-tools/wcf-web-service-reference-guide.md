---
title: Dodaj odwołanie do usługi sieci Web WCF
description: Przegląd narzędzia Microsoft WCF Web Service Reference Provider, które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobnie jak Dodaj odwołanie do usługi dla projektów .NET Framework.
author: mlacouture
ms.date: 04/19/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 28eaae4a83d918f8a9e5376eb3c8d42843ffa027
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773957"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="e8226-103">Korzystanie z narzędzia dostawcy odwołań usługi sieci Web programu WCF</span><span class="sxs-lookup"><span data-stu-id="e8226-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="e8226-104">W ciągu lat wiele deweloperów programu Visual Studio korzystało z wydajności, którą zapewnia narzędzie [**Dodaj odwołanie do usługi**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) , gdy .NET Framework projekty potrzebują dostępu do usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e8226-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="e8226-105">Narzędzie **referencyjne usługi sieci Web WCF** to rozszerzenie usługi połączonej z programem Visual Studio, które zapewnia środowisko, takie jak Dodaj odwołanie do usługi funkcje dla projektów .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e8226-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="e8226-106">To narzędzie pobiera metadane z usługi sieci Web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub z pliku WSDL i generuje plik źródłowy zgodny z programem .NET Core zawierający kod serwera proxy klienta Windows Communication Foundation (WCF), którego można użyć w celu uzyskania dostępu do sieci Web. usługi.</span><span class="sxs-lookup"><span data-stu-id="e8226-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8226-107">Należy tylko odwoływać się do usług z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="e8226-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="e8226-108">Dodanie odwołań z niezaufanego źródła może spowodować naruszenie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e8226-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e8226-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e8226-109">Prerequisites</span></span>

- <span data-ttu-id="e8226-110">[Visual Studio 2017 w wersji 15,5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) lub nowszej</span><span class="sxs-lookup"><span data-stu-id="e8226-110">[Visual Studio 2017 version 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="e8226-111">Jak używać rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="e8226-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="e8226-112">Opcja **odwołania do usługi sieci Web programu WCF** ma zastosowanie do projektów utworzonych przy użyciu następujących szablonów projektu:</span><span class="sxs-lookup"><span data-stu-id="e8226-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
>
> - <span data-ttu-id="e8226-113">**Visual C#**   >  **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="e8226-113">**Visual C#** > **.NET Core**</span></span>
> - <span data-ttu-id="e8226-114">**Visual C#**   >  **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="e8226-114">**Visual C#** > **.NET Standard**</span></span>
> - <span data-ttu-id="e8226-115">**Aplikacja internetowa**  **C# programu Visual**  > **Web**  >  ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e8226-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="e8226-116">Korzystając z szablonu projektu **ASP.NET Core aplikacji sieci Web** , w tym artykule opisano sposób dodawania do projektu odwołania do usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="e8226-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="e8226-117">W Eksplorator rozwiązań kliknij dwukrotnie węzeł **usługi połączone** w projekcie (dla projektu .NET Core lub .NET Standard, ta opcja jest dostępna po kliknięciu prawym przyciskiem myszy węzła **zależności** projektu w Eksplorator rozwiązań).</span><span class="sxs-lookup"><span data-stu-id="e8226-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="e8226-118">Zostanie wyświetlona strona **połączone usługi** , jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="e8226-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![Karta usługi połączone programu Visual Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="e8226-120">Na stronie **podłączone usługi** kliknij pozycję **Microsoft WCF Web Service Reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="e8226-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="e8226-121">Spowoduje to wyświetlenie kreatora **konfiguracji odwołania usługi sieci Web programu WCF** :</span><span class="sxs-lookup"><span data-stu-id="e8226-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![Karta punktu końcowego usługi Visual Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="e8226-123">Wybierz usługę.</span><span class="sxs-lookup"><span data-stu-id="e8226-123">Select a service.</span></span>

    <span data-ttu-id="e8226-124">art.</span><span class="sxs-lookup"><span data-stu-id="e8226-124">3a.</span></span> <span data-ttu-id="e8226-125">W kreatorze **konfiguracji odwołania usługi sieci Web programu WCF** dostępne są kilka opcji wyszukiwania usług:</span><span class="sxs-lookup"><span data-stu-id="e8226-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="e8226-126">Aby wyszukać usługi zdefiniowane w bieżącym rozwiązaniu, kliknij przycisk **odkryj** .</span><span class="sxs-lookup"><span data-stu-id="e8226-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="e8226-127">Aby wyszukać usługi hostowane w określonym adresie, wprowadź adres URL usługi w polu **adres** , a następnie kliknij przycisk **Przejdź** .</span><span class="sxs-lookup"><span data-stu-id="e8226-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="e8226-128">Aby wybrać plik WSDL zawierający informacje o metadanych usługi sieci Web, kliknij przycisk **Przeglądaj** .</span><span class="sxs-lookup"><span data-stu-id="e8226-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="e8226-129">3b.</span><span class="sxs-lookup"><span data-stu-id="e8226-129">3b.</span></span> <span data-ttu-id="e8226-130">Wybierz usługę z listy wyników wyszukiwania w polu **usługi** .</span><span class="sxs-lookup"><span data-stu-id="e8226-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="e8226-131">W razie potrzeby wprowadź przestrzeń nazw dla wygenerowanego kodu w polu tekstowym odpowiadające mu **przestrzeń nazw** .</span><span class="sxs-lookup"><span data-stu-id="e8226-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="e8226-132">3C.</span><span class="sxs-lookup"><span data-stu-id="e8226-132">3c.</span></span> <span data-ttu-id="e8226-133">Kliknij przycisk **dalej** , aby otworzyć **Opcje typu danych** i strony **Opcje klienta** .</span><span class="sxs-lookup"><span data-stu-id="e8226-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="e8226-134">Alternatywnie kliknij przycisk **Zakończ** , aby użyć opcji domyślnych.</span><span class="sxs-lookup"><span data-stu-id="e8226-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="e8226-135">Formularz **Opcje typu danych** umożliwia uściślenie ustawień konfiguracji wygenerowanych odwołań do usługi:</span><span class="sxs-lookup"><span data-stu-id="e8226-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![Karta Opcje typu danych programu Visual Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="e8226-137">Opcja **Użyj ponownie typów w przywoływanych zestawach** jest przydatna, gdy typy danych potrzebne do generowania kodu odwołania do usługi są zdefiniowane w jednym z zestawów, do których się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="e8226-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="e8226-138">Ważne jest, aby ponownie użyć istniejących typów danych, aby uniknąć konfliktów typu czas kompilacji lub problemów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e8226-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="e8226-139">Podczas ładowania informacji o typie może wystąpić opóźnienie, w zależności od liczby zależności projektu i innych czynników wydajności systemu.</span><span class="sxs-lookup"><span data-stu-id="e8226-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="e8226-140">Przycisk **Zakończ** jest wyłączony podczas ładowania, chyba że pole wyboru **ponowne używanie typów w przywoływanych zestawach** nie jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="e8226-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="e8226-141">Po zakończeniu kliknij przycisk **Zakończ** .</span><span class="sxs-lookup"><span data-stu-id="e8226-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="e8226-142">Podczas wyświetlania postępu narzędzie:</span><span class="sxs-lookup"><span data-stu-id="e8226-142">While displaying progress, the tool:</span></span>

- <span data-ttu-id="e8226-143">Pobiera metadane z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="e8226-143">Downloads metadata from the WCF service.</span></span>
- <span data-ttu-id="e8226-144">Generuje kod odwołania do usługi w pliku o nazwie *Reference.cs*i dodaje go do projektu w węźle **usługi połączone** .</span><span class="sxs-lookup"><span data-stu-id="e8226-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span>
- <span data-ttu-id="e8226-145">Aktualizuje plik projektu (. csproj) odwołania do pakietów NuGet wymagane do kompilowania i uruchamiania na platformie docelowej.</span><span class="sxs-lookup"><span data-stu-id="e8226-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Okno postępu programu Visual Studio](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="e8226-147">Po zakończeniu tych procesów można utworzyć wystąpienie wygenerowanego typu klienta WCF i wywołać operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="e8226-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e8226-148">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e8226-148">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="e8226-149">Opinie & pytania</span><span class="sxs-lookup"><span data-stu-id="e8226-149">Feedback & questions</span></span>

<span data-ttu-id="e8226-150">Jeśli masz jakieś pytania lub opinie, [Otwórz problem w usłudze GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="e8226-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="e8226-151">Możesz również zapoznać się z istniejącymi pytaniami i problemami [w REPOZYTORIUM WCF w serwisie GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="e8226-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="e8226-152">Uwagi do wersji</span><span class="sxs-lookup"><span data-stu-id="e8226-152">Release notes</span></span>

- <span data-ttu-id="e8226-153">Zapoznaj się z informacjami o [wersji](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) dotyczącymi zaktualizowanych informacji o wersji, w tym znanych problemów.</span><span class="sxs-lookup"><span data-stu-id="e8226-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>
