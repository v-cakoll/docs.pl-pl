---
title: Dodatki do formatu csproj dla .NET Core
description: Dowiedz się więcej o różnicach między istniejącymi i net-core csproj plików
ms.date: 04/08/2019
ms.openlocfilehash: fadc6de43f522129970e48bc72914cf187fe3f82
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607709"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Dodatki do formatu csproj dla .NET Core

W tym dokumencie opisano zmiany, które zostały dodane do plików projektu w ramach przejścia z *project.json* do *csproj* i [MSBuild](https://github.com/Microsoft/MSBuild). Aby uzyskać więcej informacji na temat ogólnej składni pliku projektu i odwołania, zobacz [dokumentację pliku projektu MSBuild.](/visualstudio/msbuild/msbuild-project-file-schema-reference)

## <a name="implicit-package-references"></a>Odwołania do pakietu niejawnego

Do metapakietów niejawnie odwoływane są na podstawie `<TargetFramework>` `<TargetFrameworks>` ram docelowych określonych w pliku projektu lub ich właściwości. `<TargetFrameworks>`jest ignorowana, jeśli `<TargetFramework>` jest określona, niezależnie od kolejności. Aby uzyskać więcej informacji, zobacz [Pakiety, metapakiety i struktury](../packages.md).

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

Ponieważ `Microsoft.NETCore.App` `NETStandard.Library` lub metapakiety są niejawnie odwoływane, oto nasze zalecane najlepsze rozwiązania:

- Podczas kierowania .NET Core lub .NET Standard, nigdy `Microsoft.NETCore.App` `NETStandard.Library` nie mają jawne `<PackageReference>` odwołanie do lub metapakiety za pośrednictwem elementu w pliku projektu.
- Jeśli potrzebujesz określonej wersji środowiska wykonawczego podczas kierowania .NET Core, należy użyć `<RuntimeFrameworkVersion>` właściwości `1.0.4`w projekcie (na przykład ) zamiast odwoływać się do metapakiety.
  - Może się tak zdarzyć, jeśli używasz [samodzielnych wdrożeń](../deploying/index.md#publish-self-contained) i potrzebujesz określonej wersji poprawki środowiska wykonawczego 1.0.0 LTS, na przykład.
- Jeśli potrzebujesz określonej wersji `NETStandard.Library` metapakiety podczas kierowania .NET Standard, możesz użyć `<NetStandardImplicitPackageVersion>` właściwości i ustawić wersję, której potrzebujesz.
- Nie jawnie dodawać lub aktualizować odwołania `Microsoft.NETCore.App` `NETStandard.Library` do lub metapakiet w projektach .NET Framework. Jeśli dowolna `NETStandard.Library` wersja jest potrzebna podczas korzystania z pakietu NuGet opartego na systemie .NET Standard, nuget automatycznie instaluje tę wersję.

## <a name="implicit-version-for-some-package-references"></a>Wersja niejawna dla niektórych odwołań do pakietu

Większość użycia [`<PackageReference>`](#packagereference) wymaga ustawienia `Version` atrybutu, aby określić wersję pakietu NuGet, która ma być używana. W przypadku korzystania z platformy .NET Core 2.1 lub 2.2 i odwoływania się do [aplikacji Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) lub [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), jednak ten atrybut jest zbędny. Pakiet .NET Core SDK może automatycznie wybrać wersję tych pakietów, które powinny być używane.

### <a name="recommendation"></a>Zalecenie

Podczas odwoływania `Microsoft.AspNetCore.App` `Microsoft.AspNetCore.All` się do lub pakietów, nie należy określać ich wersji. Jeśli określono wersję, SDK może wywołać ostrzeżenie NETSDK1071. Aby rozwiązać to ostrzeżenie, usuń wersję pakietu, tak jak w poniższym przykładzie:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> Znany problem: pakiet .NET Core 2.1 SDK obsługiwał tę składnię tylko wtedy, gdy projekt używa również pliku Microsoft.NET.Sdk.Web. Ta wartość jest rozpoznawana w sdku .NET Core 2.2.

Te odwołania do ASP.NET Core metapackages mają nieco inne zachowanie od większości normalnych pakietów NuGet. [Wdrożenia zależne od struktury](../deploying/index.md#publish-runtime-dependent) aplikacji korzystających z tych metapakietów automatycznie korzystają z udostępnionej struktury ASP.NET Core. Podczas korzystania z metapakietów nie ma żadnych zasobów z pakietów Core NuGet, do których odwołuje się odwołuje się ASP.NET Core NuGet, **nie** są wdrażane z aplikacją — wspólna struktura ASP.NET Core zawiera te zasoby. Zasoby w udostępnionej ramach są zoptymalizowane pod kątem platformy docelowej, aby skrócić czas uruchamiania aplikacji. Aby uzyskać więcej informacji na temat udostępnionej struktury, zobacz [.NET Core distribution packaging](../distribution-packaging.md).

Jeśli wersja *jest* określona, jest traktowana jako *minimalna* wersja ASP.NET core udostępnionej struktury dla wdrożeń zależnych od struktury i jako *dokładna* wersja dla wdrożeń samodzielnych. Może to mieć następujące konsekwencje:

- Jeśli wersja ASP.NET Core zainstalowana na serwerze jest mniejsza niż wersja określona w PackageReference, nie można uruchomić procesu .NET Core. Aktualizacje metapakietu są często dostępne w NuGet.org przed udostępnieniem aktualizacji w środowiskach hostingowych, takich jak Azure. Aktualizowanie wersji na PackageReference do ASP.NET Core może spowodować niepowodzenie wdrożonej aplikacji.
- Jeśli aplikacja jest wdrażana jako [samodzielne wdrożenie,](../deploying/index.md#publish-self-contained)aplikacja może nie zawierać najnowszych aktualizacji zabezpieczeń do platformy .NET Core. Gdy wersja nie jest określona, SDK może automatycznie dołączyć najnowszą wersję ASP.NET Core w samodzielnym wdrożeniu.

## <a name="default-compilation-includes-in-net-core-projects"></a>Domyślna kompilacja obejmuje projekty .NET Core

Wraz z przejściem do formatu *csproj* w najnowszych wersjach SDK przenieśliśmy domyślne elementy zawiera i wyklucza dla elementów kompilacji i osadzonych zasobów do plików właściwości SDK. Oznacza to, że nie trzeba już określać tych elementów w pliku projektu.

Głównym powodem tego jest zmniejszenie bałaganu w pliku projektu. Wartości domyślne, które są obecne w SDK powinny obejmować najczęstsze przypadki użycia, więc nie ma potrzeby powtarzania ich w każdym projekcie, który tworzysz. Prowadzi to do mniejszych plików projektu, które są znacznie łatwiejsze do zrozumienia, a także edytować ręcznie, w razie potrzeby.

W poniższej tabeli przedstawiono, który element i które [globy](https://en.wikipedia.org/wiki/Glob_(programming)) są uwzględniane i wykluczane w zestawie SDK:

| Element           | Uwzględnij glob                              | Wyklucz glob                                                  | Usuń glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Skompilować           | \*\*/\*.cs (lub inne rozszerzenia języka) | \*\*/\*.user;  \*\*/\*. \*proj ;  \* \* / \*  \* \* /.vssscc \*(vssscc)  | Nie dotyczy                      |
| Zasoby wbudowaneSerekseźródło  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*. \*proj ; \* \* / \* \* \* /.vssscc \*(vssscc)     | Nie dotyczy                      |
| Brak              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*. \*proj ; \* \* / \* \* \* /.vssscc \*(vssscc)     | \*\*/\*.cs ; \* \* /.resx \*(resx)   |

> [!NOTE]
> **Wyklucz glob** zawsze `./bin` wyklucza `./obj` foldery i, które `$(BaseOutputPath)` są `$(BaseIntermediateOutputPath)` reprezentowane przez i MSBuild właściwości, odpowiednio. Jako całość wszystkie wykluczenia są `$(DefaultItemExcludes)`reprezentowane przez .

Jeśli masz globs w projekcie i spróbujesz go zbudować przy użyciu najnowszego SDK, otrzymasz następujący błąd:

> Zduplikowane elementy kompilacji zostały uwzględnione. Zestaw SDK platformy .NET domyślnie zawiera elementy kompilacji z katalogu projektu. Można usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultCompileItems" na "false", jeśli chcesz jawnie dołączyć je do pliku projektu.

Aby obejść ten błąd, można usunąć jawne `Compile` elementy, które pasują do tych wymienionych w `<EnableDefaultCompileItems>` poprzedniej `false`tabeli, lub można ustawić właściwość na , w ten sposób:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Ustawienie tej `false` właściwości spowoduje wyłączenie niejawnego włączenia, przywracając zachowanie poprzednich sdków, w których trzeba było określić domyślne globs w projekcie.

Ta zmiana nie modyfikuje głównej mechaniki innych zawiera. Jeśli jednak chcesz określić, na przykład niektóre pliki, które mają zostać opublikowane w aplikacji, nadal możesz użyć znanych `<Content>` mechanizmów w *csproj* do tego (na przykład elementu).

`<EnableDefaultCompileItems>`tylko wyłącza `Compile` globs, ale nie wpływa na `None` inne globs, jak \*niejawne glob, który dotyczy również .cs elementów. Z tego powodu **Eksplorator rozwiązań** będzie nadal wyświetlał \*elementy `None` .cs w ramach projektu, uwzględnione jako elementy. W podobny sposób można `<EnableDefaultNoneItems>` ustawić false, aby `None` wyłączyć niejawne glob, w ten sposób:

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Aby wyłączyć **wszystkie niejawne globy,** można ustawić właściwość tak `<EnableDefaultItems>` jak `false` w poniższym przykładzie:

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Jak zobaczyć cały projekt, jak msBuild widzi go

Podczas gdy te zmiany csproj znacznie upraszczają pliki projektu, możesz chcieć zobaczyć w pełni rozwinięty projekt, ponieważ MSBuild widzi go po uwzględnieniu SDK i jego obiektów docelowych. Wstępnie przetworzyć projekt z [`dotnet msbuild`](dotnet-msbuild.md) [ `/pp` przełącznikiem](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) polecenia, które pokazuje, które pliki są importowane, ich źródła i ich wkład do kompilacji bez faktycznego budowania projektu:

`dotnet msbuild -pp:fullproject.xml`

Jeśli projekt ma wiele struktur docelowych, wyniki polecenia powinny koncentrować się tylko na jednym z nich, określając go jako właściwość MSBuild:

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>Dodatki

### <a name="sdk-attribute"></a>Atrybut Sdk

Element `<Project>` główny pliku *csproj* ma nowy atrybut `Sdk`o nazwie . `Sdk`określa, który SDK będzie używany przez projekt. Zestaw SDK, jak opisano [w dokumencie warstwowym,](cli-msbuild-architecture.md) to zestaw [zadań](/visualstudio/msbuild/msbuild-tasks) i [obiektów docelowych](/visualstudio/msbuild/msbuild-targets) MSBuild, które można tworzyć kod .NET Core. Dla platformy .NET Core dostępne są następujące skomuniky SDK:

1. Core SDK .NET z identyfikatorem`Microsoft.NET.Sdk`
2. Internetowy sDK .NET Core z identyfikatorem`Microsoft.NET.Sdk.Web`
3. SDK biblioteki klas .NET Core Razor z identyfikatorem`Microsoft.NET.Sdk.Razor`
4. Podstawowa usługa robocza .NET `Microsoft.NET.Sdk.Worker` o identyfikatorze (od .NET Core 3.0)
5. .NET Core WinForms i WPF z `Microsoft.NET.Sdk.WindowsDesktop` identyfikatorem (od .NET Core 3.0)

Musisz mieć `Sdk` atrybut ustawiony na jeden z tych identyfikatorów w elemencie, `<Project>` aby użyć narzędzi .NET Core i utworzyć kod.

### <a name="packagereference"></a>Wniosek dotyczący pakietu

Element `<PackageReference>` elementu określa [zależność NuGet w projekcie](/nuget/consume-packages/package-references-in-project-files). Atrybut `Include` określa identyfikator pakietu.

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Wersja

Wymagany `Version` atrybut określa wersję pakietu do przywrócenia. Atrybut jest zgodny z regułami schematu [zakresu wersji NuGet.](/nuget/concepts/package-versioning#version-ranges) Domyślnym zachowaniem jest minimalna wersja, dopasowanie włącznie. Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji `[1.2.3, )` NuGet i oznacza, że rozwiązany pakiet będzie miał wersję 1.2.3, jeśli jest dostępna lub większa w inny sposób.

#### <a name="includeassets-excludeassets-and-privateassets"></a>Zestawy includeAssets, ExcludeAssets i PrivateAssets

`IncludeAssets`atrybut określa, które aktywa należące do `<PackageReference>` pakietu określonego przez powinny być używane. Domyślnie wszystkie zasoby pakietu są uwzględniane.

`ExcludeAssets`atrybut określa, które aktywa należące do `<PackageReference>` pakietu określonego przez nie powinny być używane.

`PrivateAssets`atrybut określa, które zasoby należące do `<PackageReference>` pakietu określonego przez powinny być używane, ale nie przepływ do następnego projektu. Zasoby `Analyzers` `Build` i `ContentFiles` zasoby są domyślnie prywatne, gdy ten atrybut nie jest obecny.

> [!NOTE]
> `PrivateAssets`jest odpowiednikiem *elementu project.json*/*xproj.* `SuppressParent`

Te atrybuty mogą zawierać jeden lub więcej z następujących `;` elementów, oddzielonych znakiem średnika, jeśli na liście znajduje się więcej niż jeden:

- `Compile`– zawartość folderu *lib* są dostępne do kompilacji przeciwko.
- `Runtime`– zawartość folderu *środowiska wykonawczego* są dystrybuowane.
- `ContentFiles`– zawartość folderu *contentfiles* są używane.
- `Build`– rekwizyty/obiekty docelowe w folderze *kompilacji* są używane.
- `Native`– zawartość zasobów natywnych są kopiowane do folderu *wyjściowego* dla środowiska wykonawczego.
- `Analyzers`– analizatory są używane.

Alternatywnie atrybut może zawierać:

- `None`– żaden z aktywów nie jest wykorzystywany.
- `All`– wykorzystuje się wszystkie aktywa.

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference (DotNetCliToolReference)

Element `<DotNetCliToolReference>` elementu określa narzędzie interfejsu wiersza polecenia, które użytkownik chce przywrócić w kontekście projektu. Jest to zamiennik węzła `tools` w *project.json*.

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

Należy `DotNetCliToolReference` zauważyć, że jest [teraz przestarzałe](https://github.com/dotnet/announcements/issues/107) na rzecz [.NET Core Local Tools](https://aka.ms/local-tools).

#### <a name="version"></a>Wersja

`Version`określa wersję pakietu do przywrócenia. Atrybut jest zgodny z regułami schematu [wersji NuGet.](/nuget/create-packages/dependency-versions#version-ranges) Domyślnym zachowaniem jest minimalna wersja, dopasowanie włącznie. Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji `[1.2.3, )` NuGet i oznacza, że rozwiązany pakiet będzie miał wersję 1.2.3, jeśli jest dostępna lub większa w inny sposób.

### <a name="runtimeidentifiers"></a>Identyfikatory środowiska uruchomieniowego

Element `<RuntimeIdentifiers>` właściwości umożliwia określenie listy identyfikatorów [czasu wykonywania (RID)](../rid-catalog.md) rozdzielanych średnikami dla projektu.
Identyfikatory RID umożliwiają publikowanie samodzielnych wdrożeń.

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>Identyfikator środowiska uruchomieniowego

Element `<RuntimeIdentifier>` właściwości umożliwia określenie tylko jednego [identyfikatora środowiska wykonawczego (RID)](../rid-catalog.md) dla projektu. Identyfikator RID umożliwia publikowanie samodzielnego wdrożenia.

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

Użyj `<RuntimeIdentifiers>` (liczba mnoga), jeśli chcesz opublikować dla wielu uruchomień. `<RuntimeIdentifier>`może zapewnić szybsze kompilacje, gdy wymagane jest tylko jedno środowisko wykonawcze.

### <a name="packagetargetfallback"></a>PackageTargetFallback

Element `<PackageTargetFallback>` właściwości umożliwia określenie zestawu zgodnych obiektów docelowych, które mają być używane podczas przywracania pakietów. Został zaprojektowany, aby umożliwić pakietom korzystającym z dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) działanie z pakietami, które nie deklarują dotnet TxM. Jeśli projekt używa dotnet TxM, a następnie wszystkie pakiety, które zależy od musi mieć `<PackageTargetFallback>` również dotnet TxM, chyba że dodać do projektu w celu umożliwienia platform innych niż dotnet być zgodne z dotnet.

Poniższy przykład zawiera rezerwy dla wszystkich obiektów docelowych w projekcie:

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

Poniższy przykład określa rezerwy tylko `netcoreapp2.1` dla obiektu docelowego:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a>Tworzenie zdarzeń

Sposób, w jaki zdarzenia pre-build i post-build są określone w pliku projektu został zmieniony. Właściwości PreBuildEvent i PostBuildEvent nie są zalecane w formacie projektu w stylu SDK, ponieważ makra, takie jak $(ProjectDir) nie są rozpoznawane. Na przykład następujący kod nie jest już obsługiwany:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

W projektach w stylu zestawu SDK użyj `PreBuild` `PostBuild` obiektu docelowego MSBuild o nazwie lub i ustaw `BeforeTargets` właściwość dla `PreBuild` obiektu . `AfterTargets` `PostBuild` W poprzednim przykładzie użyj następującego kodu:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>Można użyć dowolnej nazwy dla obiektów docelowych MSBuild, `PreBuild` `PostBuild` ale ide programu Visual Studio rozpoznaje i obiekty docelowe, dlatego zaleca się przy użyciu tych nazw, dzięki czemu można edytować polecenia w programie Visual Studio IDE.

## <a name="nuget-metadata-properties"></a>Właściwości metadanych NuGet

Wraz z przejściem do MSBuild przenieśliśmy metadane wejściowe, które są używane podczas pakowania pakietu NuGet z *pliku project.json* do *.csproj.* Dane wejściowe są MSBuild właściwości, więc `<PropertyGroup>` muszą przejść w ramach grupy. Poniżej znajduje się lista właściwości, które są używane jako dane `dotnet pack` wejściowe `Pack` do procesu pakowania podczas korzystania z polecenia lub obiektu docelowego MSBuild, który jest częścią zestawu SDK:

### <a name="ispackable"></a>IsPackable (Opakowanie)

Wartość logiczna określająca, czy projekt może być spakowany. Wartością domyślną jest `true`.

### <a name="packageversion"></a>PackageVersion

Określa wersję, którą będzie miał wynikowy pakiet. Akceptuje wszystkie formy ciągu wersji NuGet. Wartość domyślna `$(Version)`to wartość właściwości `Version` w projekcie.

### <a name="packageid"></a>PackageId

Określa nazwę pakietu wynikowego. Jeśli nie zostanie `pack` określony, operacja `AssemblyName` domyślnie będzie używać nazwy katalogu lub jako nazwy pakietu.

### <a name="title"></a>Tytuł

Tytuł pakietu przyjazny dla ludzi, zwykle używany w interfejsie użytkownika wyświetla się jako na nuget.org i Menedżer pakietów w programie Visual Studio. Jeśli nie zostanie określony, zamiast tego jest używany identyfikator pakietu.

### <a name="authors"></a>Autorzy

Oddzielona średnikami lista autorów pakietów, pasująca do nazw profili na nuget.org. Są one wyświetlane w Galerii NuGet na nuget.org i są używane do odsyłania pakietów przez tych samych autorów.

### <a name="packagedescription"></a>Scriptość pakietu

Długi opis pakietu dla wyświetlania interfejsu użytkownika.

### <a name="description"></a>Opis

Długi opis zespołu. Jeśli `PackageDescription` nie jest określony, a następnie ta właściwość jest również używany jako opis pakietu.

### <a name="copyright"></a>Prawa autorskie

Szczegóły dotyczące praw autorskich do pakietu.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAkceptance

Wartość logiczna określająca, czy klient musi monitować konsumenta o zaakceptowanie licencji pakietu przed zainstalowaniem pakietu. Wartość domyślna to `false`.

### <a name="developmentdependency"></a>RozwójZależność

Wartość logiczna, która określa, czy pakiet jest oznaczony jako zależność tylko dla deweloperów, co uniemożliwia uwzględnieniu pakietu jako zależności w innych pakietach. Z PackageReference (NuGet 4.8+), ta flaga oznacza również, że zasoby w czasie kompilacji są wykluczone z kompilacji. Aby uzyskać więcej informacji, zobacz [RozwójZależność obsługi packagereference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).

### <a name="packagelicenseexpression"></a>PackageLicenseExpression (Wysuw czekowy)

Identyfikator lub wyrażenie [licencji SPDX.](https://spdx.org/licenses/) Na przykład `Apache-2.0`.

Oto pełna lista [identyfikatorów licencji SPDX](https://spdx.org/licenses/). NuGet.org akceptuje tylko licencje zatwierdzone przez OSI lub FSF podczas korzystania z wyrażenia typu licencji.

Dokładna składnia wyrażeń licencji jest opisana poniżej w [pliku ABNF](https://tools.ietf.org/html/rfc5234).

```abnf
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
> Tylko jeden `PackageLicenseExpression` `PackageLicenseFile` z `PackageLicenseUrl` , i mogą być określone w czasie.

### <a name="packagelicensefile"></a>Plik z ciekłą dostępem do pakietu

Ścieżka do pliku licencji w pakiecie, jeśli używasz licencji, która nie została przypisana identyfikator SPDX `PackageLicenseExpression` lub jest to licencja niestandardowa (w przeciwnym razie jest preferowane)

Zastępuje `PackageLicenseUrl`, nie można połączyć z `PackageLicenseExpression`programem Visual Studio w wersji 15.9.4 i .NET SDK 2.1.502 lub 2.2.101 lub nowszym.

Należy upewnić się, że plik licencji jest spakowany, dodając go jawnie do projektu, przykład użycia:

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a>PakietLicenseUrl

Adres URL licencji, która ma zastosowanie do pakietu. (_przestarzałe od Visual Studio 15.9.4, .NET SDK 2.1.502 i 2.2.101_)

### <a name="packageiconurl"></a>PakietYkonurl

Adres URL obrazu 64x64 z przezroczystym tłem do użycia jako ikona pakietu w ekranie interfejsu użytkownika.

### <a name="packagereleasenotes"></a>PackageReleaseNotes (Opis pakietu)

Informacje o wersji pakietu.

### <a name="packagetags"></a>Znaczniki pakietów

Lista znaczników rozdzielanych średnikami, która wyznacza pakiet.

### <a name="packageoutputpath"></a>Ścieżka nakreślenia pakietu

Określa ścieżkę wyjściową, w której spakowany pakiet zostanie usunięty. Wartość domyślna to `$(OutputPath)`.

### <a name="includesymbols"></a>IncludeSymbols
Ta wartość logiczna wskazuje, czy pakiet powinien utworzyć pakiet dodatkowych symboli, gdy projekt jest spakowany. Format pakietu symboli jest kontrolowany `SymbolPackageFormat` przez właściwość.

### <a name="symbolpackageformat"></a>SymbolPackageFormat
Określa format pakietu symboli. Jeśli "symbols.nupkg", pakiet symboli starszych zostanie utworzony z rozszerzeniem *.symbols.nupkg* zawierającym pliki PDB, bibliotek dll i inne pliki wyjściowe. Jeśli "snupkg", zostanie utworzony pakiet symboli snupkg zawierający przenośne pdb. Wartość domyślna to "symbols.nupkg".

### <a name="includesource"></a>Źródło includesource

Ta wartość logiczna wskazuje, czy proces pakowania powinien utworzyć pakiet źródłowy. Pakiet źródłowy zawiera kod źródłowy biblioteki oraz pliki PDB. Pliki źródłowe są `src/ProjectName` umieszczane w katalogu w pliku pakietu wynikowego.

### <a name="istool"></a>IsTool (Niewłasce)

Określa, czy wszystkie pliki wyjściowe są kopiowane do folderu *narzędzi,* a nie do folderu *lib.* Różni się to `DotNetCliTool`od pliku csproj , który jest określony przez ustawienie `PackageType` w pliku *csproj.*

### <a name="repositoryurl"></a>RepozytoriumUrl

Określa adres URL repozytorium, w którym znajduje się kod źródłowy pakietu i/lub z którego jest on budowany.

### <a name="repositorytype"></a>Rodzaj repozytorium

Określa typ repozytorium. Wartość domyślna to "git".

### <a name="repositorybranch"></a>RepozytoriumBranch
Określa nazwę gałęzi źródłowej w repozytorium. Gdy projekt jest pakowany w pakiecie NuGet, jest dodawany do metadanych pakietu.

### <a name="repositorycommit"></a>Kompetencje repozytorium
Opcjonalne zatwierdzanie repozytorium lub zestaw zmian, aby wskazać, na którym źródle został zbudowany pakiet. `RepositoryUrl`należy również określić, aby ta właściwość została uwzględniona. Gdy projekt jest pakowany w pakiecie NuGet, to zatwierdzenie lub changeset jest dodawany do metadanych pakietu.

### <a name="nopackageanalysis"></a>NoPackageAnalysis (Analiza NoPackage)

Określa, że pakiet nie powinien uruchamiać analizy pakietu po zbudowaniu pakietu.

### <a name="minclientversion"></a>MinClientVersion (MinClientVersion)

Określa minimalną wersję klienta NuGet, który można zainstalować ten pakiet, wymuszane przez nuget.exe i Visual Studio Package Manager.

### <a name="includebuildoutput"></a>IncludeBuildOutput (Uwzględnij Nagielek)

Ta wartość logiczna określa, czy zestawy wyjściowe kompilacji powinny być pakowane do pliku *nupkg,* czy nie.

### <a name="includecontentinpack"></a>Dołącz Pakiet InPack

Ta wartość logiczna określa, czy wszystkie `Content` elementy, które mają typ, zostaną automatycznie uwzględnione w pakiecie wynikowym. Wartość domyślna to `true`.

### <a name="buildoutputtargetfolder"></a>Wykreślacz celów BuildOutput

Określa folder, w którym mają być umieszczane złoża wyjściowe. Zestawy wyjściowe (i inne pliki wyjściowe) są kopiowane do odpowiednich folderów framework.

### <a name="contenttargetfolders"></a>ContentTargetFolders (własnomie treści)

Ta właściwość określa domyślną lokalizację, gdzie wszystkie `PackagePath` pliki zawartości powinny iść, jeśli nie jest określony dla nich. Wartością domyślną jest "content;contentFiles".

### <a name="nuspecfile"></a>Plik Nuspec

Ścieżka względna lub bezwzględna do pliku *nuspec* używanego do pakowania.

> [!NOTE]
> Jeśli plik *.nuspec* jest określony, jest używany **wyłącznie** do informacji o pakowaniu, a wszelkie informacje w projektach nie są używane.

### <a name="nuspecbasepath"></a>Ścieżka Bazowa

Ścieżka podstawowa dla pliku *nuspec.*

### <a name="nuspecproperties"></a>Właściwości NuspecProperties

Lista par kluczykowych i wartości oddzielonych średnikiem.

## <a name="assemblyinfo-properties"></a>AssemblyInfo właściwości

[Atrybuty zestawu,](../../standard/assembly/set-attributes.md) które były zazwyczaj obecne w pliku *AssemblyInfo* są teraz automatycznie generowane z właściwości.

### <a name="properties-per-attribute"></a>Właściwości na atrybut

Jak pokazano w poniższej tabeli, każdy atrybut ma właściwość, która kontroluje jego zawartość i inny, który wyłącza jego generowania:

| Atrybut                                                      | Właściwość               | Właściwość, aby wyłączyć                             |
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

- `AssemblyVersion`i `FileVersion` domyślnie jest podjęcie `$(Version)` wartości bez przyrostka. Na przykład, `$(Version)` `1.2.3-beta.4`jeśli jest , `1.2.3`to wartość będzie .
- `InformationalVersion`domyślnie wartość `$(Version)`.
- `InformationalVersion`dołączona, `$(SourceRevisionId)` jeśli właściwość jest obecna. Można go wyłączyć `IncludeSourceRevisionInInformationalVersion`za pomocą programu .
- `Copyright`i `Description` właściwości są również używane dla metadanych NuGet.
- `Configuration`jest współużytkowana z całym `--configuration` procesem `dotnet` kompilacji i ustawiana za pomocą parametru poleceń.

### <a name="generateassemblyinfo"></a>Generowanie AssemblyInfo

Wartość logiczna, która włącza lub wyłącza wszystkie generowanie AssemblyInfo. Wartością domyślną jest `true`.

### <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

Ścieżka wygenerowanego pliku informacji o zestawie. Domyślnie plik w `$(IntermediateOutputPath)` katalogu (obj).
