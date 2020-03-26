---
title: Magazyn pakietu środowiska uruchomieniowego
description: Dowiedz się, jak używać magazynu pakietów środowiska wykonawczego do określania manifestów używanych przez program .NET Core.
ms.date: 08/12/2017
ms.openlocfilehash: ba3182b682e8a47397ac09ed46afe25190d34e5f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134272"
---
# <a name="runtime-package-store"></a>Magazyn pakietu środowiska uruchomieniowego

Począwszy od platformy .NET Core 2.0, można spakować i wdrożyć aplikacje względem znanego zestawu pakietów, które istnieją w środowisku docelowym. Korzyści to szybsze wdrożenia, mniejsze użycie miejsca na dysku i zwiększona wydajność uruchamiania w niektórych przypadkach.

Ta funkcja jest implementowana jako *magazyn pakietów środowiska wykonawczego,* który jest katalogiem na dysku, na którym przechowywane są pakiety (zazwyczaj w */usr/local/share/dotnet/store* w systemie macOS/Linux i *C:/Program Files/dotnet/store* w systemie Windows). W tym katalogu istnieją podkatalogi dla architektur i [struktur docelowych](../../standard/frameworks.md). Układ pliku jest podobny do sposobu, w jaki [zasoby NuGet są rozmieszczone na dysku:](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure)

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

Docelowy plik *manifestu* zawiera listę pakietów w magazynie pakietów środowiska wykonawczego. Deweloperzy mogą kierować ten manifest podczas publikowania aplikacji. Manifest docelowy jest zazwyczaj dostarczany przez właściciela docelowego środowiska produkcyjnego.

## <a name="preparing-a-runtime-environment"></a>Przygotowywanie środowiska wykonawczego

Administrator środowiska wykonawczego może zoptymalizować aplikacje pod kątem szybszych wdrożeń i mniejszego wykorzystania miejsca na dysku, tworząc magazyn pakietów środowiska wykonawczego i odpowiedni manifest docelowy.

Pierwszym krokiem jest utworzenie *manifestu magazynu pakietów,* który zawiera listę pakietów, które tworzą magazyn pakietów środowiska wykonawczego. Ten format pliku jest zgodny z formatem pliku projektu (*csproj*).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Przykład**

Następujące przykładowe manifest magazynu pakietu (*packages.csproj*) służy do dodawania [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) i [`Moq`](https://www.nuget.org/packages/moq/) do magazynu pakietów środowiska wykonawczego:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Aprowizuj magazyn pakietów środowiska wykonawczego, wykonując `dotnet store` z manifestem magazynu pakietów, środowiska wykonawczego i struktury:

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Przykład**

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Można przekazać wiele ścieżek manifestu magazynu [`dotnet store`](../tools/dotnet-store.md) pakietów docelowych do pojedynczego polecenia, powtarzając opcję i ścieżkę w poleceniu.

Domyślnie dane wyjściowe polecenia jest magazyn pakietów w podkatalogu *.dotnet/store* profilu użytkownika. Za pomocą `--output <OUTPUT_DIRECTORY>` tej opcji można określić inną lokalizację. Katalog główny magazynu zawiera docelowy plik *artifact.xml* manifestu. Ten plik może być dostępny do pobrania i być używany przez autorów aplikacji, którzy chcą kierować ten magazyn podczas publikowania.

**Przykład**

Następujący plik *artifact.xml* jest produkowany po uruchomieniu poprzedniego przykładu. Należy [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) zauważyć, że `Moq`jest zależność , więc jest automatycznie uwzględniane i pojawia się w pliku manifestu *artifacts.xml.*

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Publikowanie aplikacji względem manifestu docelowego

Jeśli masz docelowy plik manifestu na dysku, należy określić ścieżkę do pliku podczas publikowania aplikacji za pomocą [`dotnet publish`](../tools/dotnet-publish.md) polecenia:

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Przykład**

```dotnetcli
dotnet publish --manifest manifest.xml
```

Można wdrożyć wynikową opublikowaną aplikację do środowiska, które ma pakiety opisane w manifeście docelowym. W przeciwnym razie powoduje, że aplikacja nie może się uruchomić.

Określ wiele manifestów docelowych podczas publikowania aplikacji, powtarzając `--manifest manifest1.xml --manifest manifest2.xml`opcję i ścieżkę (na przykład ). Po wykonaniu tej sprawy aplikacja jest przycinana dla unii pakietów określonych w plikach manifestu docelowego dostarczonych do polecenia.

## <a name="specifying-target-manifests-in-the-project-file"></a>Określanie manifestów docelowych w pliku projektu

Alternatywą dla określania manifestów [`dotnet publish`](../tools/dotnet-publish.md) docelowych za pomocą polecenia jest określenie ich w pliku projektu jako listy ścieżek oddzielonych średnikami pod tagiem ** \<targetmanifestfiles>.**

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Określ manifesty docelowe w pliku projektu tylko wtedy, gdy środowisko docelowe dla aplikacji jest dobrze znane, na przykład dla projektów .NET Core. Nie dotyczy to projektów typu open source. Użytkownicy projektu typu open source zazwyczaj wdrażają go w różnych środowiskach produkcyjnych. Te środowiska produkcyjne zazwyczaj mają różne zestawy pakietów wstępnie zainstalowanych. Nie można zakładać manifestu docelowego w takich środowiskach, `--manifest` więc [`dotnet publish`](../tools/dotnet-publish.md)należy użyć opcji .

## <a name="aspnet-core-implicit-store"></a>ASP.NET Magazyn niejawny Core

Magazyn niejawny ASP.NET Core ma zastosowanie tylko do ASP.NET Core 2.0. Zdecydowanie zaleca się aplikacje używać ASP.NET Core 2.1 i nowsze, który **nie** używa magazynu niejawne. ASP.NET Core 2.1 i nowszych korzystać z udostępnionej struktury.

Funkcja magazynu pakietów środowiska uruchomieniowego jest używana niejawnie przez aplikację ASP.NET Core, gdy aplikacja jest wdrażana jako aplikacja [wdrożenia zależnego od struktury (FDD).](index.md#publish-runtime-dependent) Obiekty docelowe obejmują [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) manifesty odwołujące się do magazynu pakietów niejawnych w systemie docelowym. Ponadto każda aplikacja FDD, która `Microsoft.AspNetCore.All` zależy od pakietu powoduje, że opublikowana aplikacja, która zawiera tylko `Microsoft.AspNetCore.All` aplikację i jej zasoby, a nie pakiety wymienione w metapakiet. Zakłada się, że te pakiety są obecne w systemie docelowym.

Magazyn pakietów środowiska wykonawczego jest instalowany na hoście po zainstalowaniu zestawu .NET Core SDK. Inni instalatorzy mogą udostępniać magazyn pakietów środowiska wykonawczego, w tym instalacje `apt-get`zip/tarball zestawu .NET Core SDK, Red Hat Yum, pakiet hostingu systemu .NET Core Windows Server i ręczne instalacje magazynu pakietów środowiska wykonawczego.

Podczas wdrażania aplikacji [wdrożenia zależnego od struktury (FDD)](index.md#publish-runtime-dependent) upewnij się, że środowisko docelowe ma zainstalowany pakiet .NET Core SDK. Jeśli aplikacja jest wdrażana w środowisku, które nie zawiera ASP.NET Core, można zrezygnować z magazynu niejawnego, określając ** \<PublishWithAspNetCoreTargetManifest>** ustawiona `false` w pliku projektu, jak w poniższym przykładzie:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> W przypadku aplikacji [niezależnego wdrażania (SCD)](index.md#publish-self-contained) zakłada się, że system docelowy nie musi zawierać wymaganych pakietów manifestu. W związku z tym ** \<PublishWithAspNetCoreTargetManifest**>`true` nie można ustawić dla aplikacji SCD.

Jeśli wdrożysz aplikację z zależnością manifestu, która jest obecna we wdrożeniu (zestaw jest obecny w folderze *bin),* magazyn pakietów środowiska wykonawczego *nie jest używany* na hoście dla tego zestawu. Zestaw folderów *pojemnika* jest używany niezależnie od jego obecności w magazynie pakietów środowiska wykonawczego na hoście.

Wersja zależności wskazana w manifeście musi być zgodna z wersją zależności w magazynie pakietów środowiska wykonawczego. Jeśli masz niezgodność wersji między zależności w manifeście docelowym i wersji, która istnieje w magazynie pakietów środowiska wykonawczego i aplikacja nie zawiera wymaganej wersji pakietu w jego wdrożeniu, aplikacja nie można uruchomić. Wyjątek zawiera nazwę manifestu docelowego, który jest wywoływany dla zestawu magazynu pakietów środowiska wykonawczego, co ułatwia rozwiązywanie problemów z niezgodnością.

Gdy wdrożenie jest *przycinane* na publikowanie, tylko określone wersje pakietów manifestu, które wskazujesz, są wstrzymane z opublikowanych danych wyjściowych. Pakiety w wskazanych wersjach muszą być obecne na hoście, aby aplikacja została uruchomiony.

## <a name="see-also"></a>Zobacz też

- [dotnet-publikować](../tools/dotnet-publish.md)
- [sklep dotnet](../tools/dotnet-store.md)
