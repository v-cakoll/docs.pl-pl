---
title: Użyj pakietu zgodności systemu Windows do portu kodu do .NET Core
description: Dowiedz się więcej o pakiecie zgodności systemu Windows i o tym, jak można go używać do przenoszenia istniejącego kodu .NET Framework do .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 91a653b2345d414c18ebdb6e8b7d6d49bbdbb83e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733613"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="555d1-103">Użyj pakietu zgodności systemu Windows do portu kodu do .NET Core</span><span class="sxs-lookup"><span data-stu-id="555d1-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="555d1-104">Niektóre z najczęstszych problemów znalezionych podczas przenoszenia istniejącego kodu do .NET Core są zależności od interfejsów API i technologii, które znajdują się tylko w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="555d1-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="555d1-105">*Pakiet zgodności systemu Windows* zawiera wiele z tych technologii, dlatego znacznie łatwiej jest tworzyć aplikacje .NET Core i biblioteki .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="555d1-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="555d1-106">Pakiet zgodności jest logicznym [rozszerzeniem .NET Standard 2.0,](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) które znacznie zwiększa zestaw interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="555d1-106">The compatibility pack is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases the API set.</span></span> <span data-ttu-id="555d1-107">Istniejący kod kompiluje się prawie bez żadnych modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="555d1-107">Existing code compiles with almost no modifications.</span></span> <span data-ttu-id="555d1-108">Aby dotrzymać obietnicy "zestawu interfejsów API, które zapewniają wszystkie implementacje .NET", .NET Standard nie zawiera technologii, które nie mogą działać na wszystkich platformach, takich jak rejestr, Instrumentacja zarządzania Windows (WMI) lub odbicie emitują interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="555d1-108">To keep its promise of "the set of APIs that all .NET implementations provide", .NET Standard doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span> <span data-ttu-id="555d1-109">Pakiet zgodności systemu Windows znajduje się na platformie .NET Standard i zapewnia dostęp do tych technologii tylko dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="555d1-109">The Windows Compatibility Pack sits on top of .NET Standard and provides access to these Windows-only technologies.</span></span> <span data-ttu-id="555d1-110">Jest to szczególnie przydatne dla klientów, którzy chcą przenieść się do .NET Core, ale planują pozostać w systemie Windows, przynajmniej w pierwszym kroku.</span><span class="sxs-lookup"><span data-stu-id="555d1-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows, at least as a first step.</span></span> <span data-ttu-id="555d1-111">W tym scenariuszu możliwość korzystania z technologii tylko systemu Windows usuwa przeszkodę migracji.</span><span class="sxs-lookup"><span data-stu-id="555d1-111">In that scenario, being able to use Windows-only technologies removes the migration hurdle.</span></span>

## <a name="package-contents"></a><span data-ttu-id="555d1-112">Zawartość pakietu</span><span class="sxs-lookup"><span data-stu-id="555d1-112">Package contents</span></span>

<span data-ttu-id="555d1-113">Pakiet zgodności systemu Windows jest dostarczany za pośrednictwem [pakietu Microsoft.Windows.Compatibility NuGet](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) i można się do niego odwoływać z projektów docelowych .NET Core lub .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="555d1-113">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET Core or .NET Standard.</span></span>

<span data-ttu-id="555d1-114">Zapewnia około 20 000 interfejsów API, w tym interfejsy API tylko dla systemu Windows, a także międzyplatformowe interfejsy API z następujących obszarów technologicznych:</span><span class="sxs-lookup"><span data-stu-id="555d1-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="555d1-115">Strony kodowe</span><span class="sxs-lookup"><span data-stu-id="555d1-115">Code Pages</span></span>
- <span data-ttu-id="555d1-116">Codedom</span><span class="sxs-lookup"><span data-stu-id="555d1-116">CodeDom</span></span>
- <span data-ttu-id="555d1-117">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="555d1-117">Configuration</span></span>
- <span data-ttu-id="555d1-118">Usługi katalogowe</span><span class="sxs-lookup"><span data-stu-id="555d1-118">Directory Services</span></span>
- <span data-ttu-id="555d1-119">Rysowanie</span><span class="sxs-lookup"><span data-stu-id="555d1-119">Drawing</span></span>
- <span data-ttu-id="555d1-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="555d1-120">ODBC</span></span>
- <span data-ttu-id="555d1-121">Uprawnienia</span><span class="sxs-lookup"><span data-stu-id="555d1-121">Permissions</span></span>
- <span data-ttu-id="555d1-122">Porty</span><span class="sxs-lookup"><span data-stu-id="555d1-122">Ports</span></span>
- <span data-ttu-id="555d1-123">Listy kontroli dostępu systemu Windows (ACL)</span><span class="sxs-lookup"><span data-stu-id="555d1-123">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="555d1-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="555d1-124">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="555d1-125">Kryptografia systemu Windows</span><span class="sxs-lookup"><span data-stu-id="555d1-125">Windows Cryptography</span></span>
- <span data-ttu-id="555d1-126">Dziennik zdarzeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="555d1-126">Windows EventLog</span></span>
- <span data-ttu-id="555d1-127">Instrumentacja zarządzania Windows (WMI)</span><span class="sxs-lookup"><span data-stu-id="555d1-127">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="555d1-128">Liczniki wydajności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="555d1-128">Windows Performance Counters</span></span>
- <span data-ttu-id="555d1-129">Rejestr systemu Windows</span><span class="sxs-lookup"><span data-stu-id="555d1-129">Windows Registry</span></span>
- <span data-ttu-id="555d1-130">Buforowanie środowiska uruchomieniowe systemu Windows</span><span class="sxs-lookup"><span data-stu-id="555d1-130">Windows Runtime Caching</span></span>
- <span data-ttu-id="555d1-131">Usługi systemu Windows</span><span class="sxs-lookup"><span data-stu-id="555d1-131">Windows Services</span></span>

<span data-ttu-id="555d1-132">Aby uzyskać więcej informacji, zobacz [specyfikację pakietu zgodności](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="555d1-132">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="555d1-133">Rozpoczęcie pracy</span><span class="sxs-lookup"><span data-stu-id="555d1-133">Get started</span></span>

1. <span data-ttu-id="555d1-134">Przed przeniesieniem należy zapoznać się z [procesem przenoszenia](index.md).</span><span class="sxs-lookup"><span data-stu-id="555d1-134">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="555d1-135">Podczas przenoszenia istniejącego kodu do .NET Core lub .NET Standard zainstaluj [pakiet Microsoft.Windows.Compatibility NuGet](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="555d1-135">When porting existing code to .NET Core or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="555d1-136">Jeśli chcesz pozostać w systemie Windows, wszystko jest ustawione.</span><span class="sxs-lookup"><span data-stu-id="555d1-136">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="555d1-137">Jeśli chcesz uruchomić aplikację .NET Core lub bibliotekę .NET Standard w systemie Linux lub macOS, użyj [analizatora interfejsu API,](../../standard/analyzers/api-analyzer.md) aby znaleźć użycie interfejsów API, które nie będą działać między platformami.</span><span class="sxs-lookup"><span data-stu-id="555d1-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="555d1-138">Usuń użycie tych interfejsów API, zastąp je alternatywami między platformami lub stróżuj je za pomocą sprawdzania platformy, takich jak:</span><span class="sxs-lookup"><span data-stu-id="555d1-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="555d1-139">Aby zapoznać się z pokazem, obejrzyj [film wideo kanału 9 pakietu zgodności systemu Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="555d1-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
