---
title: "Środowisko uruchomieniowe pakietu magazynu"
description: "W tym temacie opisano magazynie pakietów środowiska uruchomieniowego i manifestów docelowy używana przez .NET Core."
keywords: ".NET i .NET core dotnet magazynu, magazynie pakietów środowiska wykonawczego"
author: bleroy
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 9521d8b4-25fc-412b-a65b-4c975ebf6bfd
ms.openlocfilehash: 607f8259fa6d8488a7fccf3c7d90b6cf40d5f237
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-package-store"></a>Środowisko uruchomieniowe pakietu magazynu

Począwszy od programu .NET Core 2.0 jest możliwe pakietu i wdrażanie aplikacji pod kątem znanych zestawu pakietów, które istnieją w środowisku docelowym. Zalety są szybsze wdrożeń, niższe użycie miejsca na dysku i uruchamiania lepszą wydajność w niektórych przypadkach.

Ta funkcja jest zaimplementowany jako *Magazyn pakietu środowiska uruchomieniowego*, czyli katalogu na dysku przechowywania pakietów (zazwyczaj na */usr/local/share/dotnet/store* na macOS/Linux i *C: / Program plików/dotnet/store* w systemie Windows). W tym katalogu są podkatalogi dla architektury i [platform docelowych](../../standard/frameworks.md). Układ pliku jest podobny sposób, który [NuGet zasoby zostały przedstawione na dysku](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):

\dotnet   
&nbsp;&nbsp;\store   
&nbsp;&nbsp;&nbsp;&nbsp;\x64   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.applicationinsights   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.aspnetcore   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...   
&nbsp;&nbsp;&nbsp;&nbsp;\x86   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.applicationinsights   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.aspnetcore   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...   

A *manifest docelowej* plik zawiera listę pakietów w magazynie pakietów środowiska wykonawczego. Umożliwiają deweloperom tego manifestu podczas publikowania aplikacji. Manifest docelowy jest zwykle zapewniany przez właściciela środowiska produkcyjnego docelowych.

## <a name="preparing-a-runtime-environment"></a>Przygotowywanie środowiska uruchomieniowego

Administrator środowiska uruchomieniowego można zoptymalizować aplikacje dla wdrożeń szybsze i dolnym użycie miejsca na dysku według budynków magazynie pakietów środowiska uruchomieniowego i odpowiednie manifest docelowej.

Pierwszym krokiem jest utworzenie *manifestu sklepu pakietu* który zawiera listę pakietów, które tworzą magazyn pakietu środowiska wykonawczego. Ten format jest zgodny z formatem pliku projektu (*csproj*).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Przykład**

Następujące manifest przykład w magazynie pakietów (*packages.csproj*) służy do dodawania [ `Newtonsoft.Json` ](https://www.nuget.org/packages/Newtonsoft.Json/) i [ `Moq` ](https://www.nuget.org/packages/moq/) do magazynu pakiet środowiska uruchomieniowego:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Udostępnić Magazyn pakietu środowiska uruchomieniowego, wykonując `dotnet store` z manifestu sklepu pakietu, środowisko uruchomieniowe i framework:

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Przykład**

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Wiele ścieżek manifestu sklepu pakietu docelowych można przekazać do pojedynczego [ `dotnet store` ](../tools/dotnet-store.md) polecenia powtarzając opcja i ścieżki w poleceniu.

Domyślnie dane wyjściowe polecenia jest magazynem pakietu w obszarze *.dotnet/store* podkatalogu profilu użytkownika. Możesz określić inną lokalizację przy użyciu `--output <OUTPUT_DIRECTORY>` opcji. Katalog główny magazynu zawiera manifest docelowej *artifact.xml* pliku. Ten plik można udostępnić do pobrania i jest używany przez autorów aplikacji, które ma być docelowa tego magazynu podczas publikowania.

**Przykład**

Następujące *artifact.xml* jest generowany po uruchomieniu w poprzednim przykładzie. Należy pamiętać, że [ `Castle.Core` ](https://www.nuget.org/packages/Castle.Core/) zależą od elementu `Moq`, tak, aby go zostało automatycznie uwzględnione w *artifacts.xml* pliku manifestu.

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Publikowanie aplikacji dla manifest docelowego

Jeśli masz manifestu pliku na dysku docelowym, określ ścieżkę do pliku podczas publikowania aplikacji za pomocą [ `dotnet publish` ](../tools/dotnet-publish.md) polecenia:

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Przykład**

```console
dotnet publish --manifest manifest.xml
```

Wynikowa opublikowanej aplikacji można wdrożyć na środowisku pakietów opisanego w manifeście docelowej. Niepowodzenie w tym przypadku powoduje niepowodzenie uruchomienia aplikacji.

Określ wiele manifestów docelowego podczas publikowania aplikacji przez powtarzające się opcja i ścieżki (na przykład `--manifest manifest1.xml --manifest manifest2.xml`). Po wykonaniu tej aplikacji jest usuwane Unii pakietów określona w plikach manifestu docelowy dostarczony do polecenia.

## <a name="specifying-target-manifests-in-the-project-file"></a>Określanie docelowej manifesty w pliku projektu

Zamiast określania docelowych manifesty z [ `dotnet publish` ](../tools/dotnet-publish.md) ma je określić w pliku projektu jako Rozdzielana średnikami lista ścieżek w ramach polecenie  **\<TargetManifestFiles >** tagu.

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Określ docelowy manifesty w pliku projektu tylko wtedy, gdy dobrze znane, takich jak .NET Core projektów środowiska docelowego dla aplikacji. Nie jest to w przypadku projektów open source. Użytkownicy projekt typu open source zwykle go wdrożyć w różnych środowiskach. Tych środowisk produkcyjnych zazwyczaj mają różne zestawy wstępnie zainstalowane pakiety. Nie można wprowadzić założenia dotyczące manifestu docelowego w takich środowiskach, należy użyć `--manifest` opcji [ `dotnet publish` ](../tools/dotnet-publish.md).

## <a name="aspnet-core-implicit-store"></a>Niejawne magazynu platformy ASP.NET Core

Funkcja Magazyn pakietu środowiska uruchomieniowego służy niejawnie przez aplikację ASP.NET Core gdy aplikacja jest wdrożona jako [wdrożenia framework zależne (stacje)](index.md#framework-dependent-deployments-fdd) aplikacji. Obiekty docelowe w [ `Microsoft.NET.Sdk.Web` ](https://github.com/aspnet/websdk) obejmują manifestów odwołujące się do niejawnego magazynie pakietów w systemie docelowym. Ponadto dowolną aplikację Dyskietki, która jest zależna od `Microsoft.AspNetCore.All` pakietu wyniki w opublikowanej aplikacji, który zawiera tylko aplikacji i jej zasoby i nie pakiety wymienione w `Microsoft.AspNetCore.All` metapackage. Zakłada się, że pakiety są obecne w systemie docelowym.

Magazyn pakietu środowiska uruchomieniowego jest zainstalowana na hoście, po zainstalowaniu programu .NET Core SDK. Inne instalatorów może udostępnić magazyn środowisko uruchomieniowe pakietu, w tym Zip/tarball instalacji programu .NET Core SDK `apt-get`, Red Hat Yum, .NET Core systemu Windows serwer obsługujący pakietu i instalacje magazynie pakietów ręcznego środowiska wykonawczego.

W przypadku wdrażania [wdrożenia framework zależne (stacje)](index.md#framework-dependent-deployments-fdd) aplikacji, upewnij się, że środowisko docelowe ma zainstalowany zestaw .NET Core SDK. Jeśli aplikacja jest wdrażana w środowisku, który nie zawiera platformy ASP.NET Core, można zrezygnować z magazynu niejawne, określając  **\<PublishWithAspNetCoreTargetManifest >** ustawioną `false` w pliku projektu, jak w programie Poniższy przykład:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE] 
> Dla [niezależne wdrożenia (SCD)](index.md#self-contained-deployments-scd) aplikacji, zakłada się, że w systemie docelowym musi nie zawiera wymaganych pakietów manifestu. W związku z tym  **\<PublishWithAspNetCoreTargetManifest >** nie można ustawić `true` SCD aplikacji.

W przypadku wdrożenia aplikacji z zależnością manifestu, który istnieje we wdrożeniu (znajduje się w zestawie *bin* folderu), magazynie pakietów środowiska uruchomieniowego *nie jest używana* na hoście dla tego zestawu. *Bin* folderu zestaw jest używany niezależnie od jej obecności w magazynie pakietów środowiska uruchomieniowego na hoście.

Wersja zależności wskazane w manifeście musi być zgodna wersja zależności w magazynie pakietów środowiska wykonawczego. Jeśli masz niezgodność wersji między zależności w manifeście docelowych i wersji, który istnieje w magazynie pakietów środowiska uruchomieniowego i aplikacji nie zawiera wymaganej wersji pakietu w jego wdrażania, aplikacja nie powiedzie się. Wyjątek zawiera nazwę manifestu docelowych, wymagane zestawu magazynie pakietów środowiska wykonawczego, która pomaga w rozwiązywaniu problemów niezgodność.

Gdy wdrożenie jest *przycięty* przy publikowaniu, określonych wersji manifestu pakietów, należy wskazać zostały wstrzymane z publikowanych danych wyjściowych. Pakiety w wersji wskazane musi być obecny na hoście aplikacji do uruchomienia.

## <a name="see-also"></a>Zobacz także
 [DotNet-publikowania](../tools/dotnet-publish.md)  
 [Magazyn DotNet](../tools/dotnet-store.md)  
