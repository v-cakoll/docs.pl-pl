---
title: Użyj pakietu Windows zgodności do portu kodu platformy .NET Core
description: Więcej informacji na temat pakietu Windows zgodności i jak można jej używać do portu istniejącego kodu .NET Framework i .NET Core
author: terrajobst
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 09c5533dbc46d16585b7f3cbfd2a3a70819ceb75
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903747"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="a793c-103">Użyj pakietu Windows zgodności do portu kodu platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="a793c-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="a793c-104">Niektóre z najczęściej spotykanych problemów podczas przenosisz istniejący kod do programu .NET Core są zależności o interfejsach API i technologii, które znajdują się tylko w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a793c-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in the .NET Framework.</span></span> <span data-ttu-id="a793c-105">*Systemie Windows Compatibility Pack* zapewnie wiele z tych technologii, więc jest znacznie łatwiejsze tworzenie aplikacji .NET Core i biblioteki .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="a793c-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="a793c-106">Ten pakiet jest wartość logiczna [rozszerzenia .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) , znacznie zwiększa zestawu interfejsów API i istniejący kod kompiluje bez niemal żadnych modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="a793c-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="a793c-107">Aby zachować obietnicy .NET Standard, ale ("to zbiór interfejsów API, które zapewniają wszystkich implementacji .NET"), to nie zostały uwzględnione technologie, które nie może działać na wszystkich platformach, takich jak rejestru, Instrumentacji zarządzania Windows (WMI) lub emisji odbicia Interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="a793c-107">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="a793c-108">*Systemie Windows Compatibility Pack* znajduje się na szczycie .NET Standard i zapewnia dostęp do technologii, które są tylko Windows.</span><span class="sxs-lookup"><span data-stu-id="a793c-108">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="a793c-109">Jest to szczególnie przydatne w przypadku klientów, które chcesz przenieść do platformy .NET Core, ale plan pozostanie w Windows jako pierwszy krok.</span><span class="sxs-lookup"><span data-stu-id="a793c-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="a793c-110">W tym scenariuszu nie będzie mógł korzystać z technologii Windows tylko jest tylko próg migracji wykluczający się zero zalety architektury.</span><span class="sxs-lookup"><span data-stu-id="a793c-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="a793c-111">Zawartość pakietu</span><span class="sxs-lookup"><span data-stu-id="a793c-111">Package contents</span></span>

<span data-ttu-id="a793c-112">*Systemie Windows Compatibility Pack* znajduje się za pośrednictwem pakietu NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) i mogą być przywoływane z projektów przeznaczonych dla platformy .NET Core lub .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="a793c-112">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="a793c-113">Zapewnia około 20 000 interfejsów API, tylko do Windows, a także dla wielu platform interfejsów API z następujących obszarów technologii w tym:</span><span class="sxs-lookup"><span data-stu-id="a793c-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="a793c-114">Strony kodowe</span><span class="sxs-lookup"><span data-stu-id="a793c-114">Code Pages</span></span>
* <span data-ttu-id="a793c-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="a793c-115">CodeDom</span></span>
* <span data-ttu-id="a793c-116">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a793c-116">Configuration</span></span>
* <span data-ttu-id="a793c-117">Usługi katalogowe</span><span class="sxs-lookup"><span data-stu-id="a793c-117">Directory Services</span></span>
* <span data-ttu-id="a793c-118">Rysowanie</span><span class="sxs-lookup"><span data-stu-id="a793c-118">Drawing</span></span>
* <span data-ttu-id="a793c-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="a793c-119">ODBC</span></span>
* <span data-ttu-id="a793c-120">Uprawnienia</span><span class="sxs-lookup"><span data-stu-id="a793c-120">Permissions</span></span>
* <span data-ttu-id="a793c-121">Porty</span><span class="sxs-lookup"><span data-stu-id="a793c-121">Ports</span></span>
* <span data-ttu-id="a793c-122">Listy kontroli dostępu systemu Windows (ACL)</span><span class="sxs-lookup"><span data-stu-id="a793c-122">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="a793c-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="a793c-123">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="a793c-124">Windows Cryptography</span><span class="sxs-lookup"><span data-stu-id="a793c-124">Windows Cryptography</span></span>
* <span data-ttu-id="a793c-125">Windows w dzienniku zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a793c-125">Windows EventLog</span></span>
* <span data-ttu-id="a793c-126">Instrumentacja zarządzania Windows (WMI)</span><span class="sxs-lookup"><span data-stu-id="a793c-126">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="a793c-127">Liczniki wydajności Windows</span><span class="sxs-lookup"><span data-stu-id="a793c-127">Windows Performance Counters</span></span>
* <span data-ttu-id="a793c-128">Windows Registry</span><span class="sxs-lookup"><span data-stu-id="a793c-128">Windows Registry</span></span>
* <span data-ttu-id="a793c-129">Buforowanie środowiska uruchomieniowego Windows</span><span class="sxs-lookup"><span data-stu-id="a793c-129">Windows Runtime Caching</span></span>
* <span data-ttu-id="a793c-130">Usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a793c-130">Windows Services</span></span>

<span data-ttu-id="a793c-131">Aby uzyskać więcej informacji, zobacz [specyfikacji pakietu zgodności](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="a793c-131">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="a793c-132">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="a793c-132">Get started</span></span>

1. <span data-ttu-id="a793c-133">Przed przenoszenie, upewnij się, że Przyjrzyj się [proces przenoszenia](index.md).</span><span class="sxs-lookup"><span data-stu-id="a793c-133">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="a793c-134">Jeśli przenosisz istniejący kod platformy .NET Core lub .NET Standard, należy zainstalować pakiet NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="a793c-134">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="a793c-135">Jeśli chcesz pozostać na Windows, wszystko jest gotowe.</span><span class="sxs-lookup"><span data-stu-id="a793c-135">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="a793c-136">Uruchamianie aplikacji .NET Core i biblioteki .NET Standard w systemie Linux lub macOS, należy użyć [analizatora API](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) można znaleźć użycia interfejsów API, które nie będą działać na różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="a793c-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="a793c-137">Usuń użycia tych interfejsów API, zastąp je alternatywy dla wielu platform lub je przed nieprzewidzianymi je za pomocą wyboru platform, takich jak:</span><span class="sxs-lookup"><span data-stu-id="a793c-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="a793c-138">Pokaz, zapoznaj się z [wideo Channel 9 z pakietu zgodności Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="a793c-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
