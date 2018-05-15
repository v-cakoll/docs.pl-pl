---
title: Eksportowanie do platformy .NET Core - przy użyciu pakietu zgodności systemu Windows
description: Więcej informacji na temat pakietu zgodności systemu Windows i jak można go używać do portu istniejącego kodu .NET Framework do platformy .NET Core
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.openlocfilehash: 6b25a2d5c197a6c9b0a7ead18370870ddc091e1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-windows-compatibility-pack"></a><span data-ttu-id="b9367-103">Przy użyciu pakietu zgodności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b9367-103">Using the Windows Compatibility Pack</span></span>

<span data-ttu-id="b9367-104">Jednym z najbardziej typowe problemy, które deweloperzy stają przed podczas przenoszenia ich istniejącego kodu do platformy .NET Core jest ich są zależne od interfejsów API i technologie, które istnieją tylko w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9367-104">One of the most common issues that developers face when porting their existing code to .NET Core is that they depend on APIs and technologies that only exist in the .NET Framework.</span></span> <span data-ttu-id="b9367-105">*Pakiet zgodności systemu Windows* jest o wiele z tych technologii zapewnienie, że tworzenie aplikacji platformy .NET Core, a także bibliotek .NET Standard staje się bardziej mogą zostać wykorzystane do istniejącego kodu.</span><span class="sxs-lookup"><span data-stu-id="b9367-105">The *Windows Compatibility Pack* is about providing many of these technologies so that building .NET Core applications as well as .NET Standard libraries becomes much more viable for existing code.</span></span>

<span data-ttu-id="b9367-106">Ten pakiet jest logiczną [rozszerzenia .NET 2.0 standardowe](../whats-new/index.md#api-changes-and-library-support) czy znacznie zwiększa zestawu interfejsów API i istniejący kod kompiluje z prawie żadnych modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="b9367-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/index.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="b9367-107">Aby zapewnić promise .NET Standard, ale ("jest zestaw interfejsów API, które zapewniają wszystkich implementacji .NET"), to nie zostały uwzględnione technologie, które nie może działać na wszystkich platformach, takich jak rejestru Instrumentacji zarządzania Windows (WMI) lub emisja odbicia Interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="b9367-107">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="b9367-108">*Pakiet zgodności systemu Windows* znajduje się na szczycie .NET Standard i zapewnia dostęp do technologii, które są tylko systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b9367-108">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="b9367-109">Jest to szczególnie przydatne dla użytkowników, którzy mają zostać przeniesione do platformy .NET Core, ale planu, aby zachować zgodność z systemem Windows jako pierwszy krok.</span><span class="sxs-lookup"><span data-stu-id="b9367-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="b9367-110">W tym scenariuszu nie będzie mógł korzystać z technologii systemu Windows jest tylko próg migracji wykluczający się o zerowej architektury korzyści.</span><span class="sxs-lookup"><span data-stu-id="b9367-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="b9367-111">Zawartość pakietu</span><span class="sxs-lookup"><span data-stu-id="b9367-111">Package contents</span></span>

<span data-ttu-id="b9367-112">*Pakiet zgodności systemu Windows* zostaną przekazane za pośrednictwem pakietu NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) i może być przywoływany w projektach przeznaczonych dla platformy .NET Core lub .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="b9367-112">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="b9367-113">Zapewnia około 20 000 interfejsów API, łącznie z interfejsów API systemu Windows, jak również między platformami z następujących obszarów technologii:</span><span class="sxs-lookup"><span data-stu-id="b9367-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="b9367-114">Strony kodowe</span><span class="sxs-lookup"><span data-stu-id="b9367-114">Code Pages</span></span>
* <span data-ttu-id="b9367-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="b9367-115">CodeDom</span></span>
* <span data-ttu-id="b9367-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="b9367-116">Configuration</span></span>
* <span data-ttu-id="b9367-117">Usługi katalogowe</span><span class="sxs-lookup"><span data-stu-id="b9367-117">Directory Services</span></span>
* <span data-ttu-id="b9367-118">Rysowanie</span><span class="sxs-lookup"><span data-stu-id="b9367-118">Drawing</span></span>
* <span data-ttu-id="b9367-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="b9367-119">ODBC</span></span>
* <span data-ttu-id="b9367-120">Uprawnienia</span><span class="sxs-lookup"><span data-stu-id="b9367-120">Permissions</span></span>
* <span data-ttu-id="b9367-121">Porty</span><span class="sxs-lookup"><span data-stu-id="b9367-121">Ports</span></span>
* <span data-ttu-id="b9367-122">Listy kontroli dostępu do systemu Windows (ACL)</span><span class="sxs-lookup"><span data-stu-id="b9367-122">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="b9367-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="b9367-123">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="b9367-124">Kryptografia systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b9367-124">Windows Cryptography</span></span>
* <span data-ttu-id="b9367-125">Dziennik zdarzeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b9367-125">Windows EventLog</span></span>
* <span data-ttu-id="b9367-126">Instrumentacja zarządzania Windows (WMI)</span><span class="sxs-lookup"><span data-stu-id="b9367-126">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="b9367-127">Liczniki wydajności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b9367-127">Windows Performance Counters</span></span>
* <span data-ttu-id="b9367-128">Rejestr systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b9367-128">Windows Registry</span></span>
* <span data-ttu-id="b9367-129">Buforowanie środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b9367-129">Windows Runtime Caching</span></span>
* <span data-ttu-id="b9367-130">Usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b9367-130">Windows Services</span></span>

<span data-ttu-id="b9367-131">Aby uzyskać więcej informacji, zobacz [specyfikacji pakietu zgodności](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="b9367-131">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="b9367-132">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="b9367-132">Get started</span></span>

1. <span data-ttu-id="b9367-133">Przed eksportowanie, upewnij się, że Przyjrzyjmy się [eksportowanie procesu](index.md).</span><span class="sxs-lookup"><span data-stu-id="b9367-133">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="b9367-134">Podczas przenoszenia istniejącego kodu platformy .NET Core lub .NET Standard, zainstaluj pakiet NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="b9367-134">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="b9367-135">Jeśli chcesz zachować zgodność z systemem Windows, wszystko jest gotowe.</span><span class="sxs-lookup"><span data-stu-id="b9367-135">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="b9367-136">Uruchamianie aplikacji .NET Core i biblioteki .NET Standard w systemie Linux lub macOS, należy użyć [analizator interfejsu API](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) można znaleźć użycia interfejsów API, które nie będą działać na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="b9367-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="b9367-137">Usuń użycia tych interfejsów API, Zamień alternatyw i platform lub zabezpieczenia je za pomocą wyboru platform, takich jak:</span><span class="sxs-lookup"><span data-stu-id="b9367-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="b9367-138">Dla demonstrację, zapoznaj się z [wideo z witryny Channel 9 pakietu zgodności systemu Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="b9367-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

