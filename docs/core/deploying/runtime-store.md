---
title: Magazyn pakietu środowiska uruchomieniowego
description: Dowiedz się, jak używać magazynu pakietów środowiska uruchomieniowego do manifestów docelowych używanych przez platformę .NET Core.
ms.date: 08/12/2017
ms.openlocfilehash: 4395370c3bb2d97511d549a63813022fb8cac4b7
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158296"
---
# <a name="runtime-package-store"></a>Magazyn pakietu środowiska uruchomieniowego

Począwszy od platformy .NET Core 2,0, możliwe jest pakowanie i wdrażanie aplikacji względem znanego zestawu pakietów istniejących w środowisku docelowym. Korzyści to szybsze wdrożenia, mniejsze użycie miejsca na dysku i Ulepszona wydajność uruchamiania w niektórych przypadkach.

Ta funkcja jest zaimplementowana jako *Magazyn pakietów środowiska uruchomieniowego*, który jest katalogiem na dysku, na którym są przechowywane pakiety (zwykle w */usr/local/share/dotnet/Store* na macOS/Linux i *C:/pliki programu/dotnet/sklep* w systemie Windows). W tym katalogu znajdują się podkatalogi dla architektury i [platform docelowych](../../standard/frameworks.md). Układ pliku jest podobny do sposobu, w jaki [zasoby programu NuGet są wdrożone na dysku](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):

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

*Docelowy plik manifestu* zawiera listę pakietów w magazynie pakietów środowiska uruchomieniowego. Deweloperzy mogą wskazywać ten manifest podczas publikowania aplikacji. Manifest docelowy jest zwykle dostarczany przez właściciela docelowego środowiska produkcyjnego.

## <a name="preparing-a-runtime-environment"></a>Przygotowywanie środowiska uruchomieniowego

Administrator środowiska uruchomieniowego może zoptymalizować aplikacje dla szybszych wdrożeń i zmniejszyć użycie miejsca na dysku przez utworzenie magazynu pakietów środowiska uruchomieniowego i odpowiedniego manifestu docelowego.

Pierwszym krokiem jest utworzenie *manifestu magazynu pakietów* zawierającego listę pakietów, które tworzą magazyn pakietów środowiska uruchomieniowego. Ten format pliku jest zgodny z formatem pliku projektu (*csproj*).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Przykład**

Następujący przykładowy manifest magazynu pakietów (*Packages. csproj*) służy do dodawania [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) i [`Moq`](https://www.nuget.org/packages/moq/) do magazynu pakietów środowiska uruchomieniowego:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Zainicjuj obsługę magazynu pakietów środowiska uruchomieniowego, wykonując `dotnet store` z manifestem magazynu pakietów, środowiskiem uruchomieniowym i strukturą:

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Przykład**

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Istnieje możliwość przekazania wielu ścieżek manifestu magazynu pakietów docelowych do jednego [`dotnet store`](../tools/dotnet-store.md) polecenia przez powtórzenie opcji i ścieżki w poleceniu.

Domyślnie dane wyjściowe polecenia są magazynem pakietów w podkatalogu *. dotnet/Store* w profilu użytkownika. Możesz określić inną lokalizację przy użyciu `--output <OUTPUT_DIRECTORY>` opcji. Katalog główny magazynu zawiera docelowy plik *artefaktu* manifestu. Ten plik można udostępnić do pobrania i będzie używany przez autorów aplikacji, którzy chcą wskazać ten magazyn podczas publikowania.

**Przykład**

Następujący plik *artefaktu. XML* jest generowany po uruchomieniu poprzedniego przykładu. Należy pamiętać [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) `Moq`, że jest to zależność, dlatego jest dołączona automatycznie i pojawia się w pliku manifestu *artefakts. XML* .

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Publikowanie aplikacji w manifeście docelowym

Jeśli na dysku znajduje się docelowy plik manifestu, należy określić ścieżkę do pliku podczas publikowania aplikacji za pomocą [`dotnet publish`](../tools/dotnet-publish.md) polecenia:

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Przykład**

```dotnetcli
dotnet publish --manifest manifest.xml
```

Opublikowana aplikacja jest wdrażana w środowisku z pakietami opisanymi w manifeście docelowym. Wykonanie tej czynności spowoduje niepowodzenie uruchomienia aplikacji.

Określ wiele manifestów docelowych podczas publikowania aplikacji przez powtórzenie opcji i ścieżki (na przykład `--manifest manifest1.xml --manifest manifest2.xml`). Gdy to zrobisz, aplikacja zostanie przycięta dla związku z pakietami określonymi w docelowym pliku manifestu dostarczanym do polecenia.

W przypadku wdrożenia aplikacji z zależnością manifestu, która znajduje się we wdrożeniu (zestaw jest obecny w folderze *bin* ), magazyn pakietów środowiska uruchomieniowego *nie jest używany* na hoście dla tego zestawu. Zestaw folderu *bin* jest używany niezależnie od jego obecności w magazynie pakietów środowiska uruchomieniowego na hoście.

Wersja zależności wskazanej w manifeście musi być zgodna z wersją zależności w magazynie pakietów środowiska uruchomieniowego. Jeśli masz niezgodność wersji między zależnością w manifeście docelowym a wersją, która istnieje w magazynie pakietów środowiska uruchomieniowego, a aplikacja nie zawiera wymaganej wersji pakietu w jej wdrożeniu, uruchomienie aplikacji nie powiedzie się. Wyjątek zawiera nazwę manifestu docelowego, który został wywołany dla zestawu magazynu pakietów środowiska uruchomieniowego, co pomaga w rozwiązywaniu problemów z niezgodnością.

Gdy wdrożenie zostanie *przycięte* po opublikowaniu, tylko określone wersje pakietów manifestu są potrącane z publikowanych danych wyjściowych. Pakiety na wskazanych wersjach muszą być obecne na hoście, aby można było uruchomić aplikację.

## <a name="specifying-target-manifests-in-the-project-file"></a>Określanie manifestów docelowych w pliku projektu

Alternatywą dla określenia manifestów docelowych za pomocą [`dotnet publish`](../tools/dotnet-publish.md) polecenia jest określenie ich w pliku projektu jako listę ścieżek rozdzielonych średnikami pod tagiem ** \<TargetManifestFiles>** .

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Określ docelowe manifesty w pliku projektu tylko wtedy, gdy Środowisko docelowe dla aplikacji jest dobrze znane, na przykład w przypadku projektów .NET Core. Nie jest to przypadek dla projektów open source. Użytkownicy projektu typu open source zwykle wdrażają je w różnych środowiskach produkcyjnych. W tych środowiskach produkcyjnych ogólnie zainstalowano różne zestawy pakietów. Nie można tworzyć założeń dotyczących manifestu docelowego w takich środowiskach, dlatego należy użyć `--manifest` opcji. [`dotnet publish`](../tools/dotnet-publish.md)

## <a name="aspnet-core-implicit-store-net-core-20-only"></a>Niejawny magazyn ASP.NET Core (tylko w przypadku programu .NET Core 2,0)

Niejawny magazyn ASP.NET Core ma zastosowanie tylko do ASP.NET Core 2,0. Zdecydowanie zalecamy stosowanie aplikacji ASP.NET Core 2,1 i nowszych, które **nie** korzystają z magazynu niejawnego. ASP.NET Core 2,1 i później używają udostępnionej platformy.

W przypadku platformy .NET Core 2,0 funkcja magazynu pakietów środowiska uruchomieniowego jest używana niejawnie przez aplikację ASP.NET Core, gdy aplikacja jest wdrażana jako aplikacja [wdrożenia zależna od środowiska uruchomieniowego](index.md#publish-runtime-dependent) . Elementy docelowe w [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) programie zawierają manifesty odwołujące się do niejawnego magazynu pakietów w systemie docelowym. Ponadto wszystkie aplikacje zależne od środowiska uruchomieniowego, które są `Microsoft.AspNetCore.All` zależne od pakietu, mają opublikowaną aplikację, która zawiera tylko aplikację i jej zasoby, a nie pakiety `Microsoft.AspNetCore.All` wymienione w pakiecie. Przyjęto założenie, że te pakiety znajdują się w systemie docelowym.

Magazyn pakietów środowiska uruchomieniowego jest instalowany na hoście, gdy zainstalowano zestaw .NET Core SDK. Inne Instalatory mogą dostarczyć magazyn pakietów środowiska uruchomieniowego, w tym instalacje zip/plik tar zestaw .NET Core SDK, `apt-get`Red Hat yum, pakiet hostingu platformy .NET Core z systemem Windows Server i ręczne instalacje magazynu pakietów w środowisku uruchomieniowym.

Podczas wdrażania aplikacji [wdrożenia zależnej od środowiska uruchomieniowego](index.md#publish-runtime-dependent) upewnij się, że środowisko docelowe ma zainstalowaną zestaw .NET Core SDK. Jeśli aplikacja jest wdrażana w środowisku, które nie zawiera ASP.NET Core, można zrezygnować z niejawnego magazynu przez określenie ** \<PublishWithAspNetCoreTargetManifest>** ustawionej `false` na wartość w pliku projektu, jak w poniższym przykładzie:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> W przypadku aplikacji do [samodzielnego wdrażania](index.md#publish-self-contained) zakłada się, że system docelowy nie musi zawierać wymaganych pakietów manifestu. W związku z tym ** \<PublishWithAspNetCoreTargetManifest>** nie można `true` ustawić na dla aplikacji samodzielnej.

## <a name="see-also"></a>Zobacz też

- [dotnet — publikowanie](../tools/dotnet-publish.md)
- [dotnet — sklep](../tools/dotnet-store.md)
