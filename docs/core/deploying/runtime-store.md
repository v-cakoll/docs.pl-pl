---
title: Magazyn pakietu środowiska uruchomieniowego
description: Dowiedz się, jak używać magazynu pakietów czasu wykonywania do kierowania manifestów używanych przez .NET Core.
ms.date: 08/12/2017
ms.openlocfilehash: 7a833ed95147608c6fb403f8f0dec179d2a73833
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77448961"
---
# <a name="runtime-package-store"></a>Magazyn pakietu środowiska uruchomieniowego

Począwszy od .NET Core 2.0, można spakować i wdrożyć aplikacje przeciwko znanemu zestawowi pakietów, które istnieją w środowisku docelowym. Korzyści są szybsze wdrożenia, mniejsze zużycie miejsca na dysku i zwiększona wydajność uruchamiania w niektórych przypadkach.

Ta funkcja jest implementowana jako *magazyn pakietów środowiska uruchomieniowego,* który jest katalogiem na dysku, na którym przechowywane są pakiety (zazwyczaj w */usr/local/share/dotnet/store* w systemie macOS/Linux i *C:/Program Files/dotnet/store* w systemie Windows). W tym katalogu istnieją podkatalogi dla architektur i [platform docelowych](../../standard/frameworks.md). Układ pliku jest podobny do sposobu, w jaki [zasoby NuGet są rozmieszczone na dysku:](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure)

```
\dotnet
    \store
        \x64
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
        \x86
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
```

Plik *manifestu docelowego* wyświetla listę pakietów w magazynie pakietów w czasie wykonywania. Deweloperzy mogą kierować ten manifest podczas publikowania aplikacji. Manifest docelowy jest zazwyczaj dostarczany przez właściciela docelowego środowiska produkcyjnego.

## <a name="preparing-a-runtime-environment"></a>Przygotowywanie środowiska środowiska uruchomieniowego

Administrator środowiska uruchomieniowego można zoptymalizować aplikacje dla szybszych wdrożeń i mniejsze wykorzystanie miejsca na dysku, tworząc magazyn pakietów środowiska uruchomieniowego i odpowiedniego manifestu docelowego.

Pierwszym krokiem jest utworzenie *manifestu magazynu pakietów,* który zawiera listę pakietów, które tworzą magazyn pakietów w czasie wykonywania. Ten format pliku jest zgodny z formatem pliku projektu *(csproj).*

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Przykład**

Poniższy przykładowy manifest magazynu pakietów (*packages.csproj*) służy do dodawania [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) i [`Moq`](https://www.nuget.org/packages/moq/) do magazynu pakietów w czasie wykonywania:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Aprowizuj magazyn pakietów `dotnet store` w czasie wykonywania, wykonując za pomocą manifestu magazynu pakietów, czasu wykonawczego i struktury:

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Przykład**

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Można przekazać wiele ścieżek manifestu [`dotnet store`](../tools/dotnet-store.md) magazynu pakietów docelowych do jednego polecenia, powtarzając opcję i ścieżkę w poleceniu.

Domyślnie dane wyjściowe polecenia to magazyn pakietów w podkatalogu *.dotnet/store* profilu użytkownika. Można określić inną lokalizację `--output <OUTPUT_DIRECTORY>` za pomocą tej opcji. Katalog główny magazynu zawiera plik artefaktu manifestu *docelowego.xml.* Ten plik może być dostępny do pobrania i być używany przez autorów aplikacji, którzy chcą kierować ten sklep podczas publikowania.

**Przykład**

Następujący plik *artifact.xml* jest tworzony po uruchomieniu poprzedniego przykładu. Należy [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) zauważyć, że `Moq`jest zależność , więc jest ona dołączona automatycznie i pojawia się w pliku manifestu *artifacts.xml.*

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Publikowanie aplikacji względem manifestu docelowego

Jeśli na dysku znajduje się docelowy plik manifestu, należy określić ścieżkę do pliku podczas publikowania aplikacji [`dotnet publish`](../tools/dotnet-publish.md) za pomocą polecenia:

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Przykład**

```dotnetcli
dotnet publish --manifest manifest.xml
```

Wdrożenie wynikowej opublikowanej aplikacji do środowiska, które ma pakiety opisane w manifeście docelowym. Nie wykonanie tego nie powoduje niepowodzenia aplikacji w przypadku nieuruchomienia.

Określ wiele manifestów docelowych podczas publikowania aplikacji, powtarzając `--manifest manifest1.xml --manifest manifest2.xml`opcję i ścieżkę (na przykład). Po złożeniu tej pracy aplikacja jest przycięta dla unii pakietów określonych w docelowych plików manifestu dostarczonych do polecenia.

## <a name="specifying-target-manifests-in-the-project-file"></a>Określanie manifestów docelowych w pliku projektu

Alternatywą dla określania manifestów [`dotnet publish`](../tools/dotnet-publish.md) docelowych za pomocą polecenia jest określenie ich w pliku projektu jako listy ścieżek oddzielonych średnikami pod tagiem ** \<>TargetManifestFiles.**

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Określ manifesty docelowe w pliku projektu tylko wtedy, gdy środowisko docelowe dla aplikacji jest dobrze znane, na przykład dla projektów .NET Core. Nie dotyczy to projektów typu open source. Użytkownicy projektu typu open source zazwyczaj wdrażają go w różnych środowiskach produkcyjnych. Te środowiska produkcyjne mają zazwyczaj różne zestawy pakietów wstępnie zainstalowanych. Nie można zakładać manifestu docelowego w takich środowiskach, więc `--manifest` należy [`dotnet publish`](../tools/dotnet-publish.md)użyć opcji .

## <a name="aspnet-core-implicit-store"></a>ASP.NET Magazyn niejawny core

Magazyn niejawny ASP.NET Core ma zastosowanie tylko do ASP.NET Core 2.0. Zdecydowanie zaleca się aplikacje używać ASP.NET Core 2.1 i nowsze, który **nie** używa magazynu niejawnego. ASP.NET Core 2.1 i później użyć wspólnej struktury.

Funkcja magazynu pakietów w czasie wykonywania jest używana niejawnie przez aplikację ASP.NET Core, gdy aplikacja jest wdrażana jako aplikacja [wdrażania zależnego od struktury (FDD).](index.md#publish-runtime-dependent) Obiekty docelowe [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) w include manifesty odwołujące się do magazynu pakietów niejawnych w systemie docelowym. Ponadto każda aplikacja FDD, która `Microsoft.AspNetCore.All` zależy od wyników pakietu w opublikowanej aplikacji, która zawiera tylko `Microsoft.AspNetCore.All` aplikację i jej zasoby, a nie pakiety wymienione w metapakiecie. Zakłada się, że te pakiety są obecne w systemie docelowym.

Magazyn pakietów w czasie wykonywania jest instalowany na hoście po zainstalowaniu zestawu SDK .NET Core. Inni instalatorzy mogą udostępniać magazyn pakietów środowiska uruchomieniowego, w tym instalacje `apt-get`Zip/tarball zestawu .NET Core SDK, Red Hat Yum, pakietu hostingowego .NET Core Windows Server hosting umiejętnie oraz ręczne instalacje magazynu pakietów środowiska uruchomieniowego.

Podczas wdrażania aplikacji [wdrażania zależnej od struktury (FDD)](index.md#publish-runtime-dependent) upewnij się, że w środowisku docelowym jest zainstalowany zestaw SDK .NET Core. Jeśli aplikacja jest wdrażana w środowisku, które nie zawiera ASP.NET Core, można zrezygnować z magazynu niejawnego, `false` określając ** \<PublishWithAspNetCoreTargetManifest>** ustawiony w pliku projektu, jak w poniższym przykładzie:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> W przypadku aplikacji [do samodzielnego wdrażania (SCD)](index.md#publish-self-contained) zakłada się, że system docelowy niemusi zawierać wymaganych pakietów manifestu. W związku z tym ** \<PublishWithAspNetCoreTargetManifest>** nie można ustawić `true` dla aplikacji SCD.

Jeśli wdrożysz aplikację z zależnościmanifestu, który jest obecny we wdrożeniu (zestaw jest obecny w folderze *pakietu,* magazyn pakietów czasu *wykonywania nie jest używany* na hoście dla tego zestawu. Zestaw folderu *pojemnika* jest używany niezależnie od jego obecności w magazynie pakietów w czasie wykonywania na hoście.

Wersja zależności wskazanew manifeście musi odpowiadać wersji zależności w magazynie pakietów czasu wykonywania. Jeśli masz niezgodność wersji między zależności w manifeście docelowym i wersji, która istnieje w magazynie pakietów w czasie wykonywania i aplikacja nie zawiera wymaganą wersję pakietu w jego wdrożeniu, aplikacja nie może zostać uruchomiony. Wyjątek zawiera nazwę manifestu docelowego, który wezwał do zestawu magazynu pakietów czasu wykonywania, który pomaga rozwiązać problem niezgodności.

Gdy wdrożenie jest *przycięte* na publikacji, tylko określone wersje pakietów manifestu, które wskazują są wstrzymane z opublikowanych danych wyjściowych. Pakiety w wskazanych wersjach muszą być obecne na hoście, aby aplikacja została uniejszona.

## <a name="see-also"></a>Zobacz też

- [dotnet-publikowanie](../tools/dotnet-publish.md)
- [dotnet-sklep](../tools/dotnet-store.md)
