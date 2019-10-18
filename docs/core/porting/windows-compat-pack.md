---
title: Używanie pakietu zgodności systemu Windows do przenoszenia kodu do programu .NET Core
description: Dowiedz się więcej o pakiecie zgodności systemu Windows i jak można go używać do przenoszenia istniejącego kodu .NET Framework do programu .NET Core
author: terrajobst
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: adf2aaab27b5a8afcc89fceac67184d3b1974037
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521283"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="6e238-103">Używanie pakietu zgodności systemu Windows do przenoszenia kodu do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="6e238-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="6e238-104">Niektóre z najczęstszych problemów występujących podczas przenoszenia istniejącego kodu do programu .NET Core są zależnościami od interfejsów API i technologii, które są dostępne tylko w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6e238-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in the .NET Framework.</span></span> <span data-ttu-id="6e238-105">*Pakiet zgodności systemu Windows* zawiera wiele z tych technologii, więc znacznie łatwiej jest tworzyć aplikacje .NET Core i biblioteki .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6e238-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="6e238-106">Ten pakiet jest logicznym [rozszerzeniem .NET Standard 2,0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) , które znacząco zwiększają zestaw interfejsów API i istniejące skompilowane kod przy niemal nie modyfikowaniu.</span><span class="sxs-lookup"><span data-stu-id="6e238-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="6e238-107">Jednak aby zachować obietnicę .NET Standard ("jest zestawem interfejsów API, które udostępnia wszystkie implementacje platformy .NET"), nie obejmuje to technologii, które nie działają na wszystkich platformach, takich jak Registry, Instrumentacja zarządzania Windows (WMI) lub emisja odbicia Programowania.</span><span class="sxs-lookup"><span data-stu-id="6e238-107">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="6e238-108">*Pakiet zgodności systemu Windows* znajduje się w oparciu o .NET Standard i zapewnia dostęp do technologii, które są przeznaczone tylko dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6e238-108">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="6e238-109">Jest to szczególnie przydatne w przypadku klientów, którzy chcą przenieść się na platformę .NET Core, ale planujesz pozostawać w systemie Windows jako pierwszy krok.</span><span class="sxs-lookup"><span data-stu-id="6e238-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="6e238-110">W tym scenariuszu nie można używać technologii obsługujących tylko system Windows tylko w przypadku, gdy zalety migracji nie są równe zeru.</span><span class="sxs-lookup"><span data-stu-id="6e238-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="6e238-111">Zawartość pakietu</span><span class="sxs-lookup"><span data-stu-id="6e238-111">Package contents</span></span>

<span data-ttu-id="6e238-112">*Pakiet zgodności systemu Windows* jest dostarczany za pośrednictwem pakietu NuGet [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) i może być przywoływany z projektów przeznaczonych dla platformy .NET Core lub .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6e238-112">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="6e238-113">Zawiera on około 20 000 interfejsów API, w tym Windows-only i międzyplatformowych interfejsów API, z następujących obszarów technologii:</span><span class="sxs-lookup"><span data-stu-id="6e238-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="6e238-114">Strony kodowe</span><span class="sxs-lookup"><span data-stu-id="6e238-114">Code Pages</span></span>
- <span data-ttu-id="6e238-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="6e238-115">CodeDom</span></span>
- <span data-ttu-id="6e238-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="6e238-116">Configuration</span></span>
- <span data-ttu-id="6e238-117">Usługi katalogowe</span><span class="sxs-lookup"><span data-stu-id="6e238-117">Directory Services</span></span>
- <span data-ttu-id="6e238-118">Rysowania</span><span class="sxs-lookup"><span data-stu-id="6e238-118">Drawing</span></span>
- <span data-ttu-id="6e238-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="6e238-119">ODBC</span></span>
- <span data-ttu-id="6e238-120">Uprawnienia</span><span class="sxs-lookup"><span data-stu-id="6e238-120">Permissions</span></span>
- <span data-ttu-id="6e238-121">Porty</span><span class="sxs-lookup"><span data-stu-id="6e238-121">Ports</span></span>
- <span data-ttu-id="6e238-122">Listy Access Control systemu Windows (ACL)</span><span class="sxs-lookup"><span data-stu-id="6e238-122">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="6e238-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="6e238-123">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="6e238-124">Kryptografia systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6e238-124">Windows Cryptography</span></span>
- <span data-ttu-id="6e238-125">Dziennik zdarzeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6e238-125">Windows EventLog</span></span>
- <span data-ttu-id="6e238-126">Instrumentacja zarządzania Windows (WMI)</span><span class="sxs-lookup"><span data-stu-id="6e238-126">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="6e238-127">Liczniki wydajności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6e238-127">Windows Performance Counters</span></span>
- <span data-ttu-id="6e238-128">Rejestr systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6e238-128">Windows Registry</span></span>
- <span data-ttu-id="6e238-129">Buforowanie środowisko wykonawcze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6e238-129">Windows Runtime Caching</span></span>
- <span data-ttu-id="6e238-130">Usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6e238-130">Windows Services</span></span>

<span data-ttu-id="6e238-131">Aby uzyskać więcej informacji, zobacz [specyfikację pakietu zgodności](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="6e238-131">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="6e238-132">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="6e238-132">Get started</span></span>

1. <span data-ttu-id="6e238-133">Przed przystąpieniem do przenoszenia upewnij się, że Przyjrzyj się [procesowi przenoszenia](index.md).</span><span class="sxs-lookup"><span data-stu-id="6e238-133">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="6e238-134">Podczas przenoszenia istniejącego kodu do programu .NET Core lub .NET Standard Zainstaluj pakiet NuGet [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="6e238-134">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="6e238-135">Jeśli chcesz pozostać w systemie Windows, wszystko jest gotowe.</span><span class="sxs-lookup"><span data-stu-id="6e238-135">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="6e238-136">Jeśli chcesz uruchomić aplikację .NET Core lub bibliotekę .NET Standard w systemie Linux lub macOS, użyj [analizatora interfejsów API](../../standard/analyzers/api-analyzer.md) , aby znaleźć użycie interfejsów API, które nie będą działać na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="6e238-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="6e238-137">Usuń użycie tych interfejsów API, zastąp je niektórymi alternatywami dla wielu platform lub zapoznaj się z nimi przy użyciu sprawdzenia platformy, takiego jak:</span><span class="sxs-lookup"><span data-stu-id="6e238-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

<span data-ttu-id="6e238-138">Aby zapoznać się z pokazem, zapoznaj się z [tematem wideo Channel 9 pakietu zgodności systemu Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="6e238-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
