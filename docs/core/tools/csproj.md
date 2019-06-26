---
title: Dodatki do formatu csproj dla platformy .NET Core
description: Dowiedz się więcej o różnicach między istniejące i pliki csproj .NET Core
ms.date: 04/08/2019
ms.openlocfilehash: a9b1caf6068a7161258a6825ed16894ac41b3be7
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397535"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Dodatki do formatu csproj dla platformy .NET Core

W tym dokumencie opisano zmiany, które zostały dodane w plikach projektu jako część przeniesienia z *project.json* do *csproj* i [MSBuild](https://github.com/Microsoft/MSBuild). Aby uzyskać więcej informacji na temat składni pliku ogólnego projektu i odwołania, zobacz [plik projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentacji.

## <a name="implicit-package-references"></a>Odwołania do pakietu niejawne

Metapakiety niejawnie są określone w oparciu o framework(s) docelowej, określone w `<TargetFramework>` lub `<TargetFrameworks>` właściwości pliku projektu. `<TargetFrameworks>` jest ignorowana, jeśli `<TargetFramework>` jest określony, niezależnie od kolejności. Aby uzyskać więcej informacji, zobacz [pakiety, metapakiety i struktury](../packages.md). 

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp2.1</TargetFramework>
 </PropertyGroup>
 ```

 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a>Zalecenia

Ponieważ `Microsoft.NETCore.App` lub `NETStandard.Library` metapakiety niejawnie są wywoływane, Oto nasze zalecane najlepsze rozwiązania:

* Podczas określania wartości docelowej platformy .NET Core lub .NET Standard, nigdy nie mają wyraźne odniesienie do `Microsoft.NETCore.App` lub `NETStandard.Library` metapakiety za pośrednictwem `<PackageReference>` elementu w pliku projektu.
* Jeśli potrzebujesz określonej wersji środowiska uruchomieniowego podczas określania wartości docelowej platformy .NET Core, należy użyć `<RuntimeFrameworkVersion>` właściwość w projekcie (na przykład `1.0.4`) zamiast odwoływać się do meta Microsoft.aspnetcore.all.
  * Może się to zdarzyć, jeśli używasz [niezależna wdrożeń](../deploying/index.md#self-contained-deployments-scd) i należy określona poprawka wersję 1.0.0 LTS środowiska uruchomieniowego, na przykład.
* Jeśli potrzebujesz określonej wersji `NETStandard.Library` meta Microsoft.aspnetcore.all podczas przeznaczonych dla platformy .NET Standard, możesz użyć `<NetStandardImplicitPackageVersion>` właściwości i wersji zestawu.
* Nie jawnie dodać lub zaktualizować odwołania do albo `Microsoft.NETCore.App` lub `NETStandard.Library` meta Microsoft.aspnetcore.all w projektach .NET Framework. Jeśli jakakolwiek wersja `NETStandard.Library` jest wymagana, gdy przy użyciu pakietu NuGet oparte na .NET Standard, NuGet automatycznie instaluje tę wersję.

## <a name="implicit-version-for-some-package-references"></a>Niejawne wersji niektóre odwołania do pakietu

Większość użycia [ `<PackageReference>` ](#packagereference) wymagane ustawienie `Version` atrybutu, aby określić wersję pakietu NuGet, który ma być używany. Korzystając z platformy .NET Core 2.1 lub 2,2 i odwołujący się [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) lub [pakiet](/aspnet/core/fundamentals/metapackage), jednak ten atrybut nie jest konieczne. .NET Core SDK automatycznie wybrać wersję te pakiety, które powinny być używane.

### <a name="recommendation"></a>Zalecenie

Podczas odwoływania się do `Microsoft.AspNetCore.App` lub `Microsoft.AspNetCore.All` pakietów, nie należy określać ich wersji. Jeśli wersja jest określony, zestaw SDK może generować ostrzeżenie NETSDK1071. Aby usunąć to ostrzeżenie, Usuń wersję pakietu jak w poniższym przykładzie:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> Znany problem: zestaw SDK programu .NET Core 2.1 obsługiwana tylko w tej składni projekt używa również Microsoft.NET.Sdk.Web. Ten problem jest rozwiązany w .NET Core 2.2 SDK.

Te odwołania do platformy ASP.NET Core metapakiety ma nieco inne zachowanie z większości zwykłych pakietów NuGet. [Zależny od struktury wdrożeń](../deploying/index.md#framework-dependent-deployments-fdd) aplikacji używających tych metapakiety automatycznie korzystać z udostępnionej platformy ASP.NET Core. Gdy używasz metapakiety **nie** zasoby z pakietów platformy ASP.NET Core NuGet, do którego istnieje odwołanie, są wdrażane przy użyciu aplikacji — udostępnionej platformy ASP.NET Core zawiera te zasoby. Zasoby w ramach udostępnionego są zoptymalizowane pod kątem platformy docelowej poprawić czas uruchamiania aplikacji. Aby uzyskać więcej informacji na temat struktury udostępnione Zobacz [tworzenie pakietów dystrybucji platformy .NET Core](../build/distribution-packaging.md).

Jeśli jakaś wersja *jest* określone, jest ona traktowana jako *minimalne* wersję udostępnionej platformy ASP.NET Core dla wdrożeń zależny od struktury oraz *dokładnie* wersji niezależne wdrożenia. Może to mieć następujące konsekwencje:

* Jeśli na zainstalowana wersja programu ASP.NET Core serwer jest starsza niż wersja określona w funkcji PackageReference, nie może uruchomić procesu platformy .NET Core. Aktualizacje meta Microsoft.aspnetcore.all są często dostępne w witrynie NuGet.org, zanim aktualizacje zostały udostępnione w środowiskach, takich jak Azure hostingu. Aktualizowanie wersji na PackageReference do platformy ASP.NET Core może spowodować awarię wdrożonej aplikacji.
* Jeśli aplikacja jest wdrażana jako [niezależna wdrożenia](../deploying/index.md#self-contained-deployments-scd), aplikacja nie może zawierać najnowsze aktualizacje zabezpieczeń w programie .NET Core. Jeśli wersja nie jest określona, zestaw SDK automatycznie dołączać najnowszą wersję platformy ASP.NET Core we wdrożeniu niezależna.

## <a name="default-compilation-includes-in-net-core-projects"></a>Kompilacja domyślna obejmuje w projektach .NET Core

Wraz z przejściem do *csproj* format w najnowszych wersjach zestawu SDK, zmieniliśmy domyślnie zawiera i nie obejmuje elementy kompilacji i zasoby osadzone pliki właściwości zestawu SDK. Oznacza to, że nie należy określić te elementy w pliku projektu.

Głównym powodem w ten sposób jest zaśmiecać w pliku projektu. Wartości domyślne, które znajdują się w zestawie SDK obejmuje najbardziej typowe przypadki użycia, więc nie ma potrzeby powtarzanie ich każdego projektu, które tworzysz. Prowadzi to do mniejsze pliki projektu, które są znacznie łatwiejsze do zrozumienia, jak również edytować ręcznie, jeśli to konieczne.

W poniższej tabeli przedstawiono, które element oraz tych, które [elementy globalne](https://en.wikipedia.org/wiki/Glob_(programming)) zarówno uwzględniać i wykluczone w zestawie SDK:

| Element           | Obejmują glob                              | Wyklucz glob                                                  | Usuń glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Kompilacji           | \*\*/\*CS (lub inne rozszerzenia językowe) | \*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc  | Brak                      |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | Brak                      |
| Brak              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | \*\*/\*.cs; \*\*/\*.resx   |

> [!NOTE]
> **Wyklucz glob** zawsze wyklucza `./bin` i `./obj` foldery, które są reprezentowane przez `$(BaseOutputPath)` i `$(BaseIntermediateOutputPath)` właściwości programu MSBuild, odpowiednio. Podsumowując, wyklucza wszystkie są reprezentowane przez `$(DefaultItemExcludes)`.

Jeśli podczas próby utworzenia go za pomocą zestawu SDK najnowsze elementy globalne są zdefiniowane w projekcie, otrzymasz następujący błąd:

> Zduplikowane elementy kompilacji zostaną uwzględnione. Zestaw SDK platformy .NET obejmuje elementy kompilacji z katalogu projektu domyślnie. Możesz usunąć te elementy z pliku projektu lub ustaw właściwość "EnableDefaultCompileItems", "false", jeśli chcesz jawnie umieszczone w pliku projektu.

Aby obejść ten błąd, można usunąć jawne `Compile` elementy, które są zgodne z typami wymienionych w powyższej tabeli, można także ustawić `<EnableDefaultCompileItems>` właściwości `false`, podobnie do następującego:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Ustawienie tej właściwości na `false` spowoduje wyłączenie włączenia niejawne, przywrócenie zachowania poprzedniego zestawów SDK, który wymagał określić elementy domyślne globalne w projekcie.

Ta zmiana nie powoduje modyfikacji głównego zawiera mechanika innych. Jednak jeśli chcesz określić, na przykład, niektóre pliki na publikowaniu z Twoją aplikacją, nadal można znanych mechanizmów w *csproj* do tego (na przykład `<Content>` elementu).

`<EnableDefaultCompileItems>` powoduje wyłączenie tylko `Compile` elementy globalne, ale nie ma wpływu na inne elementy globalne, takich jak niejawny `None` glob, która ma zastosowanie również do \*.cs elementów. Z tego powodu **Eksploratora rozwiązań** będą nadal show \*.cs elementy w ramach projektu, dołączone jako `None` elementów. W podobny sposób można ustawić `<EnableDefaultNoneItems>` wartość false, aby wyłączyć niejawny `None` glob w następujący sposób:

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Aby wyłączyć **wszystkie niejawne elementy globalne**, można ustawić `<EnableDefaultItems>` właściwość `false` jak w poniższym przykładzie:

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Jak wyświetlić całego projektu, jak MSBuild widzi on

Chociaż te zmiany w pliku csproj znacznie upraszczają pliki projektu, możesz chcieć wyświetlaną w pełni rozwinięte projektu MSBuild widzi on po zestawie SDK i jego obiekty docelowe są uwzględniane. Przetwarzanie wstępne projektu z [ `/pp` Przełącz](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) z [ `dotnet msbuild` ](dotnet-msbuild.md) polecenia, które pokazują, które pliki są importowane, ich źródła i materiały przekazywane do kompilacji bez faktycznego Tworzenie projektu:

`dotnet msbuild -pp:fullproject.xml`

Jeśli projekt zawiera wiele platform docelowych, wyniki polecenia powinna zostać zwrócona na tylko jeden z nich, określając ją jako właściwość narzędzia MSBuild:

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>Dodatki

### <a name="sdk-attribute"></a>Atrybutu zestawu SDK

Katalog główny `<Project>` elementu *.csproj* plik ma nowy atrybut o nazwie `Sdk`. `Sdk` Określa zestaw SDK będzie używane przez projekt. Zestaw SDK, jako [dokumentu warstwowe](cli-msbuild-architecture.md) opisuje, to zbiór MSBuild [zadania](/visualstudio/msbuild/msbuild-tasks) i [cele](/visualstudio/msbuild/msbuild-targets) , można tworzyć kod platformy .NET Core. Publikujemy trzech głównych zestawów SDK z narzędziami .NET Core i dodatkowe dwa zestawy SDK podczas korzystania z programu .NET Core 3.0 w wersji zapoznawczej:

1. .NET Core SDK o identyfikatorze `Microsoft.NET.Sdk`
2. .NET Core web SDK o identyfikatorze `Microsoft.NET.Sdk.Web`
3. Biblioteki klas Razor platformy .NET Core SDK z Identyfikatorem programu `Microsoft.NET.Sdk.Razor`
4. Usługa procesu roboczego platformy .NET Core, o identyfikatorze `Microsoft.NET.Sdk.Worker` (.NET Core 3.0 w wersji zapoznawczej)
5. .NET Core WinForms i WPF o identyfikatorze `Microsoft.NET.Sdk.WindowsDesktop` (.NET Core 3.0 w wersji zapoznawczej)

Musisz mieć `Sdk` atrybut do jednego z tych identyfikatorów w `<Project>` element, aby użyć narzędzi .NET Core i kompilowanie kodu.

### <a name="packagereference"></a>PackageReference

A `<PackageReference>` określa elementu [zależności NuGet w projekcie](/nuget/consume-packages/package-references-in-project-files). `Include` Atrybut określa identyfikator pakietu.

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Wersja

Wymagane `Version` atrybut określa numer wersji pakietu do przywrócenia. Ten atrybut przestrzega zasad [wersji NuGet](/nuget/reference/package-versioning#version-ranges-and-wildcards) schematu. Domyślnym zachowaniem jest dokładna wersja dopasowania. Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji NuGet `[1.2.3]` dla 1.2.3 dokładną wersję pakietu.

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets, ExcludeAssets i PrivateAssets

`IncludeAssets` atrybut określa, które zasoby należące do pakietu określony przez `<PackageReference>` powinny być używane. Domyślnie uwzględniane są wszystkie zasoby pakietu.

`ExcludeAssets` atrybut określa, które zasoby należące do pakietu określony przez `<PackageReference>` nie powinny być używane.

`PrivateAssets` atrybut określa, które zasoby należące do pakietu określony przez `<PackageReference>` powinny być używane, ale nie przepływać do następnego projektu. `Analyzers`, `Build` i `ContentFiles` zasoby są domyślnie prywatne, gdy ten atrybut nie jest obecny.

> [!NOTE]
> `PrivateAssets` jest odpowiednikiem *project.json*/*xproj* `SuppressParent` elementu.

Tych atrybutów może zawierać jeden lub więcej z poniższych elementów oddzielonych średnikami `;` znak, jeśli więcej niż jeden znajduje się na liście:

* `Compile` — zawartość folderu biblioteki są dostępne kompilowanie z użyciem.
* `Runtime` — zawartość folderu środowiska uruchomieniowego są dystrybuowane.
* `ContentFiles` — zawartość *contentfiles* folderu są używane.
* `Build` — właściwości/elementów docelowych, w folderze kompilacji są używane.
* `Native` — zawartość z zasobów natywnych są kopiowane do folderu wyjściowego dla środowiska uruchomieniowego.
* `Analyzers` — są używane analizatory.

Alternatywnie ten atrybut może zawierać:

* `None` — zasoby są używane.
* `All` — wszystkie zasoby są używane.

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference
Element `<DotNetCliToolReference>` elementu określa narzędzie interfejsu wiersza polecenia, które użytkownik chce przywrócić w kontekście projektu. Jest zamiennikiem `tools` w węźle *project.json*.

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a>Wersja

`Version` Określa numer wersji pakietu do przywrócenia. Ten atrybut przestrzega zasad [wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges) schematu. Domyślnym zachowaniem jest dokładna wersja dopasowania. Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji NuGet `[1.2.3]` dla 1.2.3 dokładną wersję pakietu.

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

`<RuntimeIdentifiers>` Property — element umożliwia określenie rozdzieloną średnikami listę [identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.
RID włączyć publikowanie niezależne wdrożenia.

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>RuntimeIdentifier

`<RuntimeIdentifier>` Element właściwości można określić tylko jeden [identyfikator środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu. Identyfikator RID umożliwia publikowanie niezależne wdrożenia.

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

Użyj `<RuntimeIdentifiers>` (liczba mnoga) zamiast Jeśli potrzebujesz do opublikowania dla wielu modułów wykonawczych. `<RuntimeIdentifier>` zapewnia szybsze kompilacje, gdy tylko jednego środowiska wykonawczego jest wymagana.

### <a name="packagetargetfallback"></a>PackageTargetFallback

`<PackageTargetFallback>` Element właściwości można określić zestaw zgodnych elementów docelowych do użycia podczas przywracania pakietów. Został zaprojektowany tak, aby zezwolić na pakiety, które używają dotnet [TxM (krótkiej nazwy docelowej x)](/nuget/schema/target-frameworks) do pracy z pakietami, które nie deklarują dotnet TxM. Jeśli projekt używa dotnet TxM, a następnie wszystkich pakietów to zależy od musi również mieć dotnet TxM, chyba że dodasz `<PackageTargetFallback>` do swojego projektu, aby umożliwić-dotnet platform zapewnić ich zgodność za pomocą polecenia dotnet.

W poniższym przykładzie przedstawiono przejścia dla wszystkich obiektów docelowych w projekcie:

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

W poniższym przykładzie określono planów awaryjnych tylko w przypadku `netcoreapp2.1` docelowej:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a>Właściwości metadanych NuGet

Wraz z przejściem do programu MSBuild, przenieśliśmy metadanych wejściowych, który jest używany podczas pakowania pakietów NuGet, od *project.json* do *.csproj* plików. Dane wejściowe są właściwości programu MSBuild, aby musieli przejść w ramach `<PropertyGroup>` grupy. Poniżej przedstawiono listę właściwości, które są używane jako dane wejściowe, aby proces pakowania, korzystając z `dotnet pack` polecenia lub `Pack` MSBuild docelowa to znaczy częścią zestawu SDK.

### <a name="ispackable"></a>IsPackable

Wartość logiczna określająca, czy można będzie bogatymi w projekcie. Wartość domyślna to `true`.

### <a name="packageversion"></a>PackageVersion

Określa wersję tego pakietu wynikowego. Akceptuje wszystkie formularze ciąg wersji NuGet. Wartością domyślną jest wartość z `$(Version)`, oznacza to, że właściwości `Version` w projekcie.

### <a name="packageid"></a>PackageId

Określa nazwę pakietu wynikowego. Jeśli nie zostanie określony, `pack` operacji będą domyślnie używają `AssemblyName` lub nazwę katalogu jako nazwę pakietu.

### <a name="title"></a>Tytuł

Tytuł przyjaznego dla człowieka pakietu, zwykle używanych w interfejsie użytkownika wyświetla w witrynach nuget.org i Menedżera pakietów w programie Visual Studio. Jeśli nie zostanie określony, identyfikator pakietu jest używana zamiast tego.

### <a name="authors"></a>Autorzy

Rozdzielana średnikami lista autorów pakietów, pasujące nazwy profilu w witrynie nuget.org. Te są wyświetlane w galerii pakietów NuGet w witrynie nuget.org i są odwoływania się do pakietów przez ten sam autorów.

### <a name="packagedescription"></a>PackageDescription

Długi opis pakietu do wyświetlania w interfejsie użytkownika.

### <a name="description"></a>Opis

Długi opis zestawu. Jeśli `PackageDescription` nie zostanie określony, a następnie ta właściwość jest również używany jako opis pakietu.

### <a name="copyright"></a>Prawa autorskie

Szczegóły dotyczące praw autorskich dla pakietu.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAcceptance

Wartość logiczna określająca, czy klient musi monitować konsumenta o zaakceptowanie licencji pakietu przed zainstalowaniem pakietu. Wartość domyślna to `false`.

### <a name="packagelicenseexpression"></a>PackageLicenseExpression

[Identyfikatora licencji SPDX](https://spdx.org/licenses/) lub wyrażenie. Na przykład `Apache-2.0`.

Oto Pełna lista [identyfikatory licencji SPDX](https://spdx.org/licenses/). NuGet.org akceptuje tylko OSI lub licencji FSF zatwierdzone, korzystając z licencji wyrażenie typu.

Dokładna składnia wyrażeń licencji jest opisane poniżej w [ABNF](https://tools.ietf.org/html/rfc5234).

```cli
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> Tylko jeden z `PackageLicenseExpression`, `PackageLicenseFile` i `PackageLicenseUrl` można określić jednocześnie.

### <a name="packagelicensefile"></a>PackageLicenseFile

Ścieżka do pliku licencji w ramach pakietu, jeśli używasz licencji, w której nie przypisano identyfikator SPDX lub jest ona niestandardowe licencji (przeciwnym `PackageLicenseExpression` jest preferowana)

Zastępuje `PackageLicenseUrl`, nie można połączyć z `PackageLicenseExpression` i wymaga programu Visual Studio 15.9.4, zestaw SDK platformy .NET 2.1.502 lub 2.2.101, lub nowszej.

Należy upewnić się, że plik licencji jest pakowany, jawnie dodając ją do projektu, na przykład użycia:

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a>PackageLicenseUrl

Adres URL licencji, która ma zastosowanie do pakietu. (_przestarzały począwszy od programu Visual Studio 15.9.4, zestaw SDK platformy .NET 2.1.502 i 2.2.101_)

### <a name="packageiconurl"></a>PackageIconUrl

Adres URL obrazu 64 x 64 z przezroczystym tłem do użycia jako ikona dla pakietu wyświetlania w interfejsie użytkownika.

### <a name="packagereleasenotes"></a>PackageReleaseNotes

Informacje o wersji dla pakietu.

### <a name="packagetags"></a>PackageTags

Rozdzielaną średnikami listę znaczników, który wyznacza pakietu.

### <a name="packageoutputpath"></a>PackageOutputPath

Określa ścieżkę wyjściową, w którym spakowany pakiet zostanie porzucony. Wartość domyślna to `$(OutputPath)`.

### <a name="includesymbols"></a>IncludeSymbols
Ta wartość logiczna wskazuje, czy pakiet powinien Utwórz pakiet dodatkowych symboli, gdy projekt jest pakowany. Format pakietu symboli jest kontrolowana przez `SymbolPackageFormat` właściwości.

### <a name="symbolpackageformat"></a>SymbolPackageFormat
Określa format pakietu symboli. Jeśli "symbols.nupkg" symbole starszej wersji pakietu zostanie utworzona z *. symbols.nupkg* rozszerzenia zawierającego pliki PDB, pliki dll i inne pliki wyjściowe. Jeśli "snupkg" snupkg symbol zostanie utworzony pakiet zawierający przenośnych plików PDB. Wartością domyślną jest "symbols.nupkg".

### <a name="includesource"></a>IncludeSource

Ta wartość logiczna wskazuje, czy Proces pakietu należy utworzyć pakiet "source". Źródłowy pakiet zawiera biblioteki kodu źródłowego oraz pliki PDB. Pliki źródłowe są umieszczane w `src/ProjectName` katalogu w powstałym pliku pakietu.

### <a name="istool"></a>IsTool

Określa, czy wszystkie pliki wyjściowe są kopiowane do *narzędzia* folderu zamiast *lib* folderu. Należy pamiętać, że to różni się od `DotNetCliTool` określić, ustawiając `PackageType` w *.csproj* pliku.

### <a name="repositoryurl"></a>RepositoryUrl

Określa adres URL repozytorium, gdzie znajduje się kod źródłowy dla pakietu i/lub z którego jest ona kompilowana.

### <a name="repositorytype"></a>RepositoryType

Określa typ repozytorium. Wartością domyślną jest "git".

### <a name="nopackageanalysis"></a>NoPackageAnalysis

Określa, że pakiet nie należy uruchamiać analizy pakietu po utworzeniu pakietu.

### <a name="minclientversion"></a>MinClientVersion

Określa minimalną wersję klienta NuGet, który można zainstalować ten pakiet, wymuszane przez nuget.exe oraz Menedżera pakietów programu Visual Studio.

### <a name="includebuildoutput"></a>IncludeBuildOutput

Tej wartości logicznych Określa, czy zestawy danych wyjściowych kompilacji powinien pakowane w *.nupkg* plików lub nie.

### <a name="includecontentinpack"></a>IncludeContentInPack

Ta wartość logiczna określa, czy wszystkie elementy, mają typ `Content` zostanie automatycznie dołączony do pakietu wynikowego. Wartość domyślna to `true`.

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder

Określa folder, gdzie umieścić zestawy danych wyjściowych. Zestawy danych wyjściowych (i inne pliki wyjściowe) są kopiowane do ich odpowiednich ramach folderów.

### <a name="contenttargetfolders"></a>ContentTargetFolders

Ta właściwość określa domyślną lokalizację kogo powinno zwrócić wszystkie pliki zawartości, gdy `PackagePath` nie określono dla nich. Wartość domyślna to "zawartość; pliki".

### <a name="nuspecfile"></a>NuspecFile

Względna lub bezwzględna ścieżka do *.nuspec* plików używanych na potrzeby pakowania.

> [!NOTE]
> Jeśli *.nuspec* pliku jest określona, jest on używany **wyłącznie** pakowanie informacji i wszelkie informacje zawarte w projektów nie jest używany.

### <a name="nuspecbasepath"></a>NuspecBasePath

Podstawową ścieżkę dla *.nuspec* pliku.

### <a name="nuspecproperties"></a>NuspecProperties

Rozdzielana średnikami lista klucz = wartość pary.

## <a name="assemblyinfo-properties"></a>Właściwości AssemblyInfo

[Atrybuty zestawu](../../framework/app-domains/set-assembly-attributes.md) , które były w *AssemblyInfo* pliku są teraz automatycznie generowane na podstawie właściwości.

### <a name="properties-per-attribute"></a>Właściwości dla atrybutu

Każdy atrybut ma właściwości, które sterują jej zawartość i innej, aby wyłączyć jej generacji, jak pokazano w poniższej tabeli:

| Atrybut                                                      | Właściwość               | Właściwość, która wyłącza                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

Uwagi:

* `AssemblyVersion` i `FileVersion` domyślny ma wartość `$(Version)` bez sufiksu. Na przykład jeśli `$(Version)` jest `1.2.3-beta.4`, a następnie wartość będzie wynosić `1.2.3`.
* `InformationalVersion` Wartość domyślna to wartość `$(Version)`.
* `InformationalVersion` ma `$(SourceRevisionId)` dołączona, jeśli właściwość jest obecny. Można je wyłączyć, używając `IncludeSourceRevisionInInformationalVersion`.
* `Copyright` i `Description` właściwości są używane również do metadanych NuGet.
* `Configuration` jest współużytkowany z procesu kompilacji i ustawić za pomocą `--configuration` parametru `dotnet` poleceń.

### <a name="generateassemblyinfo"></a>GenerateAssemblyInfo

Wartość logiczna, która włącza lub wyłącza Generowanie AssemblyInfo. Wartość domyślna to `true`.

### <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

Ścieżka pliku z informacjami wygenerowanego zestawu. Domyślnie plik w `$(IntermediateOutputPath)` katalogu (obj).
