---
title: Tworzenie aplikacji dla wielu platform przy użyciu przenośnej biblioteki klas
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afaa8e118bb21e5c1e4f1c53b1d0d29ca6bb3bf5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47172709"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a><span data-ttu-id="7a2e9-102">Programowanie dla wielu platform przy użyciu biblioteki klas przenośnych</span><span class="sxs-lookup"><span data-stu-id="7a2e9-102">Cross-platform development with the Portable Class Library</span></span>

<span data-ttu-id="7a2e9-103">Typ projektu biblioteki klas przenośnych w programie Visual Studio pomaga w tworzeniu aplikacji dla wielu platform i bibliotek dla platform firmy Microsoft, szybkie i łatwe.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-103">The Portable Class Library project type in Visual Studio helps you build cross-platform apps and libraries for Microsoft platforms quickly and easily.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

<span data-ttu-id="7a2e9-104">Biblioteki klas przenośnych mogą pomóc skrócić czas i koszt programowania oraz testowania kodu.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-104">Portable class libraries can help you reduce the time and costs of developing and testing code.</span></span> <span data-ttu-id="7a2e9-105">Użyj tego typu projektu do zapisywania i tworzenia przenośnych zestawów .NET Framework, a następnie odwołuje się do tych zestawów z aplikacji przeznaczonych dla wielu platform, takich jak .NET Framework, iOS i komputerów Mac.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-105">Use this project type to write and build portable .NET Framework assemblies, and then reference those assemblies from apps that target multiple platforms such as the .NET Framework, iOS, or Mac.</span></span>

<span data-ttu-id="7a2e9-106">Nawet po Utwórz projekt biblioteki klas przenośnych w programie Visual Studio i zacznij programować go, możesz zmienić platformy docelowe.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-106">Even after you create a Portable Class Library project in Visual Studio and start developing it, you can change the target platforms.</span></span> <span data-ttu-id="7a2e9-107">Program Visual Studio kompiluje biblioteki za pomocą nowych zestawów, który pomaga zidentyfikować zmiany, które należy wprowadzić w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-107">Visual Studio compiles your library with the new assemblies, which helps you identify the changes you need to make in your code.</span></span>

## <a name="create-a-portable-class-library-project"></a><span data-ttu-id="7a2e9-108">Utwórz projekt biblioteki klas przenośnych</span><span class="sxs-lookup"><span data-stu-id="7a2e9-108">Create a Portable Class Library project</span></span>

<span data-ttu-id="7a2e9-109">Aby utworzyć Portable Class Library, należy użyć szablonu dostępnego w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-109">To create a Portable Class Library, use the template provided in Visual Studio.</span></span> <span data-ttu-id="7a2e9-110">Utwórz nowy projekt (**pliku** > **nowy projekt**), a następnie w **nowy projekt** okna dialogowego Wybierz język programowania (Visual C# lub Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-110">Create a new project (**File** > **New Project**), and in the **New Project** dialog box, select your programming language (Visual C# or Visual Basic).</span></span> <span data-ttu-id="7a2e9-111">Następnie wybierz **biblioteki klas (starsza wersja przenośny)** szablonu.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-111">Then, select the **Class Library (Legacy Portable)** template.</span></span> <span data-ttu-id="7a2e9-112">Wprowadź nazwę dla projektu, a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-112">Enter a name for your project and choose **OK**.</span></span>

<span data-ttu-id="7a2e9-113">**Dodaj Portable Class Library** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-113">The **Add Portable Class Library** dialog box appears.</span></span> <span data-ttu-id="7a2e9-114">Wybierz co najmniej dwa elementy docelowe, a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-114">Choose two or more targets, and then choose **OK**.</span></span>

![Dodaj elementy docelowe biblioteki klas przenośnych w programie Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a><span data-ttu-id="7a2e9-116">Zmień cele</span><span class="sxs-lookup"><span data-stu-id="7a2e9-116">Change targets</span></span>

<span data-ttu-id="7a2e9-117">Możesz zmienić platformy docelowe projektu biblioteki klas przenośnych podczas jej tworzenia lub po rozpoczęciu programowania.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-117">You can change the target platforms of a portable class library project when you create it or after you’ve started development.</span></span> <span data-ttu-id="7a2e9-118">Jeśli chcesz zmienić elementy docelowe, po utworzeniu projektu w **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu biblioteki klas przenośnych (nie rozwiązanie), a następnie wybierz **właściwości** .</span><span class="sxs-lookup"><span data-stu-id="7a2e9-118">If you want to change the targets after you’ve created your project, in **Solution Explorer**, open the shortcut menu for your Portable Class Library project (not the solution), and then choose **Properties**.</span></span> <span data-ttu-id="7a2e9-119">Na stronie właściwości projektu **biblioteki** karta przedstawia platformy projektu obecnie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-119">On the project properties page, the **Library** tab shows the platforms that your project currently targets.</span></span>

![Właściwości projektu biblioteki klas przenośnych w programie Visual Studio](media/pcl-project-properties.png)

<span data-ttu-id="7a2e9-121">Aby dodać lub usunąć elementy docelowe, wybierz opcję **zmiany** przycisk, a następnie wybierz i usuń zaznaczenie pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-121">To add or remove targets, choose the **Change** button, and then select and clear the appropriate check boxes.</span></span>

<span data-ttu-id="7a2e9-122">Jeśli zmienisz docelowe, interfejsów API, które są dostępne i umożliwiają tworzenie projektu zmieni się na dopasować wybór.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-122">When you change the targets, the APIs that are available to you for developing your project will change to match your selection.</span></span> <span data-ttu-id="7a2e9-123">Visual Studio zgłasza błędy i ostrzeżenia, które może wyniknąć z elementów docelowych, zmiana.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-123">Visual Studio reports the errors and warnings that may occur as a result of the targets changing.</span></span>

<span data-ttu-id="7a2e9-124">Jeśli chcesz przeprowadzić ocenę przenośność zestawy przed wprowadzić zmiany w programie Visual Studio, można użyć [narzędzia .NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-124">If you want to evaluate the portability of your assemblies before you make changes in Visual Studio, you can use the [.NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).</span></span>

## <a name="supported-types-and-members"></a><span data-ttu-id="7a2e9-125">Obsługiwane typy i elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7a2e9-125">Supported types and members</span></span>

<span data-ttu-id="7a2e9-126">Typy i elementy członkowskie, które są dostępne w projektach Portable Class Library zależy od kilku czynników zgodności:</span><span class="sxs-lookup"><span data-stu-id="7a2e9-126">The types and members that are available in Portable Class Library projects are constrained by several compatibility factors:</span></span>

-   <span data-ttu-id="7a2e9-127">Muszą one zostać udostępnione w lokalizacjach docelowych, które wybrano.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-127">They must be shared across the targets you selected.</span></span>

-   <span data-ttu-id="7a2e9-128">Musi zachowywać się podobnie w tych lokalizacjach docelowych.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-128">The must behave similarly across those targets.</span></span>

-   <span data-ttu-id="7a2e9-129">Nie mogą być kandydatami do wycofania z użycia.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-129">They must not be candidates for deprecation.</span></span>

-   <span data-ttu-id="7a2e9-130">Muszą mieć sens w środowisku przenośnym, zwłaszcza gdy pomocnicze elementy członkowskie nie są przenośne.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-130">They must make sense in a portable environment, especially when supporting members are not portable.</span></span>

<span data-ttu-id="7a2e9-131">Jeśli członek jest obsługiwany, in Portable Class Library i wybrane elementy docelowe, pojawi się w projekcie w technologii IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-131">If a member is supported in the Portable Class Library and for your selected targets, it will appear in your project in IntelliSense.</span></span> <span data-ttu-id="7a2e9-132">Należy jednak pamiętać, że interfejs API może być obsługiwana w Portable Class Library, ale czy można użyć interfejsu API zależy od celów wybierz.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-132">However, remember that an API may be supported in the Portable Class Library, but whether you can use the API depends on the targets you select.</span></span>

## <a name="api-differences-in-the-portable-class-library"></a><span data-ttu-id="7a2e9-133">Różnice interfejsu API w bibliotece klas przenośnych</span><span class="sxs-lookup"><span data-stu-id="7a2e9-133">API differences in the Portable Class Library</span></span>

<span data-ttu-id="7a2e9-134">Aby zestawy Portable Class Library zgodne na wszystkich obsługiwanych platformach, niektórzy członkowie nieznacznie zmieniono in Portable Class Library.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-134">To make Portable Class Library assemblies compatible across all supported platforms, some members have been slightly changed in the Portable Class Library.</span></span>

## <a name="use-the-portable-class-library"></a><span data-ttu-id="7a2e9-135">Korzystanie z biblioteki klas przenośnych</span><span class="sxs-lookup"><span data-stu-id="7a2e9-135">Use the Portable Class Library</span></span>

<span data-ttu-id="7a2e9-136">Po skompilowaniu projektu Portable Class Library, możesz po prostu odwołanie do niego z innych projektów.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-136">After you build your Portable Class Library project, you just reference it from other projects.</span></span> <span data-ttu-id="7a2e9-137">Odwołanie może dotyczyć projektu lub określonych zestawów zawierających klasy, do których chce się uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-137">You can reference either the project or specific assemblies that contain the classes you want to access.</span></span>

<span data-ttu-id="7a2e9-138">Aby uruchomić aplikację, która odwołuje się do zestawu Portable Class Library, wymagana wersja (lub nowszym) platformy docelowej musi być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-138">To run an app that references a Portable Class Library assembly, the required version (or later) of the targeted platforms must be installed on your computer.</span></span> <span data-ttu-id="7a2e9-139">Program Visual Studio zawiera wszystkie wymagane struktury, aby można było uruchomić aplikację bez dalszych modyfikacji na komputerze, który jest używany do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-139">Visual Studio contains all the required frameworks, so you can run the app without further modification on the computer that you used to develop the app.</span></span>

### <a name="deploy-a-universal-windows-app"></a><span data-ttu-id="7a2e9-140">Wdrażanie aplikacji Windows Universal</span><span class="sxs-lookup"><span data-stu-id="7a2e9-140">Deploy a Universal Windows app</span></span>

<span data-ttu-id="7a2e9-141">Podczas tworzenia aplikacji Windows Universal odwołujący się do zestawu Portable Class Library, wszystko, czego potrzebujesz do wdrażania aplikacji znajduje się w pakiecie aplikacji i nie trzeba wykonywać dalszych czynności są wymagane.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-141">When you create a Universal Windows app that references a Portable Class Library assembly, everything you need to deploy the app is included in the app package, and no further steps are required.</span></span>

### <a name="deploy-a-net-framework-app"></a><span data-ttu-id="7a2e9-142">Wdrażanie .NET Framework aplikacji</span><span class="sxs-lookup"><span data-stu-id="7a2e9-142">Deploy a .NET Framework app</span></span>

<span data-ttu-id="7a2e9-143">Podczas wdrażania aplikacji .NET Framework, która odwołuje się do zestawu Portable Class Library, należy określić zależność od prawidłowej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-143">When you deploy a .NET Framework app that references a Portable Class Library assembly, you must specify a dependency on the correct version of the .NET Framework.</span></span> <span data-ttu-id="7a2e9-144">Określenie tej zależności gwarantuje, że wymagana wersja będzie instalowana wraz z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-144">By specifying this dependency, you ensure that the required version is installed with your app.</span></span>

-   <span data-ttu-id="7a2e9-145">Aby utworzyć zależność z wdrożeniem ClickOnce: W **Eksploratora rozwiązań**, wybierz węzeł projektu dla projektu, który chcesz opublikować.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-145">To create a dependency with ClickOnce deployment: In **Solution Explorer**, choose the project node for the project you want to publish.</span></span> <span data-ttu-id="7a2e9-146">(Jest to projekt, który odwołuje się do projektu Portable Class Library). Na pasku menu wybierz **projektu** > **właściwości**, a następnie wybierz **Publikuj** kartę. Na **Publikuj** wybierz **wymagania wstępne**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-146">(This is the project that references the Portable Class Library project.) On the menu bar, choose **Project** > **Properties**, and then choose the **Publish** tab. On the **Publish** page, choose **Prerequisites**.</span></span> <span data-ttu-id="7a2e9-147">Jako wymaganie wstępne wybierz wymaganą wersję programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-147">Select the required .NET Framework version as a prerequisite.</span></span>

-   <span data-ttu-id="7a2e9-148">Aby utworzyć zależność z projektem Instalatora: W **Eksploratora rozwiązań**, wybierz projekt Instalatora.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-148">To create a dependency with a setup project: In **Solution Explorer**, choose the setup project.</span></span> <span data-ttu-id="7a2e9-149">Na pasku menu wybierz **projektu** > **właściwości** > **wymagania wstępne**.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-149">On the menu bar, choose **Project** > **Properties** > **Prerequisites**.</span></span> <span data-ttu-id="7a2e9-150">Jako wymaganie wstępne wybierz wymaganą wersję programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a2e9-150">Select the required .NET Framework version as a prerequisite.</span></span>

<span data-ttu-id="7a2e9-151">Aby uzyskać więcej informacji na temat wdrażania aplikacji .NET Framework, zobacz [przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="7a2e9-151">For more information about deploying .NET Framework apps, see [Deployment Guide for Developers](../../../docs/framework/deployment/deployment-guide-for-developers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7a2e9-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a2e9-152">See also</span></span>

- [<span data-ttu-id="7a2e9-153">Korzystanie z biblioteki klas przenośnych z modelem MVVM</span><span class="sxs-lookup"><span data-stu-id="7a2e9-153">Using Portable Class Library with MVVM</span></span>](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)
- [<span data-ttu-id="7a2e9-154">Zasoby aplikacji dla bibliotek przeznaczonych do wielu platform</span><span class="sxs-lookup"><span data-stu-id="7a2e9-154">App Resources for Libraries That Target Multiple Platforms</span></span>](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)
- [<span data-ttu-id="7a2e9-155">Narzędzia .NET portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="7a2e9-155">.NET Portability Analyzer</span></span>](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [<span data-ttu-id="7a2e9-156">Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7a2e9-156">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [<span data-ttu-id="7a2e9-157">Wdrażanie</span><span class="sxs-lookup"><span data-stu-id="7a2e9-157">Deployment</span></span>](../../../docs/framework/deployment/net-framework-applications.md)
