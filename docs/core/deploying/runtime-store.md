---
title: Magazyn pakietu środowiska uruchomieniowego
description: Dowiedz się, jak używać Magazyn pakietu środowiska uruchomieniowego do manifesty docelowy używany przez platformy .NET Core.
author: bleroy
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: a190e148715547fde29d3a852183ea4d75065e79
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170356"
---
# <a name="runtime-package-store"></a>Magazyn pakietu środowiska uruchomieniowego

Począwszy od programu .NET Core 2.0, istnieje możliwość pakować i wdrażać aplikacje przed znanych zestaw pakietów, które istnieją w środowisku docelowym. Korzyści są szybsze wdrożenia, niższe użycie miejsca na dysku i wydajności uruchamiania ulepszone w niektórych przypadkach.

Ta funkcja jest implementowany jako *Magazyn pakietu środowiska uruchomieniowego*, który jest katalogiem na dysku, na którym przechowywane są pakiety (zwykle znajduje się w */usr/local/share/dotnet/store* w systemie macOS/Linux i *C: / Program plików/dotnet/store* na Windows). W tym katalogu istnieją podkatalogów dla architektury i [ustalać platformy docelowe](../../standard/frameworks.md). Układ pliku jest podobny sposób, który [NuGet zasoby są ułożone w na dysku](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):

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

A *target manifestem* plik listy pakietów w Magazyn pakietu środowiska uruchomieniowego. Deweloperzy mogą kierować tego manifestu, podczas publikowania aplikacji. Manifest docelowy jest zwykle zapewniany przez właściciela w środowisku produkcyjnym docelowych.

## <a name="preparing-a-runtime-environment"></a>Przygotowywanie środowiska uruchomieniowego

Administrator środowiska uruchomieniowego, można zoptymalizować aplikacje dla wdrożeń szybciej i niższym użycie miejsca na dysku, tworząc Magazyn pakietu środowiska uruchomieniowego i odpowiedniego manifestu docelowego.

Pierwszym krokiem jest utworzenie *manifestu sklepu pakietu* , zawiera listę pakietów, które tworzą magazyn pakietu środowiska uruchomieniowego. Ten format jest zgodny z formatem pliku projektu (*csproj*).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Przykład**

Poniższy przykład pakietów manifestu Sklepu (*packages.csproj*) służy do dodawania [ `Newtonsoft.Json` ](https://www.nuget.org/packages/Newtonsoft.Json/) i [ `Moq` ](https://www.nuget.org/packages/moq/) do Magazyn pakietu środowiska uruchomieniowego:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Aprowizuj Magazyn pakietu środowiska uruchomieniowego, wykonując `dotnet store` z manifestu Magazyn pakietu środowiska uruchomieniowego i framework:

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Przykład**

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Wiele ścieżek manifestu pakietu magazynu docelowego można przekazać do pojedynczego [ `dotnet store` ](../tools/dotnet-store.md) polecenia, powtarzając opcja i ścieżki w poleceniu.

Domyślnie dane wyjściowe polecenia jest Magazyn pakietu, w obszarze *.dotnet/store* podkatalogu profilu użytkownika. Możesz określić inną lokalizację, w którym używana jest `--output <OUTPUT_DIRECTORY>` opcji. Katalog główny magazyn zawiera manifest docelowej *artifact.xml* pliku. Ten plik może być udostępniane do pobrania i używane przez autorów aplikacji, którzy ma pod kątem tego magazynu podczas publikowania.

**Przykład**

Następujące *artifact.xml* po uruchomieniu w poprzednim przykładzie jest tworzony plik. Należy pamiętać, że [ `Castle.Core` ](https://www.nuget.org/packages/Castle.Core/) zależą od elementu `Moq`, więc jest automatycznie włączone i pojawia się w *artifacts.xml* pliku manifestu.

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Publikowanie aplikacji względem manifest docelowej

Jeśli masz plik manifestu docelowego na dysku, określ ścieżkę do pliku podczas publikowania aplikacji za pomocą [ `dotnet publish` ](../tools/dotnet-publish.md) polecenia:

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Przykład**

```console
dotnet publish --manifest manifest.xml
```

Możesz wdrożyć wynikowy opublikowanej aplikacji w środowisku, który zawiera pakiety, opisane w manifeście docelowego. Powoduje niepowodzenie w tym aplikacji, nie można uruchomić.

Określ wiele manifesty docelowego podczas publikowania aplikacji, powtarzając opcji i ścieżki (na przykład `--manifest manifest1.xml --manifest manifest2.xml`). Jeśli tak zrobisz, aplikacja są spacje dla Unii pakiety określone w plikach manifestu docelowej dostarczane do polecenia.

## <a name="specifying-target-manifests-in-the-project-file"></a>Określanie manifesty docelowy w pliku projektu

Zamiast określania docelowej manifesty za pomocą [ `dotnet publish` ](../tools/dotnet-publish.md) ma je określić w pliku projektu jako Rozdzielana średnikami lista ścieżek w obszarze polecenie  **\<TargetManifestFiles >** tagu.

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Manifesty docelowego należy określić w pliku projektu tylko wtedy, gdy środowisko docelowe dla aplikacji jest dobrze znanych, takich jak dla projektów .NET Core. Nie jest to w przypadku projektów typu open source. Użytkownicy projektu open-source zazwyczaj wdrożyć ją na środowisko produkcyjne różne. Tych środowisk produkcyjnych zazwyczaj mają różne zestawy wstępnie zainstalowane pakiety. Nie możesz wprowadzać założeń dotyczących manifestu docelowego w takich środowiskach, więc zaleca się użycie `--manifest` opcji [ `dotnet publish` ](../tools/dotnet-publish.md).

## <a name="aspnet-core-implicit-store"></a>Niejawne magazynu platformy ASP.NET Core

Magazyn niejawne platformy ASP.NET Core dotyczy tylko programu ASP.NET Core 2.0. Zdecydowanie zalecamy aplikacje używają platformy ASP.NET Core 2.1 lub nowszą wersją, która obsługuje **nie** Użycie niejawnej magazynu. I późniejszego użycia udostępnionej platformy ASP.NET Core 2.1.

Funkcja Magazyn pakietu środowiska uruchomieniowego jest używany niejawnie przez aplikację ASP.NET Core gdy aplikacja jest wdrożona jako [zależny od struktury wdrożenia (stacje)](index.md#framework-dependent-deployments-fdd) aplikacji. Obiekty docelowe w [ `Microsoft.NET.Sdk.Web` ](https://github.com/aspnet/websdk) obejmują manifesty odwołujące się do niejawnego Magazyn pakietu w systemie docelowym. Ponadto żadnej aplikacji Dyskietki, która jest zależna od `Microsoft.AspNetCore.All` pakietu wyniki w opublikowanej aplikacji, która zawiera tylko aplikacji i jej zasoby i nie pakiety, które zostały wymienione w `Microsoft.AspNetCore.All` meta Microsoft.aspnetcore.all. Zakłada się, że te pakiety są obecne w systemie docelowym.

Magazyn pakietu środowiska uruchomieniowego jest zainstalowany na hoście, gdy jest zainstalowany zestaw .NET Core SDK. Inne pliki instalacyjne może udostępnić Magazyn pakietu środowiska uruchomieniowego, w tym pliku Zip/tar instalacji programu .NET Core SDK `apt-get`, Red Hat Yum, pakiet .NET Core systemu Windows serwer obsługujący i instalacje Magazyn pakietu środowiska uruchomieniowego ręczne.

W przypadku wdrażania [zależny od struktury wdrożenia (stacje)](index.md#framework-dependent-deployments-fdd) aplikacji, upewnij się, że środowisko docelowe ma zainstalowany zestaw .NET Core SDK. Jeśli aplikacja jest wdrażana w środowisku, który nie zawiera programu ASP.NET Core, można zrezygnować z niejawne magazynu, określając  **\<PublishWithAspNetCoreTargetManifest >** równa `false` w pliku projektu, podobnie jak w Poniższy przykład:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> Aby uzyskać [niezależna wdrożenia (— SCD)](index.md#self-contained-deployments-scd) aplikacji, zakłada się, że w systemie docelowym musi nie zawiera wymaganych pakietów manifestu. W związku z tym  **\<PublishWithAspNetCoreTargetManifest >** nie można ustawić `true` — SCD aplikacji.

W przypadku wdrożenia aplikacji za pomocą zależności manifestu, który znajduje się we wdrożeniu (zestawu znajduje się w *bin* folderu), Magazyn pakietu środowiska uruchomieniowego *nie jest używany* na hoście dla tego zestawu. *Bin* folderu zestaw jest używany niezależnie od jego obecność w Magazyn pakietu środowiska uruchomieniowego na hoście.

Wersja zależności wskazane w manifeście musi odpowiadać wersji zależności w Magazyn pakietu środowiska uruchomieniowego. Jeśli istnieje niezgodność wersji między zależności w manifeście docelowej i wersję, która znajduje się w Magazyn pakietu środowiska uruchomieniowego i aplikacja nie obejmuje wymagana wersja pakietu w jej wdrożenia, jej uruchomienie nie powiedzie się. Wyjątek zawiera nazwę manifest docelowego, który wywołał dla zestawu Magazyn pakietu środowiska uruchomieniowego, która pomaga w rozwiązywaniu problemów niezgodność.

Po wdrożeniu *spacje* przy publikowaniu, tylko określone wersje manifestu pakietów, możesz wskazać zostały wstrzymane z opublikowanych danych wyjściowych. Pakiety w wersjach wskazane musi być obecny na hoście dla aplikacji, aby rozpocząć.

## <a name="see-also"></a>Zobacz także

* [polecenia DotNet — publikowanie](../tools/dotnet-publish.md)  
* [Magazyn DotNet](../tools/dotnet-store.md)  
