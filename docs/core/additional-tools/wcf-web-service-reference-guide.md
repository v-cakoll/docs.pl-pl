---
title: Dodaj odwołanie do usługi sieci Web WCF
description: Przegląd Microsoft WCF Web Service Reference Provider narzędzie które dodaje funkcje dla projektów .NET Core i ASP.NET Core, podobne do Dodaj odwołanie do usługi dla projektów programu .NET Framework.
author: mlacouture
ms.date: 04/19/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 3566a92e05c03cc77e59a14e3b2521a1d6d0758a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245577"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="4184e-103">Użyj narzędzia dostawcy odwołanie do usługi sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="4184e-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="4184e-104">W ciągu lat wielu deweloperów programu Visual Studio są Państwo zadowoleni produktywność, [ **Dodaj odwołanie do usługi** ](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) narzędzia podane w razie ich projektów programu .NET Framework na dostęp do usług sieci web.</span><span class="sxs-lookup"><span data-stu-id="4184e-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="4184e-105">**WCF Web Service Reference** narzędzie to rozszerzenie usług połączonych programu Visual Studio, które zapewnia środowisko, takich jak funkcja Dodaj odwołanie do usługi .NET Core i ASP.NET Core projektów.</span><span class="sxs-lookup"><span data-stu-id="4184e-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="4184e-106">To narzędzie służy do pobierania metadanych z usługi sieci web w bieżącym rozwiązaniu, w lokalizacji sieciowej lub z pliku WSDL i generuje plik zgodne źródło .NET Core, zawierające kod serwera proxy klienta Windows Communication Foundation (WCF), który służy do dostępu do sieci web Usługa.</span><span class="sxs-lookup"><span data-stu-id="4184e-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4184e-107">Użytkownik powinien odwoływać się tylko do usług z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="4184e-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="4184e-108">Dodawanie odwołań z niezaufanego źródła może naruszyć bezpieczeństwo.</span><span class="sxs-lookup"><span data-stu-id="4184e-108">Adding references from an untrusted source may compromise security.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="4184e-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="4184e-109">Prerequisites</span></span>

* <span data-ttu-id="4184e-110">[Visual Studio 2017 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) lub nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="4184e-110">[Visual Studio 2017 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="4184e-111">Jak używać rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="4184e-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="4184e-112">**WCF Web Service Reference** opcja ma zastosowanie do projektów utworzonych za pomocą następujące szablony projektów:</span><span class="sxs-lookup"><span data-stu-id="4184e-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
> * <span data-ttu-id="4184e-113">**Visual C#** > **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="4184e-113">**Visual C#** > **.NET Core**</span></span>
> * <span data-ttu-id="4184e-114">**Wizualne C#**   >  **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="4184e-114">**Visual C#** > **.NET Standard**</span></span>
> * <span data-ttu-id="4184e-115">**Wizualne C#**   >  **Web** > **aplikacji sieci Web platformy ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="4184e-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="4184e-116">Za pomocą **aplikacji sieci Web programu ASP.NET Core** szablon projektu, na przykład, ten artykuł przeprowadzi Cię przez dodawanie odwołania do usługi WCF do projektu:</span><span class="sxs-lookup"><span data-stu-id="4184e-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="4184e-117">W Eksploratorze rozwiązań kliknij dwukrotnie **podłączone usługi** węzła projektu (dla projektu .NET Core lub .NET Standard ta opcja jest dostępna po kliknięciu prawym przyciskiem myszy **zależności** węzła Projekt w Eksploratorze rozwiązań).</span><span class="sxs-lookup"><span data-stu-id="4184e-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

<span data-ttu-id="4184e-118">**Podłączone usługi** zostanie wyświetlona strona, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="4184e-118">The **Connected Services** page appears as shown in the following image:</span></span>

![Wizualne kartę podłączone usługi Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="4184e-120">Na **podłączone usługi** kliknij **Microsoft WCF Web Service Reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="4184e-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="4184e-121">Spowoduje to przejście **skonfigurować WCF Web Service Reference** kreatora:</span><span class="sxs-lookup"><span data-stu-id="4184e-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

![Wizualne kartę punktu końcowego usługi Studio dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="4184e-123">Wybierz usługę.</span><span class="sxs-lookup"><span data-stu-id="4184e-123">Select a service.</span></span>

    <span data-ttu-id="4184e-124">3a.</span><span class="sxs-lookup"><span data-stu-id="4184e-124">3a.</span></span> <span data-ttu-id="4184e-125">Kilka innych opcji wyszukiwania usługi są dostępne w ramach **skonfigurować WCF Web Service Reference** kreatora:</span><span class="sxs-lookup"><span data-stu-id="4184e-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>
    
     * <span data-ttu-id="4184e-126">Aby wyszukać usługi zdefiniowane w bieżącym rozwiązaniu, kliknij przycisk **odnajdź** przycisku.</span><span class="sxs-lookup"><span data-stu-id="4184e-126">To search for services defined in the current solution, click the **Discover** button.</span></span> 
     * <span data-ttu-id="4184e-127">Aby wyszukać usług hostowanych pod określonym adresem, wprowadź adres URL usługi, w **adres** pole, a następnie kliknij przycisk **Przejdź** przycisku.</span><span class="sxs-lookup"><span data-stu-id="4184e-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="4184e-128">Aby wybrać plik WSDL, który zawiera informacje o metadanych dla usługi sieci web, kliknij przycisk **Przeglądaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="4184e-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span> 
     
    <span data-ttu-id="4184e-129">3b.</span><span class="sxs-lookup"><span data-stu-id="4184e-129">3b.</span></span> <span data-ttu-id="4184e-130">Wybierz usługę z listy wyników wyszukiwania w **usług** pole.</span><span class="sxs-lookup"><span data-stu-id="4184e-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="4184e-131">W razie potrzeby wprowadź przestrzeń nazw dla wygenerowanego kodu w odpowiednich **Namespace** pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="4184e-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>
    
    <span data-ttu-id="4184e-132">3c.</span><span class="sxs-lookup"><span data-stu-id="4184e-132">3c.</span></span> <span data-ttu-id="4184e-133">Kliknij przycisk **dalej** przycisk, aby otworzyć **opcje typu danych** i **opcje klienta** stron.</span><span class="sxs-lookup"><span data-stu-id="4184e-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="4184e-134">Alternatywnie kliknij **Zakończ** przycisk, aby użyć opcji domyślnych.</span><span class="sxs-lookup"><span data-stu-id="4184e-134">Alternatively, click the **Finish** button to use the default options.</span></span>


4. <span data-ttu-id="4184e-135">**Opcje typu danych** formularz pozwala dostosować ustawienia konfiguracji odniesienia wygenerowanego usługi:</span><span class="sxs-lookup"><span data-stu-id="4184e-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

![Visual Studio danych typu karta Opcje dla platformy .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

> [!NOTE]
> <span data-ttu-id="4184e-137">**Ponownie użyj typów w przywoływanych zestawach** pole wyboru opcji jest przydatne w przypadku, gdy typy danych służące do generowania kodu odwołania usługi są definiowane w jeden z przywoływanych zestawach projektu.</span><span class="sxs-lookup"><span data-stu-id="4184e-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="4184e-138">Należy ponownie użyć tych istniejących typów danych, aby uniknąć problemów z konflikt lub środowisko uruchomieniowe typów w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4184e-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

<span data-ttu-id="4184e-139">Może wystąpić opóźnienie, podczas ładowania informacji o typie, w zależności od tego, czy liczba zależności projektu i innymi czynnikami wydajnościowymi systemu.</span><span class="sxs-lookup"><span data-stu-id="4184e-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="4184e-140">**Zakończ** przycisk jest niedostępny podczas ładowania, chyba że **ponownie użyj typów w przywoływanych zestawach** pole wyboru jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="4184e-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="4184e-141">Kliknij przycisk **Zakończ** po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="4184e-141">Click **Finish** when you are done.</span></span>


<span data-ttu-id="4184e-142">Podczas wyświetlania postępu, narzędzie:</span><span class="sxs-lookup"><span data-stu-id="4184e-142">While displaying progress, the tool:</span></span>

* <span data-ttu-id="4184e-143">Pobiera metadane z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="4184e-143">Downloads metadata from the WCF service.</span></span> 
* <span data-ttu-id="4184e-144">Generuje kod odwołania usługi w pliku o nazwie *reference.cs*i dodaje go do projektu w obszarze **podłączone usługi** węzła.</span><span class="sxs-lookup"><span data-stu-id="4184e-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span> 
* <span data-ttu-id="4184e-145">Aktualizuje plik projektu (.csproj) za pomocą odwołania do pakietu NuGet wymagane do kompilowania i uruchamiania na platformie docelowej.</span><span class="sxs-lookup"><span data-stu-id="4184e-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Visual Studio postępu okna](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="4184e-147">Po ukończeniu tych procesów, można utworzyć wystąpienia typu wygenerowanego klienta WCF i wywoływanie operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="4184e-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4184e-148">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4184e-148">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="4184e-149">Opinie i pytania</span><span class="sxs-lookup"><span data-stu-id="4184e-149">Feedback & questions</span></span>
<span data-ttu-id="4184e-150">Jeśli masz pytania lub opinie, [Otwórz problem w serwisie GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="4184e-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="4184e-151">Możesz również sprawdzić wszelkie istniejące pytania lub problemy [w repozytorium usługi WCF w usłudze GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="4184e-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="4184e-152">Uwagi do wersji</span><span class="sxs-lookup"><span data-stu-id="4184e-152">Release notes</span></span>
* <span data-ttu-id="4184e-153">Zapoznaj się [informacje o wersji](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) uzyskać informacje o zaktualizowanej wersji, w tym znanych problemów.</span><span class="sxs-lookup"><span data-stu-id="4184e-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span> 
