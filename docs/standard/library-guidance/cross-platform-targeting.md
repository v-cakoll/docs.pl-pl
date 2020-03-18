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
# <a name="cross-platform-targeting"></a>Obsługiwane rozwiązania międzyplatformowe

Nowoczesny program .NET obsługuje wiele systemów operacyjnych i urządzeń. Ważne jest, aby biblioteki typu open source platformy .NET obsługiwały jak najwięcej deweloperów, niezależnie od tego, czy tworzą witrynę sieci Web ASP.NET hostowane na platformie Azure, czy grę .NET w unity.

## <a name="net-standard"></a>.NET Standard

.NET Standard to najlepszy sposób dodawania obsługi między platformami do biblioteki .NET. [.NET Standard](../net-standard.md) to specyfikacja interfejsów API .NET, które są dostępne we wszystkich implementacjach .NET. Kierowanie .NET Standard umożliwia tworzenie bibliotek, które są ograniczone do używania interfejsów API, które znajdują się w danej wersji .NET Standard, co oznacza, że jest używany przez wszystkie platformy, które implementują tę wersję standardu .NET.

![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

Kierowanie na .NET Standard i pomyślne kompilowanie projektu nie gwarantuje, że biblioteka zostanie pomyślnie uruchomiony na wszystkich platformach:

1. Interfejsy API specyficzne dla platformy nie powiedzie się na innych platformach. Na przykład <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> zakończy się powodzeniem <xref:System.PlatformNotSupportedException> w systemie Windows i wyrzuci, gdy jest używany w innych systemach operacyjnych.
2. Interfejsy API mogą zachowywać się inaczej. Na przykład interfejsy API odbicia mają różne właściwości wydajności, gdy aplikacja używa kompilacji z wyprzedzeniem w iOS lub UWP.

> [!TIP]
> Zespół .NET [oferuje analizator Roslyn,](../analyzers/api-analyzer.md) który pomoże Ci wykryć możliwe problemy.

✔️ zacząć od `netstandard2.0` włączenia celu.

> Większość bibliotek ogólnego przeznaczenia nie powinna potrzebować interfejsów API poza standardem .NET Standard 2.0. .NET Standard 2.0 jest obsługiwany przez wszystkie nowoczesne platformy i jest zalecanym sposobem obsługi wielu platform z jednym celem.

❌UNIKAJ w `netstandard1.x` tym cel.

> .NET Standard 1.x jest rozprowadzany jako szczegółowy zestaw pakietów NuGet, który tworzy wykres zależności dużego pakietu i powoduje, że deweloperzy pobierają wiele pakietów podczas tworzenia. Nowoczesne platformy .NET, w tym .NET Framework 4.6.1, UWP i Xamarin, obsługują wszystko .NET Standard 2.0. Należy kierować tylko .NET Standard 1.x, jeśli w szczególności trzeba kierować starszej platformy.

✔️ do `netstandard2.0` zawierać cel, `netstandard1.x` jeśli potrzebujesz celu.

> Wszystkie platformy obsługujące .NET Standard `netstandard2.0` 2.0 użyje docelowego i korzyści z posiadania mniejszego wykresu pakietu, podczas gdy starsze platformy będą nadal działać i wrócić do korzystania z `netstandard1.x` obiektu docelowego.

❌NIE należy dołączać do standardu .NET, jeśli biblioteka opiera się na modelu aplikacji specyficznedla platformy.

> Na przykład biblioteka zestawu narzędzi kontroli platformy uwp zależy od modelu aplikacji, który jest dostępny tylko na platformie UWP. Interfejsy API specyficzne dla modelu aplikacji nie będą dostępne w standardzie .NET.

## <a name="multi-targeting"></a>Kierowanie na wiele

Czasami trzeba uzyskać dostęp do interfejsów API specyficznych dla struktury z bibliotek. Najlepszym sposobem wywoływania interfejsów API specyficzne dla struktury jest przy użyciu wielu miejsc docelowych, który tworzy projekt dla wielu [platform docelowych .NET,](../frameworks.md) a nie tylko dla jednego.

Aby chronić konsumentów przed konieczności tworzenia dla poszczególnych struktur, należy dążyć do .NET standard danych wyjściowych oraz jeden lub więcej danych wyjściowych specyficznych dla struktury. Z wielu określania wartości, wszystkie zestawy są pakowane wewnątrz jednego pakietu NuGet. Konsumenci mogą następnie odwoływać się do tego samego pakietu i NuGet wybierze odpowiednią implementację. Biblioteka .NET Standard służy jako rezerwowej biblioteki, która jest używana wszędzie, z wyjątkiem przypadków, w których pakiet NuGet oferuje implementacji specyficzne dla struktury. Multi-targetowanie umożliwia użycie kompilacji warunkowej w kodzie i wywołać interfejsy API specyficzne dla struktury.

![Pakiet NuGet z wieloma zestawami](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Pakiet NuGet z wieloma zestawami")

✔️ ROZWAŻ kierowanie implementacji .NET oprócz .NET Standard.

> Kierowanie na implementacje .NET umożliwia wywołanie interfejsów API specyficznych dla platformy, które znajdują się poza standardem .NET.
>
> Nie należy upuszczać obsługi .NET Standard, gdy to zrobisz. Zamiast tego należy wyrzucić z implementacji i oferują możliwości interfejsów API. W ten sposób biblioteki można używać w dowolnym miejscu i obsługuje uruchamianie funkcji.

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

❌Unikaj wielu celów, a także kierowania .NET Standard, jeśli kod źródłowy jest taki sam dla wszystkich obiektów docelowych.

> Zestaw .NET Standard będzie automatycznie używany przez NuGet. Kierowanie na poszczególne implementacje .NET zwiększa rozmiar bez `*.nupkg` korzyści.

✔️ ROZWAŻ dodanie `net461` celu, gdy oferujesz `netstandard2.0` cel.

> Przy użyciu .NET Standard 2.0 z .NET Framework ma pewne problemy, które zostały rozwiązane w .NET Framework 4.7.2. Można poprawić środowisko dla deweloperów, które są nadal na .NET Framework 4.6.1 - 4.7.1, oferując im plik binarny, który jest zbudowany dla .NET Framework 4.6.1.

✔️ dystrybuują biblioteki przy użyciu pakietu NuGet.

> NuGet wybierze najlepszy cel dla dewelopera i osłonić je konieczności wybrania odpowiedniej implementacji.

✔️ DO używać `TargetFrameworks` właściwości pliku projektu podczas wielu kierowania.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

✔️ ZAStanów się przy użyciu [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) podczas wielu kierowania na platformę Uniwersalną systemu UWP i xamarin, ponieważ znacznie upraszcza plik projektu.

## <a name="older-targets"></a>Starsze cele

.NET obsługuje wersje docelowe platformy .NET Framework, które są długo poza obsługą, a także platform, które nie są już powszechnie używane. Chociaż istnieje wartość w tworzeniu pracy biblioteki na jak najwięcej obiektów docelowych, jak to możliwe, konieczności obejścia brakujących interfejsów API można dodać znaczne obciążenie. Uważamy, że niektóre ramy nie są już warte ukierunkowania, biorąc pod uwagę ich zasięg i ograniczenia.

❌NIE należy dołączać obiektu docelowego przenośnej biblioteki klas (PCL). Na przykład `portable-net45+win8+wpa81+wp8`.

> .NET Standard to nowoczesny sposób obsługi wieloplatformowych bibliotek .NET i zastępowania list PCL.

❌NIE należy uwzględniać obiektów docelowych dla platform .NET, które nie są już obsługiwane. Na przykład `SL4` `WP`, .

>[!div class="step-by-step"]
>[Poprzedni](get-started.md)
>[następny](strong-naming.md)
