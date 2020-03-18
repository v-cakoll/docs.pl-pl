---
title: Kierowanie na wiele platform dla bibliotek .NET
description: Najlepsze zalecenia dotyczące tworzenia bibliotek platformy .NET między platformami.
ms.date: 08/12/2019
ms.openlocfilehash: 61adff3759984554bb83531b4f9d8a49e29c929c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731460"
---
# <a name="cross-platform-targeting"></a><span data-ttu-id="164a6-103">Obsługiwane rozwiązania międzyplatformowe</span><span class="sxs-lookup"><span data-stu-id="164a6-103">Cross-platform targeting</span></span>

<span data-ttu-id="164a6-104">Nowoczesny program .NET obsługuje wiele systemów operacyjnych i urządzeń.</span><span class="sxs-lookup"><span data-stu-id="164a6-104">Modern .NET supports multiple operating systems and devices.</span></span> <span data-ttu-id="164a6-105">Ważne jest, aby biblioteki typu open source platformy .NET obsługiwały jak najwięcej deweloperów, niezależnie od tego, czy tworzą witrynę sieci Web ASP.NET hostowane na platformie Azure, czy grę .NET w unity.</span><span class="sxs-lookup"><span data-stu-id="164a6-105">It's important for .NET open-source libraries to support as many developers as possible, whether they're building an ASP.NET website hosted in Azure, or a .NET game in Unity.</span></span>

## <a name="net-standard"></a><span data-ttu-id="164a6-106">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="164a6-106">.NET Standard</span></span>

<span data-ttu-id="164a6-107">.NET Standard to najlepszy sposób dodawania obsługi między platformami do biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="164a6-107">.NET Standard is the best way to add cross-platform support to a .NET library.</span></span> <span data-ttu-id="164a6-108">[.NET Standard](../net-standard.md) to specyfikacja interfejsów API .NET, które są dostępne we wszystkich implementacjach .NET.</span><span class="sxs-lookup"><span data-stu-id="164a6-108">[.NET Standard](../net-standard.md) is a specification of .NET APIs that are available on all .NET implementations.</span></span> <span data-ttu-id="164a6-109">Kierowanie .NET Standard umożliwia tworzenie bibliotek, które są ograniczone do używania interfejsów API, które znajdują się w danej wersji .NET Standard, co oznacza, że jest używany przez wszystkie platformy, które implementują tę wersję standardu .NET.</span><span class="sxs-lookup"><span data-stu-id="164a6-109">Targeting .NET Standard lets you produce libraries that are constrained to use APIs that are in a given version of .NET Standard, which means it's usable by all platforms that implement that version of the .NET Standard.</span></span>

<span data-ttu-id="164a6-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span><span class="sxs-lookup"><span data-stu-id="164a6-110">![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")</span></span>

<span data-ttu-id="164a6-111">Kierowanie na .NET Standard i pomyślne kompilowanie projektu nie gwarantuje, że biblioteka zostanie pomyślnie uruchomiony na wszystkich platformach:</span><span class="sxs-lookup"><span data-stu-id="164a6-111">Targeting .NET Standard, and successfully compiling your project, doesn't guarantee the library will run successfully on all platforms:</span></span>

1. <span data-ttu-id="164a6-112">Interfejsy API specyficzne dla platformy nie powiedzie się na innych platformach.</span><span class="sxs-lookup"><span data-stu-id="164a6-112">Platform-specific APIs will fail on other platforms.</span></span> <span data-ttu-id="164a6-113">Na przykład <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> zakończy się powodzeniem <xref:System.PlatformNotSupportedException> w systemie Windows i wyrzuci, gdy jest używany w innych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="164a6-113">For example, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> will succeed on Windows and throw <xref:System.PlatformNotSupportedException> when used on any other OS.</span></span>
2. <span data-ttu-id="164a6-114">Interfejsy API mogą zachowywać się inaczej.</span><span class="sxs-lookup"><span data-stu-id="164a6-114">APIs can behave differently.</span></span> <span data-ttu-id="164a6-115">Na przykład interfejsy API odbicia mają różne właściwości wydajności, gdy aplikacja używa kompilacji z wyprzedzeniem w iOS lub UWP.</span><span class="sxs-lookup"><span data-stu-id="164a6-115">For example, reflection APIs have different performance characteristics when an application uses ahead-of-time compilation on iOS or UWP.</span></span>

> [!TIP]
> <span data-ttu-id="164a6-116">Zespół .NET [oferuje analizator Roslyn,](../analyzers/api-analyzer.md) który pomoże Ci wykryć możliwe problemy.</span><span class="sxs-lookup"><span data-stu-id="164a6-116">The .NET team [offers a Roslyn analyzer](../analyzers/api-analyzer.md) to help you discover possible issues.</span></span>

<span data-ttu-id="164a6-117">✔️ zacząć od `netstandard2.0` włączenia celu.</span><span class="sxs-lookup"><span data-stu-id="164a6-117">✔️ DO start with including a `netstandard2.0` target.</span></span>

> <span data-ttu-id="164a6-118">Większość bibliotek ogólnego przeznaczenia nie powinna potrzebować interfejsów API poza standardem .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="164a6-118">Most general-purpose libraries should not need APIs outside of .NET Standard 2.0.</span></span> <span data-ttu-id="164a6-119">.NET Standard 2.0 jest obsługiwany przez wszystkie nowoczesne platformy i jest zalecanym sposobem obsługi wielu platform z jednym celem.</span><span class="sxs-lookup"><span data-stu-id="164a6-119">.NET Standard 2.0 is supported by all modern platforms and is the recommended way to support multiple platforms with one target.</span></span>

<span data-ttu-id="164a6-120">❌UNIKAJ w `netstandard1.x` tym cel.</span><span class="sxs-lookup"><span data-stu-id="164a6-120">❌ AVOID including a `netstandard1.x` target.</span></span>

> <span data-ttu-id="164a6-121">.NET Standard 1.x jest rozprowadzany jako szczegółowy zestaw pakietów NuGet, który tworzy wykres zależności dużego pakietu i powoduje, że deweloperzy pobierają wiele pakietów podczas tworzenia.</span><span class="sxs-lookup"><span data-stu-id="164a6-121">.NET Standard 1.x is distributed as a granular set of NuGet packages, which creates a large package dependency graph and results in developers downloading a lot of packages when building.</span></span> <span data-ttu-id="164a6-122">Nowoczesne platformy .NET, w tym .NET Framework 4.6.1, UWP i Xamarin, obsługują wszystko .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="164a6-122">Modern .NET platforms, including .NET Framework 4.6.1, UWP and Xamarin, all support .NET Standard 2.0.</span></span> <span data-ttu-id="164a6-123">Należy kierować tylko .NET Standard 1.x, jeśli w szczególności trzeba kierować starszej platformy.</span><span class="sxs-lookup"><span data-stu-id="164a6-123">You should only target .NET Standard 1.x if you specifically need to target an older platform.</span></span>

<span data-ttu-id="164a6-124">✔️ do `netstandard2.0` zawierać cel, `netstandard1.x` jeśli potrzebujesz celu.</span><span class="sxs-lookup"><span data-stu-id="164a6-124">✔️ DO include a `netstandard2.0` target if you require a `netstandard1.x` target.</span></span>

> <span data-ttu-id="164a6-125">Wszystkie platformy obsługujące .NET Standard `netstandard2.0` 2.0 użyje docelowego i korzyści z posiadania mniejszego wykresu pakietu, podczas gdy starsze platformy będą nadal działać i wrócić do korzystania z `netstandard1.x` obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="164a6-125">All platforms supporting .NET Standard 2.0 will use the `netstandard2.0` target and benefit from having a smaller package graph while older platforms will still work and fall back to using the `netstandard1.x` target.</span></span>

<span data-ttu-id="164a6-126">❌NIE należy dołączać do standardu .NET, jeśli biblioteka opiera się na modelu aplikacji specyficznedla platformy.</span><span class="sxs-lookup"><span data-stu-id="164a6-126">❌ DO NOT include a .NET Standard target if the library relies on a platform-specific app model.</span></span>

> <span data-ttu-id="164a6-127">Na przykład biblioteka zestawu narzędzi kontroli platformy uwp zależy od modelu aplikacji, który jest dostępny tylko na platformie UWP.</span><span class="sxs-lookup"><span data-stu-id="164a6-127">For example, a UWP control toolkit library depends on an app model that is only available on UWP.</span></span> <span data-ttu-id="164a6-128">Interfejsy API specyficzne dla modelu aplikacji nie będą dostępne w standardzie .NET.</span><span class="sxs-lookup"><span data-stu-id="164a6-128">App model specific APIs will not be available in .NET Standard.</span></span>

## <a name="multi-targeting"></a><span data-ttu-id="164a6-129">Kierowanie na wiele</span><span class="sxs-lookup"><span data-stu-id="164a6-129">Multi-targeting</span></span>

<span data-ttu-id="164a6-130">Czasami trzeba uzyskać dostęp do interfejsów API specyficznych dla struktury z bibliotek.</span><span class="sxs-lookup"><span data-stu-id="164a6-130">Sometimes you need to access framework-specific APIs from your libraries.</span></span> <span data-ttu-id="164a6-131">Najlepszym sposobem wywoływania interfejsów API specyficzne dla struktury jest przy użyciu wielu miejsc docelowych, który tworzy projekt dla wielu [platform docelowych .NET,](../frameworks.md) a nie tylko dla jednego.</span><span class="sxs-lookup"><span data-stu-id="164a6-131">The best way to call framework-specific APIs is using multi-targeting, which builds your project for many [.NET target frameworks](../frameworks.md) rather than for just one.</span></span>

<span data-ttu-id="164a6-132">Aby chronić konsumentów przed konieczności tworzenia dla poszczególnych struktur, należy dążyć do .NET standard danych wyjściowych oraz jeden lub więcej danych wyjściowych specyficznych dla struktury.</span><span class="sxs-lookup"><span data-stu-id="164a6-132">To shield your consumers from having to build for individual frameworks, you should strive to have a .NET Standard output plus one or more framework-specific outputs.</span></span> <span data-ttu-id="164a6-133">Z wielu określania wartości, wszystkie zestawy są pakowane wewnątrz jednego pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="164a6-133">With multi-targeting, all assemblies are packaged inside a single NuGet package.</span></span> <span data-ttu-id="164a6-134">Konsumenci mogą następnie odwoływać się do tego samego pakietu i NuGet wybierze odpowiednią implementację.</span><span class="sxs-lookup"><span data-stu-id="164a6-134">Consumers can then reference the same package and NuGet will pick the appropriate implementation.</span></span> <span data-ttu-id="164a6-135">Biblioteka .NET Standard służy jako rezerwowej biblioteki, która jest używana wszędzie, z wyjątkiem przypadków, w których pakiet NuGet oferuje implementacji specyficzne dla struktury.</span><span class="sxs-lookup"><span data-stu-id="164a6-135">Your .NET Standard library serves as the fallback library that is used everywhere, except for the cases where your NuGet package offers a framework-specific implementation.</span></span> <span data-ttu-id="164a6-136">Multi-targetowanie umożliwia użycie kompilacji warunkowej w kodzie i wywołać interfejsy API specyficzne dla struktury.</span><span class="sxs-lookup"><span data-stu-id="164a6-136">Multi-targeting allows you to use conditional compilation in your code and call framework-specific APIs.</span></span>

<span data-ttu-id="164a6-137">![Pakiet NuGet z wieloma zestawami](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Pakiet NuGet z wieloma zestawami")</span><span class="sxs-lookup"><span data-stu-id="164a6-137">![NuGet package with multiple assemblies](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "NuGet package with multiple assemblies")</span></span>

<span data-ttu-id="164a6-138">✔️ ROZWAŻ kierowanie implementacji .NET oprócz .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="164a6-138">✔️ CONSIDER targeting .NET implementations in addition to .NET Standard.</span></span>

> <span data-ttu-id="164a6-139">Kierowanie na implementacje .NET umożliwia wywołanie interfejsów API specyficznych dla platformy, które znajdują się poza standardem .NET.</span><span class="sxs-lookup"><span data-stu-id="164a6-139">Targeting .NET implementations allows you to call platform-specific APIs that are outside of .NET Standard.</span></span>
>
> <span data-ttu-id="164a6-140">Nie należy upuszczać obsługi .NET Standard, gdy to zrobisz.</span><span class="sxs-lookup"><span data-stu-id="164a6-140">Do not drop support for .NET Standard when you do this.</span></span> <span data-ttu-id="164a6-141">Zamiast tego należy wyrzucić z implementacji i oferują możliwości interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="164a6-141">Instead, throw from the implementation and offer capability APIs.</span></span> <span data-ttu-id="164a6-142">W ten sposób biblioteki można używać w dowolnym miejscu i obsługuje uruchamianie funkcji.</span><span class="sxs-lookup"><span data-stu-id="164a6-142">This way, your library can be used anywhere and supports runtime light-up of features.</span></span>

```csharp
public static class GpsLocation
{
    // This project uses multi-targeting to expose device-specific APIs to .NET Standard.
    public static async Task<(double latitude, double longitude)> GetCoordinatesAsync()
    {
#if NET461
        return CallDotNetFramworkApi();
#elif WINDOWS_UWP
        return CallUwpApi();
#else
        throw new PlatformNotSupportedException();
#endif
    }

    // Allows callers to check without having to catch PlatformNotSupportedException
    // or replicating the OS check.
    public static bool IsSupported
    {
        get
        {
#if NET461 || WINDOWS_UWP
            return true;
#else
            return false;
#endif
        }
    }
}
```

<span data-ttu-id="164a6-143">❌Unikaj wielu celów, a także kierowania .NET Standard, jeśli kod źródłowy jest taki sam dla wszystkich obiektów docelowych.</span><span class="sxs-lookup"><span data-stu-id="164a6-143">❌ AVOID multi-targeting as well as targeting .NET Standard, if your source code is the same for all targets.</span></span>

> <span data-ttu-id="164a6-144">Zestaw .NET Standard będzie automatycznie używany przez NuGet.</span><span class="sxs-lookup"><span data-stu-id="164a6-144">The .NET Standard assembly will automatically be used by NuGet.</span></span> <span data-ttu-id="164a6-145">Kierowanie na poszczególne implementacje .NET zwiększa rozmiar bez `*.nupkg` korzyści.</span><span class="sxs-lookup"><span data-stu-id="164a6-145">Targeting individual .NET implementations increases the `*.nupkg` size for no benefit.</span></span>

<span data-ttu-id="164a6-146">✔️ ROZWAŻ dodanie `net461` celu, gdy oferujesz `netstandard2.0` cel.</span><span class="sxs-lookup"><span data-stu-id="164a6-146">✔️ CONSIDER adding a target for `net461` when you're offering a `netstandard2.0` target.</span></span>

> <span data-ttu-id="164a6-147">Przy użyciu .NET Standard 2.0 z .NET Framework ma pewne problemy, które zostały rozwiązane w .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="164a6-147">Using .NET Standard 2.0 from .NET Framework has some issues that were addressed in .NET Framework 4.7.2.</span></span> <span data-ttu-id="164a6-148">Można poprawić środowisko dla deweloperów, które są nadal na .NET Framework 4.6.1 - 4.7.1, oferując im plik binarny, który jest zbudowany dla .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="164a6-148">You can improve the experience for developers that are still on .NET Framework 4.6.1 - 4.7.1 by offering them a binary that is built for .NET Framework 4.6.1.</span></span>

<span data-ttu-id="164a6-149">✔️ dystrybuują biblioteki przy użyciu pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="164a6-149">✔️ DO distribute your library using a NuGet package.</span></span>

> <span data-ttu-id="164a6-150">NuGet wybierze najlepszy cel dla dewelopera i osłonić je konieczności wybrania odpowiedniej implementacji.</span><span class="sxs-lookup"><span data-stu-id="164a6-150">NuGet will select the best target for the developer and shield them having to pick the appropriate implementation.</span></span>

<span data-ttu-id="164a6-151">✔️ DO używać `TargetFrameworks` właściwości pliku projektu podczas wielu kierowania.</span><span class="sxs-lookup"><span data-stu-id="164a6-151">✔️ DO use a project file's `TargetFrameworks` property when multi-targeting.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="164a6-152">✔️ ZAStanów się przy użyciu [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) podczas wielu kierowania na platformę Uniwersalną systemu UWP i xamarin, ponieważ znacznie upraszcza plik projektu.</span><span class="sxs-lookup"><span data-stu-id="164a6-152">✔️ CONSIDER using [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) when multi-targeting for UWP and Xamarin as it greatly simplifies your project file.</span></span>

## <a name="older-targets"></a><span data-ttu-id="164a6-153">Starsze cele</span><span class="sxs-lookup"><span data-stu-id="164a6-153">Older targets</span></span>

<span data-ttu-id="164a6-154">.NET obsługuje wersje docelowe platformy .NET Framework, które są długo poza obsługą, a także platform, które nie są już powszechnie używane.</span><span class="sxs-lookup"><span data-stu-id="164a6-154">.NET supports targeting versions of the .NET Framework that are long out of support as well as platforms that are no longer commonly used.</span></span> <span data-ttu-id="164a6-155">Chociaż istnieje wartość w tworzeniu pracy biblioteki na jak najwięcej obiektów docelowych, jak to możliwe, konieczności obejścia brakujących interfejsów API można dodać znaczne obciążenie.</span><span class="sxs-lookup"><span data-stu-id="164a6-155">While there's value in making your library work on as many targets as possible, having to work around missing APIs can add significant overhead.</span></span> <span data-ttu-id="164a6-156">Uważamy, że niektóre ramy nie są już warte ukierunkowania, biorąc pod uwagę ich zasięg i ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="164a6-156">We believe certain frameworks are no longer worth targeting, considering their reach and limitations.</span></span>

<span data-ttu-id="164a6-157">❌NIE należy dołączać obiektu docelowego przenośnej biblioteki klas (PCL).</span><span class="sxs-lookup"><span data-stu-id="164a6-157">❌ DO NOT include a Portable Class Library (PCL) target.</span></span> <span data-ttu-id="164a6-158">Na przykład `portable-net45+win8+wpa81+wp8`.</span><span class="sxs-lookup"><span data-stu-id="164a6-158">For example, `portable-net45+win8+wpa81+wp8`.</span></span>

> <span data-ttu-id="164a6-159">.NET Standard to nowoczesny sposób obsługi wieloplatformowych bibliotek .NET i zastępowania list PCL.</span><span class="sxs-lookup"><span data-stu-id="164a6-159">.NET Standard is the modern way to support cross-platform .NET libraries and replaces PCLs.</span></span>

<span data-ttu-id="164a6-160">❌NIE należy uwzględniać obiektów docelowych dla platform .NET, które nie są już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="164a6-160">❌ DO NOT include targets for .NET platforms that are no longer supported.</span></span> <span data-ttu-id="164a6-161">Na przykład `SL4` `WP`, .</span><span class="sxs-lookup"><span data-stu-id="164a6-161">For example, `SL4`, `WP`.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="164a6-162">[Poprzedni](get-started.md)
>[następny](strong-naming.md)</span><span class="sxs-lookup"><span data-stu-id="164a6-162">[Previous](get-started.md)
[Next](strong-naming.md)</span></span>
