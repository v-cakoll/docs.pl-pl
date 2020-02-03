---
title: Ukierunkowane na wiele platform dla bibliotek platformy .NET
description: Zalecenia dotyczące najlepszych rozwiązań dotyczących tworzenia bibliotek platformy .NET dla wielu platform.
ms.date: 08/12/2019
ms.openlocfilehash: 61adff3759984554bb83531b4f9d8a49e29c929c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731460"
---
# <a name="cross-platform-targeting"></a>Obsługiwane rozwiązania międzyplatformowe

Nowoczesne środowisko .NET obsługuje wiele systemów operacyjnych i urządzeń. Jest to ważne w przypadku bibliotek typu open source programu .NET do obsługi możliwie największej liczby deweloperów, niezależnie od tego, czy tworzą one witrynę sieci Web ASP.NET hostowaną na platformie Azure, czy też grę z platformą .NET w środowisku Unity.

## <a name="net-standard"></a>.NET Standard

.NET Standard to najlepszy sposób na dodanie obsługi wielu platform do biblioteki .NET. [.NET Standard](../net-standard.md) to specyfikacja interfejsów API platformy .NET, które są dostępne we wszystkich implementacjach platformy .NET. .NET Standard określania wartości docelowej umożliwia tworzenie bibliotek, które są ograniczone do używania interfejsów API w danej wersji .NET Standard, co oznacza, że są one używane przez wszystkie platformy, które implementują tę wersję .NET Standard.

![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

Kierowanie .NET Standard i pomyślne skompilowanie projektu nie gwarantuje, że biblioteka zostanie uruchomiona pomyślnie na wszystkich platformach:

1. Interfejsy API specyficzne dla platformy zakończą się niepowodzeniem na innych platformach. Na przykład <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> zakończy się pomyślnie w systemie Windows i zgłosi <xref:System.PlatformNotSupportedException>, gdy jest używany w innym systemie operacyjnym.
2. Interfejsy API mogą zachowywać się inaczej. Na przykład interfejsy API odbicia mają różne charakterystyki wydajności, gdy aplikacja korzysta z kompilacji przed czasem w systemie iOS lub platformy UWP.

> [!TIP]
> Zespół .NET [oferuje Analizator Roslyn](../analyzers/api-analyzer.md) , który ułatwia odnajdywanie potencjalnych problemów.

✔️ Zacznij od dołączenia do `netstandard2.0` celu.

> Większość bibliotek ogólnego przeznaczenia nie powinna potrzebować interfejsów API poza .NET Standard 2,0. .NET Standard 2,0 jest obsługiwane przez wszystkie nowoczesne platformy i jest zalecanym sposobem obsługi wielu platform z jednym obiektem docelowym.

❌ unikać dołączenia do `netstandard1.x` celu.

> .NET Standard 1. x jest dystrybuowany jako szczegółowy zestaw pakietów NuGet, co tworzy wykres zależności pakietu i umożliwia deweloperom pobieranie dużej liczby pakietów podczas kompilowania. Nowoczesne platformy .NET, w tym .NET Framework 4.6.1, platformy UWP i Xamarin, obsługują .NET Standard 2,0. Należy określić tylko .NET Standard 1. x, jeśli konieczne jest ukierunkowanie starszej platformy.

✔️ NALEŻY uwzględnić docelowy `netstandard2.0`, jeśli jest wymagany element docelowy `netstandard1.x`.

> Wszystkie platformy obsługujące .NET Standard 2,0 będą używać elementu docelowego `netstandard2.0` i korzyści z posiadania mniejszego grafu pakietu, a starsze platformy będą nadal działały i powracają do korzystania z `netstandard1.x` celu.

❌ nie uwzględniać elementu docelowego .NET Standard, jeśli biblioteka korzysta z modelu aplikacji specyficznego dla platformy.

> Na przykład biblioteka zestawu narzędzi platformy UWP Control zależy od modelu aplikacji, który jest dostępny tylko w platformy UWP. Interfejsy API specyficzne dla modelu aplikacji nie będą dostępne w .NET Standard.

## <a name="multi-targeting"></a>Wiele elementów docelowych

Czasami trzeba uzyskać dostęp do interfejsów API specyficznych dla platformy z bibliotek. Najlepszym sposobem wywołania interfejsów API specyficznych dla platformy jest użycie wielu elementów docelowych, które kompilują projekt dla wielu platform [docelowych .NET](../frameworks.md) , a nie tylko dla jednego.

Aby chronić odbiorców przed koniecznością kompilowania dla poszczególnych platform, należy dążyć do uzyskania .NET Standard danych wyjściowych i jednego lub kilku wyjść specyficznych dla platformy. W przypadku wiele elementów docelowych wszystkie zestawy są pakowane w ramach jednego pakietu NuGet. Następnie konsumenci mogą odwoływać się do tego samego pakietu, a pakiet NuGet wybierze odpowiednią implementację. Biblioteka .NET Standard służy jako biblioteka rezerwowa używana wszędzie, z wyjątkiem przypadków, w których pakiet NuGet oferuje implementację specyficzną dla platformy. Wiele elementów docelowych umożliwia użycie kompilacji warunkowej w kodzie i wywołań interfejsów API specyficznych dla platformy.

![Pakiet NuGet z wieloma zestawami](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Pakiet NuGet z wieloma zestawami")

✔️ Rozważ uwzględnienie implementacji platformy .NET oprócz .NET Standard.

> Elementy docelowe implementacji platformy .NET umożliwiają wywoływanie interfejsów API specyficznych dla platformy, które znajdują się poza programem .NET Standard.
>
> Nie porzucaj obsługi .NET Standard, gdy to zrobisz. Zamiast tego należy zgłosić z interfejsów API możliwości implementacji i oferty. Dzięki temu biblioteka może być używana w dowolnym miejscu i obsługuje środowisko uruchomieniowe funkcji.

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

❌ unikać określania elementów docelowych i .NET Standard określania wartości docelowej, jeśli kod źródłowy jest taki sam dla wszystkich obiektów docelowych.

> Zestaw .NET Standard będzie automatycznie używany przez pakiet NuGet. Kierowanie poszczególnych implementacji platformy .NET zwiększa rozmiar `*.nupkg` w przypadku braku korzyści.

✔️ ROZWAŻYĆ dodanie elementu docelowego dla `net461`, gdy oferujesz element docelowy `netstandard2.0`.

> Korzystanie z .NET Standard 2,0 z .NET Framework ma problemy, które zostały rozwiązane w .NET Framework 4.7.2. Możesz poprawić środowisko dla deweloperów, którzy nadal znajdują się w .NET Framework 4.6.1-4.7.1, oferując im plik binarny, który jest skompilowany dla .NET Framework 4.6.1.

✔️ Przeprowadź dystrybucję biblioteki przy użyciu pakietu NuGet.

> Pakiet NuGet wybierze najlepszy cel dla dewelopera i osłonę, aby wybrać odpowiednią implementację.

✔️ Użyj właściwości `TargetFrameworks` pliku projektu podczas wieloelementowego określania wartości docelowej.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

✔️ ROZWAŻYĆ użycie programu [MSBuild. Sdk. Extras](https://github.com/onovotny/MSBuildSdkExtras) , gdy wiele obiektów docelowych dla platformy UWP i Xamarin jest znacznie upraszcza plik projektu.

## <a name="older-targets"></a>Starsze elementy docelowe

Platforma .NET obsługuje docelowe wersje .NET Framework, które są nieobsługiwane, a także platformy, które nie są już powszechnie używane. Chociaż istnieje wartość w tym, że Twoja biblioteka działa jak największej liczbie obiektów docelowych, bez obejścia interfejsów API, można zwiększyć znaczący koszt. Uważamy, że pewne struktury nie są już ukierunkowane na to, biorąc pod uwagę ich zasięg i ograniczenia.

❌ nie obejmują obiektu docelowego biblioteki klas przenośnych (PCL). Na przykład `portable-net45+win8+wpa81+wp8`.

> .NET Standard to nowoczesny sposób obsługi bibliotek platformy .NET dla wielu platform i zastępuje PCLs.

❌ nie zawierają obiektów docelowych dla platform .NET, które nie są już obsługiwane. Na przykład `SL4`, `WP`.

>[!div class="step-by-step"]
>[Poprzednie](get-started.md)
>[dalej](strong-naming.md)
