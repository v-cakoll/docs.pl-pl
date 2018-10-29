---
title: Przeznaczone dla wielu platform
description: Zalecenia dotyczące najlepszych rozwiązań do tworzenia bibliotek .NET między platformami.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 72fa891d5b1054af485a98d89b4efb11d6b0018b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202819"
---
# <a name="cross-platform-targeting"></a>Przeznaczone dla wielu platform

Nowoczesne .NET obsługuje wiele systemów operacyjnych i urządzeń. Ważne jest dla platformy .NET bibliotek typu open source do obsługi tak wielu programistów, jak to możliwe, czy jest tworzone w witrynie sieci Web platformy ASP.NET hostowanej na platformie Azure lub gra .NET na platformie Unity.

## <a name="net-standard"></a>.NET Standard

.NET standard jest najlepszym sposobem dodania obsługi wielu platform w bibliotece platformy .NET. [.NET standard](../net-standard.md) to specyfikacja interfejsów API platformy .NET, które są dostępne na wszystkich implementacji .NET. Przeznaczonych dla platformy .NET Standard umożliwia tworzenie godnych bibliotek, które są ograniczone do użycia interfejsów API, które znajdują się w danej wersji programu .NET Standard, co oznacza, że jest użyteczne przez wszystkie platformy, które implementują tę wersję .NET Standard.

![.NET standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

Przeznaczonych dla platformy .NET Standard i pomyślnie Kompilowanie projektu, nie gwarantuje, że biblioteka zostanie pomyślnie uruchomiona na wszystkich platformach:

1. Interfejsy API specyficzne dla platformy zakończy się niepowodzeniem na innych platformach. Na przykład <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> będą się powieść po Windows i generują <xref:System.PlatformNotSupportedException> stosowania w dowolnym systemie operacyjnym.
2. Interfejsy API mogą zachowywać się inaczej. Na przykład za odbicia interfejsów API jest mają różną charakterystykę wydajności w aplikacji używane kompilację ahead of time w systemie iOS lub platformy uniwersalnej systemu Windows.

> [!TIP]
> Zespół .NET [oferuje analizatora Roslyn](../analyzers/api-analyzer.md) Państwu pomóc odkryć potencjalne problemy.

**CZY ✔️** rozpoczynać się tym `netstandard2.0` docelowej.

> Najbardziej ogólnego przeznaczenia biblioteki nie powinni interfejsów API poza .NET Standard 2.0. .NET standard 2.0 jest obsługiwane przez wszystkie nowoczesne platformy i jest to zalecany sposób obsługi wielu platform w jeden element docelowy.

**Należy UNIKAĆ ❌** tym `netstandard1.x` docelowej.

> .NET standard 1.x jest rozpowszechniany jako szczegółowego zestawu pakietów NuGet, tworzy wykres zależności duży pakiet, co skutkuje deweloperów pobierania partii pakietów podczas kompilacji. Nowoczesnych platform .NET, w tym .NET Framework 4.6.1, platformy uniwersalnej systemu Windows i Xamarin, wszystkie obsługują .NET Standard 2.0. Powinien dotyczyć tylko .NET Standard 1.x, jeśli jest wymagana do starszych platformą docelową.

**CZY ✔️** obejmują `netstandard2.0` docelowe w razie potrzeby `netstandard1.x` docelowej.

> Wszystkie platformy .NET Standard 2.0 obsługi użyje `netstandard2.0` docelową i korzyści z posiadania wykres mniejszych pakietów, gdy starszych platformach będą nadal działać i wrócić korzystania z `netstandard1.x` docelowej.

**❌ NIE** obejmują .NET Standard docelowy, jeśli biblioteka opiera się na modelu specyficznego dla platformy aplikacji.

> Na przykład biblioteki zestawu narzędzi kontrolek platformy uniwersalnej systemu Windows jest zależny od modelu aplikacji, która jest dostępna tylko na platformy uniwersalnej systemu Windows. Specyficzne dla modelu aplikacji interfejsów API nie będą dostępne w programie .NET Standard.

## <a name="multi-targeting"></a>Wielowersyjność kodu

Czasami zachodzi potrzeba dostęp do interfejsów API specyficznych dla framework z bibliotek. Najlepszym sposobem wywoływania interfejsów API specyficznych dla framework używa wielowersyjność kodu, który kompiluje projekt dla wielu [platform docelowych .NET](../frameworks.md) , a nie tylko jednego.

Można włączyć osłony dla klientów z konieczności tworzenia dla poszczególnych platform, należy dążyć mieć .NET Standard danych wyjściowych, a także co najmniej jeden właściwa dla struktury danych wyjściowych. Przy użyciu wielowersyjności kodu wszystkie zestawy są spakowane w jednym pakiecie NuGet. Konsumenci następnie tworzyć odwołania do tego samego pakietu i NuGet wybierze odpowiednią implementacji. Biblioteki .NET Standard służy jako rezerwowej biblioteki, który jest używany wszędzie, z wyjątkiem przypadków, gdy pakiet NuGet oferuje wykonania określonej platformy. Wielowersyjność kodu pozwala użyć kompilacji warunkowej w kodzie i wywoływać interfejsy API specyficzne dla framework.

![Pakiet NuGet za pomocą wielu zestawów](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "pakietu NuGet wraz z wielu zestawów")

**ROZWAŻ ✔️** obsługiwane implementacje platformy .NET, oprócz .NET Standard.

> Obsługiwane implementacje platformy .NET umożliwia wywoływanie interfejsów API specyficznych dla platformy, które znajdują się poza .NET Standard.
>
> Gdy to zrobisz, nie porzucić pomocy technicznej dla platformy .NET Standard. Zamiast tego należy zgłaszać z wdrożenia i oferuje możliwości interfejsów API. W ten sposób biblioteki mogą być używane w dowolnym miejscu i obsługuje środowisko uruchomieniowe światła w górę funkcji.

**Należy UNIKAĆ ❌** przy użyciu wielowersyjności kodu za pomocą platformy .NET Standard, jeśli kod źródłowy jest taka sama dla wszystkich obiektów docelowych.

> Zestaw .NET Standard automatycznie będą używane przez NuGet. Przeznaczone dla poszczególnych implementacji .NET zwiększa `*.nupkg` rozmiar bez żadnych korzyści.

**✔️ ROZWAŻ** Dodawanie elementu docelowego dla `net461` po użytkownik oferowane `netstandard2.0` docelowej. 

> Przy użyciu platformy .NET Standard 2.0 z .NET Framework ma kilka problemów, które zostały rozwiązane w programie .NET Framework 4.7.2. Możesz poprawić środowisko dla deweloperów, którzy nadal korzystają z platformy .NET Framework 4.6.1 — 4.7.1, oferując im plik binarny, który jest przeznaczony dla platformy .NET Framework 4.6.1.

**CZY ✔️** dystrybucji przy użyciu pakietu NuGet biblioteki.

> NuGet zaznaczy najlepsze docelowego dla deweloperów i zabezpieczyć je konieczności wyboru odpowiedniej implementacji.

**CZY ✔️** przy użyciu pliku projektu `TargetFrameworks` właściwość równoczesną wielowersyjnością kodu.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

**ROZWAŻ ✔️** przy użyciu [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) równoczesną wielowersyjnością kodu platformy uniwersalnej systemu Windows i Xamarin jak znacząco upraszcza pliku projektu.

## <a name="older-targets"></a>Starsze elementów docelowych

.NET wspomaga określania wartości docelowej wersji systemu .NET Framework, które są długie poza pomocy technicznej, a także platformy, które są już powszechnie używane. Brak wartości w trakcie wprowadzania pracy biblioteki na jak wiele elementów docelowych jak to możliwe, konieczności obejść Brak interfejsów API można dodać znaczne obciążenie. My uważamy pewność, że platform nie są już warte docelowych, biorąc pod uwagę ich zasięgu i ograniczenia.

**❌ NIE** obejmują docelowej biblioteki klas przenośnych (PCL). Na przykład `portable-net45+win8+wpa81+wp8`.

> .NET standard jest nowoczesny sposób obsługi bibliotek programu .NET dla wielu platform i zastępuje PCLs.

**❌ NIE** obejmują elementy docelowe dla platform .NET, które nie są już obsługiwane. Na przykład `SL4`, `WP`.

>[!div class="step-by-step"]
[Poprzednie](./get-started.md)
[dalej](./strong-naming.md)
