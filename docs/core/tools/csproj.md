---
title: Dodatki do formatu csproj dla platformy .NET Core
description: Więcej informacji na temat różnic między istniejących i pliki csproj .NET Core
keywords: odwołanie, csproj, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
ms.workload:
- dotnetcore
ms.openlocfilehash: fdf91bdb24819c2d92b708e5937980ac2fb0d5fc
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Dodatki do formatu csproj dla platformy .NET Core

W tym dokumencie przedstawiono zmiany, które zostały dodane do plików projektu jako część przejście od *project.json* do *csproj* i [MSBuild](https://github.com/Microsoft/MSBuild). Aby uzyskać więcej informacji o składni pliku ogólnego projektu i odwołania, zobacz [pliku projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentacji.  

## <a name="implicit-package-references"></a>Odwołania do pakietu niejawne
Metapackages są niejawne odwołania w oparciu framework(s) docelowych określonych w `<TargetFramework>` lub `<TargetFrameworks>` właściwości pliku projektu. `<TargetFrameworks>` jest ignorowana, jeśli `<TargetFramework>` jest określony, niezależnie od kolejności.

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp1.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp1.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a>Zalecenia
Ponieważ `Microsoft.NETCore.App` lub `NetStandard.Library` metapackages niejawne są odwołania, Oto nasze najlepsze rozwiązania:

* Jeśli oprogramowanie .NET Core lub .NET Standard, nigdy nie ma jawnego odwołania do `Microsoft.NETCore.App` lub `NetStandard.Library` metapackages za pośrednictwem `<PackageReference>` elementu w pliku projektu.
* Jeśli potrzebujesz określonej wersji środowiska uruchomieniowego podczas określania wartości docelowej platformy .NET Core, należy użyć `<RuntimeFrameworkVersion>` właściwości projektu (na przykład `1.0.4`) zamiast odwołania do metapackage.
    * Taka sytuacja może wystąpić, jeśli używasz [niezależne wdrożeń](../deploying/index.md#self-contained-deployments-scd) i wymagają poprawek określonych wersji 1.0.0 środowiska uruchomieniowego LTS, na przykład.
* Jeśli potrzebujesz określonej wersji `NetStandard.Library` metapackage podczas określania wartości docelowej platformy .NET Standard, można użyć `<NetStandardImplicitPackageVersion>` właściwości i ustaw wersję.
* Nie jawnie dodać lub zaktualizować odwołania do albo `Microsoft.NETCore.App` lub `NetStandard.Library` metapackage w projektach platformy .NET Framework. Jeśli jakakolwiek wersja `NetStandard.Library` potrzebne w przypadku, gdy przy użyciu pakietu NuGet .NET Standard na podstawie, NuGet automatycznie instaluje tę wersję.

## <a name="default-compilation-includes-in-net-core-projects"></a>Zawiera domyślne kompilacji w projektach platformy .NET Core
Wraz z przejściem do *csproj* format w najnowszej wersji zestawu SDK, Przeprowadziliśmy domyślna obejmuje i wyklucza elementów kompilacji i zasoby osadzone w plikach właściwości zestawu SDK. Oznacza to, że nie należy określić te elementy w pliku projektu. 

Głównym celem tej czynności jest aby zwiększyć czytelność w pliku projektu. Wartości domyślne, które znajdują się w zestawie SDK obejmuje najbardziej typowe przypadki użycia, więc nie trzeba powtórzyć je w każdym projekcie, który utworzono. Prowadzi to do mniejsze pliki projektu, które są znacznie łatwiejsze do zrozumienia, jak również edytować ręcznie, jeśli to konieczne. 

W poniższej tabeli przedstawiono, który element i które [globs](https://en.wikipedia.org/wiki/Glob_(programming)) zarówno uwzględniać i wykluczone w zestawie SDK: 

| Element           | Obejmują glob                              | Wyklucz glob                                                  | Usuń glob                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Kompilacji           | \*\*/\*.cs (lub inne rozszerzenia językowe) | \*\*/\*.user;  \*\*/\*.\* Proj;  \* \* / \*.sln;  \* \* / \*.vssscc  | Brak                        |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\* Proj; \* \* / \*.sln; \* \* / \*.vssscc     | Brak                        |
| Brak              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\* Proj; \* \* / \*.sln; \* \* / \*.vssscc     | - \*\*/\*.cs; \*\*/\*.resx |

Jeśli masz globs w projekcie i zostanie podjęta próba skompiluj go przy użyciu najnowszego zestawu SDK, zostanie wyświetlony następujący błąd:

> Zduplikowane elementy kompilacji nie został dołączony. Domyślnie zestawu .NET SDK zawiera elementy kompilacji z katalogu projektu. Możesz usunąć te elementy z pliku projektu lub ustaw właściwość "EnableDefaultCompileItems" na "fałsz", aby jawnie umieszczone w pliku projektu. 

Aby uzyskać uniknąć tego błędu, można usunąć jawnych `Compile` elementy, które są zgodne z typami wymienione w powyższej tabeli, lub możesz ustawić `<EnableDefaultCompileItems>` właściwości `false`, podobnie do następującej:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
Ustawienie tej właściwości na `false` spowoduje zastąpienie niejawnego dołączania i zachowanie zostanie przywrócona do poprzedniego zestawów SDK, który wymagał Określ globs domyślne w projekcie. 

Ta zmiana nie modyfikuje głównym obejmuje mechanika innych. Jednak jeśli chcesz określić, na przykład niektóre pliki do opublikowany z aplikacji, nadal można znane mechanizmów w *csproj* tego (na przykład `<Content>` elementu).

`<EnableDefaultCompileItems>` powoduje wyłączenie `Compile` globs, ale nie ma wpływu na inne globs, takich jak niejawne `None` glob, które mają zastosowanie również do \*.cs elementów. Z tego powodu **Eksploratora rozwiązań** będzie Pokaż \*elementów .cs w ramach projektu, zawarty jako `None` elementów. W podobny sposób można użyć `<EnableDefaultNoneItems>` wyłączyć niejawne `None` glob.

Aby wyłączyć **wszystkie niejawne globs**, można ustawić `<EnableDefaultItems>` właściwości `false` jak w poniższym przykładzie:
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a>Zalecenia
Z csproj zaleca się, usuń domyślne globs z projektu i dodawać tylko ścieżki plików z globs tych artefaktów potrzebnych aplikacji/biblioteki dla różnych scenariuszy (na przykład środowiska uruchomieniowego i tworzenia pakietów NuGet).

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Jak wyświetlać całego projektu MSBuild widzi ona

Podczas zmiany csproj znacznego uproszczenia pliki projektu, można zobaczyć rozwinięty projektu MSBuild go widzi, gdy zestaw SDK i obiekty docelowe są uwzględniane. Przetwarzanie wstępne projektu z [ `/pp` przełącznika](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) z [ `dotnet msbuild` ](dotnet-msbuild.md) polecenia, która zawiera pliki, które zostaną zaimportowane, ich źródła, a ich wkład do kompilacji bez rzeczywistego Tworzenie projektu:

`dotnet msbuild /pp:fullproject.xml`

Jeśli projekt zawiera wiele platform docelowych, wyniki polecenia powinna zostać zwrócona na tylko jeden z nich, określając jako właściwość MSBuild:

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a>Dodatki

### <a name="sdk-attribute"></a>Atrybut zestawu SDK 
`<Project>` Elementu *.csproj* plik ma nowy atrybut o nazwie `Sdk`. `Sdk` Określa, która zestawu SDK będą używane przez projekt. Zestaw SDK, jako [dokumentu Tworzenie warstw](cli-msbuild-architecture.md) opisuje, to zbiór MSBuild [zadania](/visualstudio/msbuild/msbuild-tasks) i [cele](/visualstudio/msbuild/msbuild-targets) który kompilacji kodu .NET Core. Możemy wysłać dwóch głównych zestawów SDK przy użyciu narzędzi platformy .NET Core:

1. .NET Core SDK o identyfikatorze `Microsoft.NET.Sdk`
2. Zestaw SDK o identyfikatorze sieci web .NET Core `Microsoft.NET.Sdk.Web`

Musisz mieć `Sdk` atrybutu zestawu do jednego z tych identyfikatorów `<Project>` element, aby można było używać narzędzi platformy .NET Core i kompilacji kodu. 

### <a name="packagereference"></a>PackageReference
Element, który określa zależności NuGet w projekcie. `Include` Atrybut określa identyfikator pakietu. 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Wersja
`Version` Określa wersję pakietu do przywrócenia. Atrybut przestrzega zasad [wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges) schematu. Domyślnym zachowaniem jest dopasowanie dokładnej wersji. Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji NuGet `[1.2.3]` dla 1.2.3 dokładną wersję pakietu.

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets, ExcludeAssets i PrivateAssets
`IncludeAssets` atrybut określa zasoby należące do pakietu określony przez `<PackageReference>` powinny być używane. 

`ExcludeAssets` atrybut określa zasoby należące do pakietu określony przez `<PackageReference>` nie powinny być używane.

`PrivateAssets` atrybut określa zasoby należące do pakietu określony przez `<PackageReference>` powinny być używane, ale ten powinien przechodzi do następnego projektu. 

> [!NOTE]
> `PrivateAssets` jest odpowiednikiem *project.json*/*xproj* `SuppressParent` elementu.

Te atrybuty może zawierać jeden lub więcej z następujących elementów:

* `Compile` — zawartość folderu lib są dostępne do skompilowania przed.
* `Runtime` — są dystrybuowane zawartość folderu środowiska wykonawczego.
* `ContentFiles` — zawartość *pliki* folderu są używane.
* `Build` — właściwości/cele w folderze kompilacji są używane.
* `Native` — zawartość z zasobów natywnych są kopiowane do folderu wyjściowego w czasie wykonywania.
* `Analyzers` — analizatorów są używane.

Alternatywnie może zawierać atrybutu:

* `None` — nie zasoby zostały użyte.
* `All` — wszystkie zasoby są używane.

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference
`<DotNetCliToolReference>` element elementu określa narzędzie interfejsu wiersza polecenia, które użytkownik chce przywrócić w kontekście projektu. Nie zastępuje `tools` w węźle *project.json*. 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a>Wersja
`Version` Określa wersję pakietu do przywrócenia. Atrybut przestrzega zasad [wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges) schematu. Domyślnym zachowaniem jest dopasowanie dokładnej wersji. Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji NuGet `[1.2.3]` dla 1.2.3 dokładną wersję pakietu.

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers
`<RuntimeIdentifiers>` Element umożliwia określenie Rozdzielana średnikami lista [identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu. Włącz RID publikowania niezależne wdrożeń. 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>RuntimeIdentifier
`<RuntimeIdentifier>` Elementu można określić tylko jeden [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu. Włącz RID publikowania niezależne wdrożenia. 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a>PackageTargetFallback 
`<PackageTargetFallback>` Element służy do określenia zestawu zgodne cele, które mają być użyte podczas przywracania pakietów. Został zaprojektowany tak, aby umożliwić pakiety, które używają dotnet [TxM (Moniker docelowej x)](/nuget/schema/target-frameworks) do pracy z pakietami, które nie deklaruje dotnet TxM. Jeśli projekt używa dotnet TxM, a następnie wszystkie pakiety zależy on od musi również mieć dotnet TxM, chyba że dodasz `<PackageTargetFallback>` do projektu, aby umożliwić platformy dotnet z systemem innym niż był zgodny z dotnet. 

W poniższym przykładzie przedstawiono przejścia dla wszystkich obiektów docelowych w projekcie: 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

W poniższym przykładzie przejścia tylko w przypadku `netcoreapp1.0` docelowych:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a>Właściwości metadanych NuGet
Wraz z przejściem do MSbuild został przeniesiony wejściowych metadanych, które jest używany podczas pakowania pakietu NuGet z *project.json* do *.csproj* plików. Dane wejściowe są właściwości programu MSBuild, więc Przejdź w `<PropertyGroup>` grupy. Poniżej przedstawiono listę właściwości, które są używane jako dane wejściowe do procesu pakowania, korzystając z `dotnet pack` polecenia lub `Pack` MSBuild będący celem część zestawu SDK. 

### <a name="ispackable"></a>IsPackable
Wartość logiczna określająca, czy można zapakować projektu. Wartość domyślna to `true`. 

### <a name="packageversion"></a>PackageVersion
Określa wersję mające wynikowy pakiet. Akceptuje wszystkie formularze ciąg wersji NuGet. Domyślnie jest wartość `$(Version)`, która jest właściwości `Version` w projekcie. 

### <a name="packageid"></a>PackageId
Określa nazwę pakietu wynikowy. Jeśli nie zostanie określony, `pack` operacji domyślnie zostanie ustawiona przy użyciu `AssemblyName` lub nazwa katalogu jako nazwę pakietu. 

### <a name="title"></a>Tytuł
Tytuł przyjaznych dla człowieka pakietu, zwykle używanych w wyświetla interfejsu użytkownika na nuget.org i Menedżera pakietów w programie Visual Studio. Jeśli nie zostanie określony, zamiast niego jest używana identyfikator pakietu.

### <a name="authors"></a>Autorzy
Rozdzielana średnikami lista autorzy pakietów, zgodne z nazwami profilu na nuget.org. Te są wyświetlane w galerii NuGet w nuget.org i są odwoływania się do pakietów przez tego samego autorów.

### <a name="description"></a>Opis
Długi opis pakietu do wyświetlenia interfejsu użytkownika.

### <a name="copyright"></a>Copyright
Praw autorskich szczegóły pakietu.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAcceptance
Wartość logiczna określająca, czy klient musi monitować o konsumenta, aby zaakceptować licencji pakietu przed zainstalowaniem pakietu. Wartość domyślna to `false`.

### <a name="packagelicenseurl"></a>PackageLicenseUrl
Adres URL licencji, która ma zastosowanie do pakietu.

### <a name="packageprojecturl"></a>PackageProjectUrl
Wyświetla adres URL strony głównej pakietu, często są wyświetlane w interfejsie użytkownika oraz nuget.org.

### <a name="packageiconurl"></a>PackageIconUrl
Adres URL obrazu 64 x 64 z przezroczyste tło do użycia jako ikonę pakietu w wyświetlania interfejsu użytkownika.

### <a name="packagereleasenotes"></a>PackageReleaseNotes
Informacje o wersji dla pakietu.

### <a name="packagetags"></a>PackageTags
Rozdzielaną średnikami listę znaczników, który wyznacza pakietu.

### <a name="packageoutputpath"></a>PackageOutputPath
Określa ścieżki wyjściowej, w którym spakowany pakiet zostanie porzucony. Wartość domyślna to `$(OutputPath)`. 

### <a name="includesymbols"></a>IncludeSymbols
Ta wartość logiczna wskazuje, czy pakiet należy utworzyć pakiet symboli dodatkowych podczas spakowane projektu. Ten pakiet będzie mieć *. symbols.nupkg* rozszerzenia i skopiuje pliki PDB wraz z biblioteki DLL i inne pliki danych wyjściowych.

### <a name="includesource"></a>IncludeSource
Ta wartość logiczna wskazuje, czy Proces pakietu należy utworzyć pakiet źródła. Źródłowy pakiet zawiera biblioteki kodu źródłowego oraz pliki PDB. Pliki źródłowe są umieszczane w obszarze `src/ProjectName` katalogu w wynikowym pliku pakietu. 

### <a name="istool"></a>IsTool
Określa, czy wszystkie pliki wyjściowe są kopiowane do *narzędzia* folder zamiast *lib* folderu. Należy pamiętać, że jest inny niż `DotNetCliTool` który jest określany przez ustawienie `PackageType` w *.csproj* pliku.

### <a name="repositoryurl"></a>RepositoryUrl
Określa adres URL repozytorium, gdzie znajduje się kod źródłowy dla pakietu i/lub z którego jest ona kompilowana. 

### <a name="repositorytype"></a>RepositoryType
Określa typ repozytorium. Domyślna to "git". 

### <a name="nopackageanalysis"></a>NoPackageAnalysis
Określa, że pakiet nie należy uruchamiać analizy pakietu po utworzeniu pakietu.

### <a name="minclientversion"></a>Element MinClientVersion
Określa minimalną wersję klienta NuGet, który można zainstalować ten pakiet, wymuszane przez nuget.exe i Menedżer pakietów programu Visual Studio.

### <a name="includebuildoutput"></a>IncludeBuildOutput
Tej wartości logiczna określa, czy zestawy danych wyjściowych kompilacji powinien zapewniać do *.nupkg* pliku lub nie.

### <a name="includecontentinpack"></a>IncludeContentInPack
Ta wartość logiczna określa, czy wszystkie elementy które mają typ `Content` zostaną uwzględnione w pakiecie wynikowy automatycznie. Wartość domyślna to `true`. 

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder
Określa folder, gdzie umieścić zestawy danych wyjściowych. Zestawy danych wyjściowych (i inne pliki wyjściowe) są kopiowane do ich odpowiednich framework folderów.

### <a name="contenttargetfolders"></a>ContentTargetFolders
Ta właściwość określa domyślną lokalizację gdzie powinien pojawiać wszystkie pliki zawartości, jeśli `PackagePath` nie jest określony dla nich. Wartość domyślna to "zawartość; pliki".

### <a name="nuspecfile"></a>NuspecFile
Ścieżka względna lub bezwzględna do *.nuspec* pliku używany na potrzeby pakowania. 

> [!NOTE]
> Jeśli *.nuspec* określony plik, jest on używany **wyłącznie** dla pakowania informacji i informacje w projektach nie jest używany. 

### <a name="nuspecbasepath"></a>NuspecBasePath
Podstawowa ścieżka dla *.nuspec* pliku.

### <a name="nuspecproperties"></a>NuspecProperties
Rozdzielana średnikami lista kluczy = pary wartości.
