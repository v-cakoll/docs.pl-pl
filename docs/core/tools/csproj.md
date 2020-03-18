---
title: Dodatki do formatu csproj dla .NET Core
description: Dowiedz się więcej o różnicach między istniejącymi plikami csproj firmy .NET Core
ms.date: 04/08/2019
ms.openlocfilehash: 2fb00e830380c5c4cbf7b6dcd2c8a585e1617b4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398994"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Dodatki do formatu csproj dla .NET Core

Ten dokument przedstawia zmiany, które zostały dodane do plików projektu w ramach przejścia z *project.json* do *csproj* i [MSBuild](https://github.com/Microsoft/MSBuild). Aby uzyskać więcej informacji na temat ogólnej składni pliku projektu i odwołania, zobacz [dokumentację pliku projektu MSBuild.](/visualstudio/msbuild/msbuild-project-file-schema-reference)

## <a name="implicit-package-references"></a>Niejawne odwołania do pakietów

Metapakiety są niejawnie odwołuje się na podstawie platform `<TargetFramework>` docelowych określonych w lub `<TargetFrameworks>` właściwości pliku projektu. `<TargetFrameworks>`jest ignorowana, jeśli `<TargetFramework>` jest określona, niezależnie od kolejności. Aby uzyskać więcej informacji, zobacz [Pakiety, metapakiety i struktury](../packages.md).

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

Ponieważ `Microsoft.NETCore.App` `NETStandard.Library` lub metapackages są niejawnie odwołuje się, następujące są nasze zalecane najlepsze rozwiązania:

- Podczas określania wartości docelowej .NET Core lub `Microsoft.NETCore.App` .NET Standard nigdy nie ma jawnego odwołania do lub `NETStandard.Library` metapakietów za pośrednictwem `<PackageReference>` elementu w pliku projektu.
- Jeśli potrzebujesz określonej wersji czasu wykonywania podczas określania wartości `<RuntimeFrameworkVersion>` docelowej .NET Core, `1.0.4`należy użyć właściwości w projekcie (na przykład) zamiast odwoływać się do metapakietu.
  - Może się tak zdarzyć, jeśli używasz [wdrożeń samodzielnych](../deploying/index.md#publish-self-contained) i potrzebujesz określonej wersji poprawki 1.0.0 LTS, na przykład.
- Jeśli potrzebujesz określonej wersji `NETStandard.Library` metapakietu podczas określania wartości docelowej `<NetStandardImplicitPackageVersion>` .NET Standard, możesz użyć tej właściwości i ustawić potrzebną wersję.
- Nie należy jawnie dodawać ani aktualizować odwołania do `Microsoft.NETCore.App` lub `NETStandard.Library` metapackage w projektach .NET Framework. Jeśli dowolna `NETStandard.Library` wersja jest potrzebna podczas korzystania z pakietu NuGet opartego na standardzie .NET, NuGet automatycznie instaluje tę wersję.

## <a name="implicit-version-for-some-package-references"></a>Wersja niejawna dla niektórych odwołań do pakietów

Większość użycia [`<PackageReference>`](#packagereference) wymagają ustawienie `Version` atrybutu, aby określić wersję pakietu NuGet, które mają być używane. W przypadku korzystania z .NET Core 2.1 lub 2.2 i odwoływania się [do microsoft.aspNetCore.App](/aspnet/core/fundamentals/metapackage-app) lub [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage)atrybut jest jednak niepotrzebne. Zestaw SDK .NET Core może automatycznie wybrać wersję tych pakietów, która powinna być używana.

### <a name="recommendation"></a>Zalecenie

Podczas odwoływania `Microsoft.AspNetCore.App` się `Microsoft.AspNetCore.All` do lub pakietów, nie należy określać ich wersji. Jeśli określono wersję, zestaw SDK może generować ostrzeżenie NETSDK1071. Aby rozwiązać ten problem, usuń wersję pakietu, jak w poniższym przykładzie:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> Znany problem: zestaw SDK .NET Core 2.1 obsługiwał tę składnię tylko wtedy, gdy projekt korzysta również z witryny Microsoft.NET.Sdk.Web. Rozwiązanie tego problemu zostało rozwiązane w sdku .NET Core 2.2.

Te odwołania do ASP.NET core metapackages mają nieco inne zachowanie od większości zwykłych pakietów NuGet. [Wdrożenia zależne od struktury](../deploying/index.md#publish-runtime-dependent) aplikacji korzystających z tych metapakietów automatycznie korzystają z ASP.NET podstawowej struktury udostępnionej. Korzystając z metapakietów, **żadne** zasoby z ASP.NET pakietów Core NuGet są wdrażane z aplikacją — ASP.NET framework udostępniony Core zawiera te zasoby. Zasoby w ramach udostępnionych są zoptymalizowane dla platformy docelowej, aby skrócić czas uruchamiania aplikacji. Aby uzyskać więcej informacji na temat udostępnionych ram, zobacz [.NET Core distribution packaging](../distribution-packaging.md).

Jeśli wersja *jest* określona, jest traktowana jako *minimalna* wersja ASP.NET core udostępnionej struktury dla wdrożeń zależnych od struktury i jako *dokładna* wersja dla wdrożeń samodzielnych. Może to mieć następujące konsekwencje:

- Jeśli wersja ASP.NET Core zainstalowana na serwerze jest mniejsza niż wersja określona w PackageReference, nie można uruchomić procesu .NET Core. Aktualizacje metapakietu są często dostępne na NuGet.org przed udostępnieniem aktualizacji w środowiskach hostingu, takich jak Azure. Aktualizowanie wersji w packagereference do ASP.NET Core może spowodować niepowodzenie wdrożonej aplikacji.
- Jeśli aplikacja jest wdrażana jako [samodzielne wdrożenie,](../deploying/index.md#publish-self-contained)aplikacja może nie zawierać najnowszych aktualizacji zabezpieczeń .NET Core. Jeśli wersja nie jest określona, zestaw SDK może automatycznie dołączyć najnowszą wersję ASP.NET Core do samodzielnego wdrożenia.

## <a name="default-compilation-includes-in-net-core-projects"></a>Kompilacja domyślna zawiera projekty programu .NET Core

Wraz z przejściem do formatu *csproj* w najnowszych wersjach sdk, przenieśliśmy domyślne zawiera i wyklucza dla elementów kompilacji i osadzonych zasobów do plików właściwości SDK. Oznacza to, że nie trzeba już określać tych elementów w pliku projektu.

Głównym powodem tego jest zmniejszenie bałaganu w pliku projektu. Wartości domyślne, które są obecne w kiwce SDK powinny obejmować najczęstsze przypadki użycia, więc nie ma potrzeby, aby powtórzyć je w każdym projekcie, który tworzysz. Prowadzi to do mniejszych plików projektu, które są znacznie łatwiejsze do zrozumienia, a także edytować ręcznie, w razie potrzeby.

Poniższa tabela pokazuje, który element i [które globy](https://en.wikipedia.org/wiki/Glob_(programming)) są włączone i wyłączone w zestawie SDK:

| Element           | Uwzględnij glob                              | Wykluczyć glob                                                  | Usuń glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Skompilować           | \*\*/\*.cs (lub rozszerzenia innych języków) | \*\*/\*.user;  \*\*/\*. \*proj;  \* \* / \*  \* \* /.vssscc \*(vssscc)  | Nie dotyczy                      |
| Osadzony zasób  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*. \*proj; \* \* / \* \* \* /.vssscc \*(vssscc)     | Nie dotyczy                      |
| Brak              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*. \*proj; \* \* / \* \* \* /.vssscc \*(vssscc)     | \*\*/\*.cs; \* \* /.resx \*(resx)   |

> [!NOTE]
> **Wyklucz glob** `./bin` zawsze `./obj` wyklucza i foldery, `$(BaseOutputPath)` które `$(BaseIntermediateOutputPath)` są reprezentowane przez i MSBuild właściwości, odpowiednio. Jako całość, wszystkie wykluczenia `$(DefaultItemExcludes)`są reprezentowane przez .

Jeśli masz globs w projekcie i spróbuj zbudować go przy użyciu najnowszego sdk, pojawi się następujący błąd:

> Zduplikowane elementy kompilacji zostały uwzględnione. Zestaw SDK .NET domyślnie zawiera elementy kompilacji z katalogu projektu. Można usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultCompileItems" na "false", jeśli chcesz jawnie uwzględnić je w pliku projektu.

Aby obejść ten błąd, można usunąć `Compile` elementy jawne, które pasują do elementów wymienionych w `<EnableDefaultCompileItems>` poprzedniej tabeli, lub ustawić właściwość na `false`, w ten sposób:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Ustawienie tej `false` właściwości spowoduje wyłączenie niejawnego włączenia, powracając do zachowania poprzednich zestawów SDK, w których trzeba było określić domyślne globy w projekcie.

Ta zmiana nie modyfikuje głównej mechaniki innych obejmuje. Jednak jeśli chcesz określić, na przykład, niektóre pliki, aby uzyskać opublikowane z aplikacją, nadal można użyć znanych `<Content>` mechanizmów w *csproj* do tego (na przykład element).

`<EnableDefaultCompileItems>`wyłącza tylko `Compile` globs, ale nie ma wpływu na `None` inne globs, \*jak niejawne glob, który odnosi się również do .cs elementów. Z tego powodu **Eksplorator rozwiązań** będzie nadal wyświetlał \*elementy .cs jako część projektu, uwzględnione jako `None` elementy. W podobny sposób można `<EnableDefaultNoneItems>` ustawić false, aby `None` wyłączyć niejawny glob, w podobny sposób:

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Aby wyłączyć **wszystkie niejawne globs**, można ustawić `<EnableDefaultItems>` właściwość, `false` jak w poniższym przykładzie:

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Jak zobaczyć cały projekt jako MSBuild widzi go

Podczas gdy te zmiany csproj znacznie upraszczają pliki projektu, możesz chcieć zobaczyć w pełni rozwinięty projekt, ponieważ MSBuild widzi go po uwzględnieniu sdk i jego celów. Wstępnie przetwórz projekt za [`dotnet msbuild`](dotnet-msbuild.md) pomocą [ `/pp` przełącznika](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) polecenia, które pokazuje, które pliki są importowane, ich źródła i ich wkład w budowę bez tworzenia projektu:

`dotnet msbuild -pp:fullproject.xml`

Jeśli projekt ma wiele struktur docelowych, wyniki polecenia powinny koncentrować się tylko na jednym z nich, określając go jako właściwość MSBuild:

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>Dodatki

### <a name="sdk-attribute"></a>Atrybut Sdk

Element `<Project>` główny pliku *csproj* ma nowy atrybut `Sdk`o nazwie . `Sdk`określa, który zestaw SDK będzie używany przez projekt. Zestaw SDK, jak [opisano w dokumencie warstwowym,](cli-msbuild-architecture.md) jest zestawem [zadań](/visualstudio/msbuild/msbuild-tasks) i [obiektów docelowych](/visualstudio/msbuild/msbuild-targets) MSBuild, które mogą tworzyć kod .NET Core. Dla programu .NET Core dostępne są następujące zestawy SDK:

1. Zestaw SDK .NET Core o identyfikatorze`Microsoft.NET.Sdk`
2. Internetowy zestaw SDK .NET Core o identyfikatorze`Microsoft.NET.Sdk.Web`
3. Zestaw SDK biblioteki brzytwy .NET Core z identyfikatorem`Microsoft.NET.Sdk.Razor`
4. Usługa procesu roboczego .NET Core `Microsoft.NET.Sdk.Worker` o identyfikatorze (od .NET Core 3.0)
5. .NET Core WinForms i WPF z `Microsoft.NET.Sdk.WindowsDesktop` identyfikatorem (od .NET Core 3.0)

Aby użyć narzędzi `Sdk` .NET Core i utworzyć kod, należy ustawić atrybut do `<Project>` jednego z tych identyfikatorów elementu.

### <a name="packagereference"></a>Odwołanie do pakietu

Element `<PackageReference>` określa zależność [NuGet w projekcie](/nuget/consume-packages/package-references-in-project-files). Atrybut `Include` określa identyfikator pakietu.

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Wersja

Wymagany `Version` atrybut określa wersję pakietu do przywrócenia. Atrybut jest zgodny z regułami schematu [przechowywanie wersji NuGet.](/nuget/reference/package-versioning#version-ranges-and-wildcards) Zachowanie domyślne jest minimalna wersja, dopasowanie włącznie. Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji `[1.2.3, )` NuGet i oznacza, że rozwiązany pakiet będzie miał wersję 1.2.3, jeśli jest dostępny lub większy w inny sposób.

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets, ExcludeAssets i PrivateAssets

`IncludeAssets`atrybut określa, które zasoby należące `<PackageReference>` do pakietu określone przez powinny być używane. Domyślnie wszystkie zasoby pakietu są uwzględniane.

`ExcludeAssets`atrybut określa, które zasoby należące `<PackageReference>` do pakietu określone przez nie powinny być używane.

`PrivateAssets`atrybut określa, które zasoby należące `<PackageReference>` do pakietu określone przez powinny być zużyte, ale nie przepływają do następnego projektu. Program `Analyzers` `Build` , `ContentFiles` i zasoby są domyślnie prywatne, gdy ten atrybut nie jest obecny.

> [!NOTE]
> `PrivateAssets`jest odpowiednikiem *elementu project.json*/*xproj.* `SuppressParent`

Atrybuty te mogą zawierać jeden lub więcej z następujących `;` elementów, oddzielonych znakiem średnika, jeśli na liście znajduje się więcej niż jeden:

- `Compile`– zawartość folderu *lib* są dostępne do kompilacji przeciwko.
- `Runtime`– zawartość folderu *runtime* są dystrybuowane.
- `ContentFiles`– zawartość folderu *contentfiles* są używane.
- `Build`– używane są rekwizyty/obiekty docelowe w folderze *kompilacji.*
- `Native`– zawartość z zasobów macierzystych są kopiowane do folderu *wyjściowego* dla czasu wykonywania.
- `Analyzers`– używane są analizatory.

Alternatywnie atrybut może zawierać:

- `None`– żaden z aktywów nie jest wykorzystywany.
- `All`– wszystkie aktywa są wykorzystywane.

### <a name="dotnetclitoolreference"></a>DotNetCliToolOdwołanie

Element `<DotNetCliToolReference>` określa narzędzie CLI, które użytkownik chce przywrócić w kontekście projektu. Jest to zamiennik węzła w `tools` *project.json*.

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

Należy `DotNetCliToolReference` zauważyć, że jest [teraz przestarzałe](https://github.com/dotnet/announcements/issues/107) na rzecz [.NET Core Local Tools](https://aka.ms/local-tools).

#### <a name="version"></a>Wersja

`Version`określa wersję pakietu do przywrócenia. Atrybut jest zgodny z regułami schematu [przechowywanie wersji NuGet.](/nuget/create-packages/dependency-versions#version-ranges) Zachowanie domyślne jest minimalna wersja, dopasowanie włącznie. Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji `[1.2.3, )` NuGet i oznacza, że rozwiązany pakiet będzie miał wersję 1.2.3, jeśli jest dostępny lub większy w inny sposób.

### <a name="runtimeidentifiers"></a>Identyfikatory runtimeidentifiers

Element `<RuntimeIdentifiers>` właściwości umożliwia określenie listy identyfikatorów czasu wykonywania [(RID)](../rid-catalog.md) rozdzielanych średnikami dla projektu.
IDENTYFIKATORY IDENTYFIKATORY umożliwiają publikowanie wdrożeń samodzielnych.

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>Identyfikator czasu wykonywania

Element `<RuntimeIdentifier>` właściwości umożliwia określenie tylko jednego [identyfikatora wykonywania (RID)](../rid-catalog.md) dla projektu. RID umożliwia publikowanie niezależnego wdrożenia.

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

Użyj `<RuntimeIdentifiers>` (liczba mnoga) zamiast tego, jeśli trzeba opublikować dla wielu runii. `<RuntimeIdentifier>`może zapewnić szybsze kompilacje, gdy wymagany jest tylko jeden czas wykonywania.

### <a name="packagetargetfallback"></a>PackageTargetFallback (PackageTargetFallback)

Element `<PackageTargetFallback>` właściwości umożliwia określenie zestawu zgodnych obiektów docelowych, które mają być używane podczas przywracania pakietów. Jest przeznaczony do zezwalania na pakiety, które używają dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) do pracy z pakietami, które nie deklarują dotnet TxM. Jeśli projekt używa dotnet TxM, a następnie wszystkie pakiety, od których zależy, muszą mieć `<PackageTargetFallback>` również dotnet TxM, chyba że dodasz do projektu, aby umożliwić platformy inne niż dotnet być zgodne z dotnet.

Poniższy przykład zawiera rezerwowe dla wszystkich obiektów docelowych w projekcie:

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

W poniższym przykładzie określono rezerwowe `netcoreapp2.1` tylko dla obiektu docelowego:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a>Tworzenie zdarzeń

Sposób, w jaki zdarzenia pre-build i post-build są określone w pliku projektu został zmieniony. Właściwości PreBuildEvent i PostBuildEvent nie są zalecane w formacie projektu w stylu SDK, ponieważ makra, takie jak $(ProjectDir) nie są rozpoznawane. Na przykład następujący kod nie jest już obsługiwany:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

W projektach w stylu zestawu SDK `PreBuild` `PostBuild` użyj obiektu `BeforeTargets` docelowego `PreBuild` MSBuild o nazwie lub ustaw właściwość dla lub `AfterTargets` właściwość dla `PostBuild`. W poprzednim przykładzie należy użyć następującego kodu:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>Można użyć dowolnej nazwy dla obiektów docelowych MSBuild, `PreBuild` `PostBuild` ale IDE programu Visual Studio rozpoznaje i cele, więc zaleca się przy użyciu tych nazw, dzięki czemu można edytować polecenia w programie Visual Studio IDE.

## <a name="nuget-metadata-properties"></a>NuGet właściwości metadanych

Po przejściu do MSBuild przenieśliśmy metadane wejściowe, które są używane podczas pakowania pakietu NuGet z *project.json* do plików *.csproj.* Dane wejściowe są MSBuild właściwości, więc muszą `<PropertyGroup>` przejść w grupie. Poniżej przedstawiono listę właściwości, które są używane jako dane wejściowe `dotnet pack` do procesu `Pack` pakowania podczas korzystania z polecenia lub msbuild obiektu docelowego, który jest częścią sdk:

### <a name="ispackable"></a>IsPackable (IsPackable)

Wartość logiczna, która określa, czy projekt może być spakowany. Wartością domyślną jest `true`.

### <a name="packageversion"></a>PackageVersion

Określa wersję, którą będzie miał pakiet wynikowy. Akceptuje wszystkie formy nuget ciąg wersji. Domyślnie jest `$(Version)`wartość , czyli właściwości `Version` w projekcie.

### <a name="packageid"></a>PackageId

Określa nazwę pakietu wynikowego. Jeśli nie zostanie `pack` określony, operacja będzie `AssemblyName` domyślnie przy użyciu nazwy katalogu lub jako nazwy pakietu.

### <a name="title"></a>Tytuł

Przyjazny dla człowieka tytuł pakietu, zwykle używany w monitorach interfejsu użytkownika, jak na nuget.org i Menedżera pakietów w programie Visual Studio. Jeśli nie zostanie określony, zamiast tego używany jest identyfikator pakietu.

### <a name="authors"></a>Autorzy

Oddzielona średnikami lista autorów pakietów, odpowiadająca nazwom profilów w nuget.org. Są one wyświetlane w galerii NuGet na nuget.org i są używane do pakietów odsyłaczy przez tych samych autorów.

### <a name="packagedescription"></a>Opis pakietu

Długi opis pakietu dla wyświetlania interfejsu użytkownika.

### <a name="description"></a>Opis

Długi opis złożenia. Jeśli `PackageDescription` nie zostanie określony, ta właściwość jest również używany jako opis pakietu.

### <a name="copyright"></a>Prawa autorskie

Szczegóły dotyczące praw autorskich do pakietu.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAkceptacja

Wartość logiczna określająca, czy klient musi monitować konsumenta o zaakceptowanie licencji pakietu przed zainstalowaniem pakietu. Wartość domyślna to `false`.

### <a name="developmentdependency"></a>Zależność rozwojowa

Wartość logiczna, która określa, czy pakiet jest oznaczony jako zależność tylko do rozwoju, co uniemożliwia pakiet jest uwzględniany jako zależność w innych pakietach. Z PackageReference (NuGet 4.8+), ta flaga oznacza również, że zasoby czasu kompilacji są wyłączone z kompilacji. Aby uzyskać więcej informacji, zobacz [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).

### <a name="packagelicenseexpression"></a>PackageLicenseExpression (Ekspresja license akce

Identyfikator lub wyrażenie [licencji SPDX.](https://spdx.org/licenses/) Na przykład `Apache-2.0`.

Oto pełna lista [identyfikatorów licencji SPDX](https://spdx.org/licenses/). NuGet.org akceptuje tylko licencje zatwierdzone przez OSI lub FSF podczas korzystania z wyrażenia typu licencji.

Dokładna składnia wyrażeń licencji jest opisana poniżej w [ABNF](https://tools.ietf.org/html/rfc5234).

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
> Tylko jeden `PackageLicenseExpression` `PackageLicenseFile` z `PackageLicenseUrl` , i może być określony w czasie.

### <a name="packagelicensefile"></a>Plik LicenseFile packagelicense

Ścieżka do pliku licencji w pakiecie, jeśli używasz licencji, której nie przypisano identyfikatora SPDX `PackageLicenseExpression` lub jest to licencja niestandardowa (w przeciwnym razie jest preferowana)

Zastępuje `PackageLicenseUrl`, nie można łączyć `PackageLicenseExpression`z , i wymaga programu Visual Studio w wersji 15.9.4 i .NET SDK 2.1.502 lub 2.2.101 lub nowsze.

Należy upewnić się, że plik licencji jest spakowany przez dodanie go jawnie do projektu, przykład użycia:

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a>PackageLicenseUrl

Adres URL licencji, który ma zastosowanie do pakietu. (_przestarzałe od programu Visual Studio 15.9.4, .NET SDK 2.1.502 i 2.2.101_)

### <a name="packageiconurl"></a>PackageIconUrl

Adres URL obrazu 64x64 z przezroczystym tłem do użycia jako ikony pakietu w wyświetlaczu interfejsu użytkownika.

### <a name="packagereleasenotes"></a>PackageReleaseNotes (Informacje o wydaniu pakietów)

Zwolnij uwagi dotyczące pakietu.

### <a name="packagetags"></a>Tagi pakietów

Rozdzielona średnikami lista znaczników wyznaczania pakietu.

### <a name="packageoutputpath"></a>PackageOutputPath (PackageOutputPath)

Określa ścieżkę danych wyjściowych, w której pakiet zostanie usunięty. Wartość domyślna to `$(OutputPath)`.

### <a name="includesymbols"></a>Symbole includesymbole
Ta wartość logiczna wskazuje, czy pakiet powinien utworzyć pakiet dodatkowych symboli, gdy projekt jest pakowany. Format pakietu symboli jest kontrolowany przez `SymbolPackageFormat` właściwość.

### <a name="symbolpackageformat"></a>SymbolPackageFormat
Określa format pakietu symboli. Jeśli "symbols.nupkg", zostanie utworzony starszy pakiet symboli z rozszerzeniem *.symbols.nupkg* zawierającym pliki PDB, Biblioteki DLL i inne pliki wyjściowe. Jeśli "snupkg", zostanie utworzony pakiet symbolu snupkg zawierający przenośne pdb. Domyślnie jest to "symbols.nupkg".

### <a name="includesource"></a>Źródło include

Ta wartość logiczna wskazuje, czy proces pakowania powinien utworzyć pakiet źródłowy. Pakiet źródłowy zawiera kod źródłowy biblioteki, a także pliki PDB. Pliki źródłowe są `src/ProjectName` umieszczane w katalogu w wynikowym pliku pakietu.

### <a name="istool"></a>Istool (Narzędzie IsTool)

Określa, czy wszystkie pliki wyjściowe są kopiowane do folderu *narzędzi* zamiast do folderu *lib.* Różni się `DotNetCliTool`to od , który jest `PackageType` określony przez ustawienie w pliku *csproj.*

### <a name="repositoryurl"></a>Adres repositoryurl

Określa adres URL repozytorium, w którym znajduje się kod źródłowy pakietu i/lub z którego jest on budowany.

### <a name="repositorytype"></a>Typ repozytorium

Określa typ repozytorium. Domyślnie jest "git".

### <a name="repositorybranch"></a>Oddział repozytorium
Określa nazwę gałęzi źródłowej w repozytorium. Gdy projekt jest pakowany w pakiecie NuGet, jest dodawany do metadanych pakietu.

### <a name="repositorycommit"></a>RepositoryCommit
Opcjonalne zatwierdzanie repozytorium lub zestaw zmian, aby wskazać, które źródło pakiet został zbudowany przeciwko. `RepositoryUrl`należy również określić, aby ta właściwość została uwzględniona. Gdy projekt jest spakowany w pakiecie NuGet, to zatwierdzenie lub zestaw zmian jest dodawany do metadanych pakietu.

### <a name="nopackageanalysis"></a>NoPackageAnalysis (Analiza bez pakietu)

Określa, że pakiet nie powinien uruchamiać analizy pakietu po utworzeniu pakietu.

### <a name="minclientversion"></a>MinClientVersion (Wersja MinClientVersion)

Określa minimalną wersję klienta NuGet, który można zainstalować ten pakiet, wymuszane przez nuget.exe i Visual Studio Package Manager.

### <a name="includebuildoutput"></a>IncludeBuildWyjście

Ta wartość logiczna określa, czy zestawy wyjściowe kompilacji powinny być pakowane do pliku *.nupkg,* czy nie.

### <a name="includecontentinpack"></a>Pakiet includecontentinpack

Ta wartość logiczna określa, czy wszystkie `Content` elementy, które mają typ zostaną uwzględnione w pakiecie wynikowym automatycznie. Wartość domyślna to `true`.

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder (Folder docelowy danych wyjściowych kompilacji)

Określa folder, w którym mają być umieszczane zestawy wyjściowe. Zestawy wyjściowe (i inne pliki wyjściowe) są kopiowane do odpowiednich folderów framework.

### <a name="contenttargetfolders"></a>Foldery ContentTargetfolders

Ta właściwość określa domyślną lokalizację, gdzie wszystkie `PackagePath` pliki zawartości powinny iść, jeśli nie jest określony dla nich. Wartością domyślną jest "content;contentFiles".

### <a name="nuspecfile"></a>Plik NuspecFile

Ścieżka względna lub bezwzględna do pliku *nuspec* używanego do pakowania.

> [!NOTE]
> Jeśli plik *nuspec* jest określony, jest używany **wyłącznie** do pakowania informacji i wszelkie informacje w projektach nie jest używany.

### <a name="nuspecbasepath"></a>Ścieżka NuspecBasePath

Ścieżka podstawowa dla pliku *nuspec.*

### <a name="nuspecproperties"></a>Właściwości NuspecProperties

Dwuśrednik oddzielona lista par klucz=wartość.

## <a name="assemblyinfo-properties"></a>Właściwości AssemblyInfo

[Atrybuty zestawu,](../../standard/assembly/set-attributes.md) które były zwykle obecne w pliku *AssemblyInfo* są teraz automatycznie generowane z właściwości.

### <a name="properties-per-attribute"></a>Właściwości na atrybut

Jak pokazano w poniższej tabeli, każdy atrybut ma właściwość, która kontroluje jego zawartość, a inny, który wyłącza jego generacji:

| Atrybut                                                      | Właściwość               | Właściwość do wyłączenia                             |
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

- `AssemblyVersion`i `FileVersion` domyślnie jest podjęcie `$(Version)` wartości bez sufiksu. Na przykład, `$(Version)` `1.2.3-beta.4`jeśli jest , `1.2.3`a następnie wartość będzie .
- `InformationalVersion`domyślnie wartość . `$(Version)`
- `InformationalVersion`został `$(SourceRevisionId)` dołączony, jeśli nieruchomość jest obecna. Można go wyłączyć `IncludeSourceRevisionInInformationalVersion`za pomocą .
- `Copyright`i `Description` właściwości są również używane dla metadanych NuGet.
- `Configuration`jest współużytkowany przez cały proces `--configuration` kompilacji i ustawiany za pomocą parametru `dotnet` poleceń.

### <a name="generateassemblyinfo"></a>Generuj informacje o zestawie

Wartość logiczna, która włącza lub wyłącza wszystkie generowanie AssemblyInfo. Wartością domyślną jest `true`.

### <a name="generatedassemblyinfofile"></a>Wygenerowanyplik InfoAssembly

Ścieżka wygenerowanego pliku informacji o zestawie. Domyślnie plik w `$(IntermediateOutputPath)` katalogu (obj).
