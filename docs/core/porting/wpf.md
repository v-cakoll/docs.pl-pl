---
title: Przenoszenie aplikacji WPF do programu .NET Core 3,0
description: Naucz się, w jaki sposób portować .NET Framework aplikację Windows Presentation Foundation do programu .NET Core 3,0 dla systemu Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 1528e578a978de38998b3f3f4b7beb72ff7422d4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117068"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a>Instrukcje: Port aplikacji klasycznej WPF do programu .NET Core

W tym artykule opisano sposób przenoszenia aplikacji klasycznej opartej na Windows Presentation Foundation (WPF) z .NET Framework do programu .NET Core 3,0. Zestaw SDK platformy .NET Core 3,0 obsługuje aplikacje WPF. WPF jest nadal strukturą tylko dla systemu Windows i działa tylko w systemie Windows. W tym przykładzie jest używany interfejs wiersza polecenia zestaw .NET Core SDK do tworzenia projektu i zarządzania nim.

W tym artykule różne nazwy są używane do identyfikowania typów plików używanych do migracji. Podczas migrowania projektu pliki będą wyglądać inaczej, dlatego można je dopasować do nich w sposób psychiczny do wymienionych poniżej:

| Plik | Opis |
| ---- | ----------- |
| **MyApps.sln** | Nazwa pliku rozwiązania. |
| **MyWPF.csproj** | Nazwa .NET Framework projektu WPF do port. |
| **MyWPFCore.csproj** | Nazwa nowego projektu .NET Core, który tworzysz. |
| **MyAppCore.exe** | Plik wykonywalny aplikacji WPF platformy .NET Core. |

>[!IMPORTANT]
>Mimo że w tym artykule C# jest stosowany język docelowy, kroki są takie same dla VB.NET, z tą różnicą, że VB.NET używa plików *. vbproj* i *. vb* zamiast plików *. csproj* i *. cs* .

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) dla wszystkich zadań, które chcesz wykonać.

  Zainstaluj następujące obciążenia programu Visual Studio:
  - Programowanie aplikacji klasycznych dla platformy .NET
  - Programowanie dla wielu platform w środowisku .NET

- Roboczy projekt WPF w rozwiązaniu, które kompiluje i uruchamia bez problemu.
- Zainstaluj najnowszą wersję zapoznawczą [programu .NET Core 3,0](https://aka.ms/netcore3download) .

>[!NOTE]
>**Program Visual Studio 2017** nie obsługuje projektów programu .net Core 3,0. **Program Visual Studio 2019** obsługuje projekty platformy .net Core 3,0, ale ma ograniczoną obsługę programu .NET Core WPF Visual Designer. Aby użyć w pełni obsługiwanego projektanta wizualnego, musisz mieć .NET Framework projekt WPF w rozwiązaniu, które udostępnia swoje pliki w projekcie .NET Core.

### <a name="consider"></a>Pod

Podczas przenoszenia aplikacji .NET Framework WPF należy wziąć pod uwagę kilka rzeczy.

01. Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.

    Użyj [analizatora przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md) , aby określić, czy projekt zostanie zmigrowany do programu .net Core 3,0. Jeśli projekt zawiera problemy z platformą .NET Core 3,0, Analizator pomaga zidentyfikować te problemy.

01. Używasz innej wersji WPF.

    Po wydaniu programu .NET Core 3,0 wersja zapoznawcza 1 program WPF otrzymał wartość Open Source w witrynie GitHub. Kod dla platformy .NET Core WPF jest rozwidleniem bazy kodu .NET Framework WPF. Istnieją pewne różnice, które nie są dostępne dla aplikacji.

01. [Pakiet zgodności systemu Windows][compat-pack] może pomóc w migracji.

    Niektóre interfejsy API, które są dostępne w .NET Framework nie są dostępne w programie .NET Core 3,0. [Pakiet zgodności systemu Windows][compat-pack] dodaje wiele z tych interfejsów API i może pomóc aplikacji WPF z platformą .NET Core.

01. Zaktualizuj pakiety NuGet używane przez Twój projekt.

    Zawsze dobrym sposobem jest użycie najnowszych wersji pakietów NuGet przed migracją. Jeśli aplikacja odwołuje się do wszystkich pakietów NuGet, zaktualizuj je do najnowszej wersji. Upewnij się, że aplikacja została pomyślnie skompilowana. Po uaktualnieniu, jeśli występują jakiekolwiek błędy pakietów, można obniżyć pakiet do najnowszej wersji, która nie powoduje przerwania kodu.

01. Program Visual Studio 2019 nie obsługuje jeszcze projektanta WPF dla platformy .NET Core 3,0

    Obecnie należy zachować istniejący plik programu .NET Framework WPF, jeśli chcesz używać projektanta WPF w programie Visual Studio.

## <a name="create-a-new-sdk-project"></a>Utwórz nowy projekt zestawu SDK

Nowy projekt platformy .NET Core 3,0, który tworzysz, musi znajdować się w innym katalogu niż projekt .NET Framework. Jeśli oba te elementy znajdują się w tym samym katalogu, może wystąpić konflikt z plikami, które są generowane w katalogu **obj** . W tym przykładzie utworzysz katalog o nazwie **MyWPFAppCore** w katalogu **SolutionFolder** :

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

Następnie należy utworzyć projekt **MyWPFCore. csproj** w katalogu **MyWPFAppCore** . Ten plik można utworzyć ręcznie przy użyciu edytora tekstu. Wklej następujący kod XML:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

Jeśli nie chcesz tworzyć pliku projektu ręcznie, możesz użyć programu Visual Studio lub zestaw .NET Core SDK do wygenerowania projektu. Należy jednak usunąć wszystkie inne pliki wygenerowane przez szablon projektu, z wyjątkiem pliku projektu. Aby użyć zestawu SDK, uruchom następujące polecenie w katalogu **SolutionFolder** :

```dotnetcli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

Po utworzeniu **MyWPFCore. csproj**struktura katalogów powinna wyglądać następująco:

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

Należy dodać projekt **MyWPFCore. csproj** do elementu **webapps. sln** z programem Visual Studio lub interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :

```dotnetcli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Napraw generowanie informacji o zestawie

Windows Presentation Foundation projekty, które zostały utworzone za pomocą .NET Framework `AssemblyInfo.cs` obejmują plik, który zawiera atrybuty zestawu, takie jak wersja zestawu do wygenerowania. Projekty w stylu zestawu SDK automatycznie generują te informacje na podstawie pliku projektu zestawu SDK. W przypadku obu typów "informacje o zestawie" powstaje konflikt. Rozwiąż ten problem, wyłączając automatyczne generowanie, co wymusza, aby projekt korzystał `AssemblyInfo.cs` z istniejącego pliku.

Istnieją trzy ustawienia do dodania do węzła głównego `<PropertyGroup>` . 

- **GenerateAssemblyInfo**\
Ustawienie tej właściwości na `false`, nie spowoduje wygenerowanie atrybutów zestawu. Pozwala to uniknąć konfliktu z istniejącym `AssemblyInfo.cs` plikiem z projektu .NET Framework.

- **AssemblyName**\
Wartością tej właściwości jest wyjściowy plik binarny tworzony podczas kompilowania. Nazwa nie wymaga dodanego rozszerzenia. Na przykład przy użyciu `MyCoreApp` polecenia `MyCoreApp.exe`Generuj.

- **RootNamespace**\
Domyślna przestrzeń nazw używana przez projekt. Powinna być zgodna z domyślną przestrzenią nazw projektu .NET Framework.

Dodaj te trzy elementy do `<PropertyGroup>` węzła `MyWPFCore.csproj` w pliku:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>MyWPF</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>Dodaj kod źródłowy
Teraz projekt **MyWPFCore. csproj** nie kompiluje żadnego kodu. Domyślnie projekty platformy .NET Core automatycznie uwzględniają cały kod źródłowy w bieżącym katalogu i wszystkich katalogach podrzędnych. Należy skonfigurować projekt do dołączania kodu z projektu .NET Framework przy użyciu ścieżki względnej. Jeśli projekt .NET Framework używał plików **resx** dla ikon i zasobów dla okien i kontrolek, należy uwzględnić te pliki. 

Pierwszy `<ItemGroup>` węzeł, który należy dodać do projektu, zawiera plik **App. XAML** , który reprezentuje konfigurację startową i zasoby używane przez aplikację. Plik **App. XAML** ma także towarzyszący plik **App.XAML.cs** , ale zostanie automatycznie dołączony do innego `<ItemGroup>`.

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

Następnie Dodaj następujący `<ItemGroup>` węzeł do projektu. Każda instrukcja zawiera wzorzec globalizowania pliku, który zawiera katalogi podrzędne. Zawiera kod źródłowy projektu, wszystkie pliki ustawień i wszystkie zasoby. Katalog **obj** jest jawnie wykluczony.

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

`<ItemGroup>` Następnie Dołącz inny `<Page>` węzeł zawierający wpis dla każdego pliku **XAML** w projekcie, z wyjątkiem pliku **App. XAML** . Zawierają one wszystkie okna, strony i zasoby, które są w formacie **XAML** . Nie można użyć w tym miejscu wzorca globalizowania i musi on dodać wpis dla każdego pliku i wskazać `<Generator>` używany.

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a>Dodaj pakiety NuGet

Dodaj każdy pakiet NuGet, do którego odwołuje się projekt .NET Framework, do projektu .NET Core. 

Prawdopodobnie aplikacja WPF .NET Framework ma plik **Packages. config** zawierający listę wszystkich pakietów NuGet, do których odwołuje się projekt. Możesz zapoznać się z tą listą, aby określić, które pakiety NuGet dodać do projektu .NET Core. Na przykład jeśli projekt .NET Framework odwołuje `MahApps.Metro` się do pakietu NuGet, Dodaj go do projektu za pomocą programu Visual Studio. Możesz również dodać odwołanie do pakietu przy użyciu interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

Poprzednie polecenie doda następujące odwołanie NuGet do projektu **MyWPFCore. csproj** :

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Problemy skompilowane

Jeśli masz problemy z kompilowaniem projektów, możesz używać niektórych interfejsów API tylko dla systemu Windows, które są dostępne w .NET Framework ale nie są dostępne w środowisku .NET Core. Możesz spróbować dodać pakiet NuGet pakietu [zgodności systemu Windows][compat-pack] do projektu. Ten pakiet działa tylko w systemie Windows i dodaje około 20 000 interfejsów API systemu Windows do projektów .NET Core i .NET Standard.

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

Poprzednie polecenie dodaje następujący do projektu **MyWPFCore. csproj** :

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a>Projektant WPF

Zgodnie z opisem w tym artykule program Visual Studio 2019 obsługuje tylko projektanta WPF w projektach .NET Framework. Tworząc równoległy projekt platformy .NET Core, można testować projekt przy użyciu platformy .NET Core podczas projektowania formularzy przy użyciu projektu .NET Framework. Plik rozwiązania zawiera zarówno projekty .NET Framework, jak i .NET Core. Dodawanie i projektowanie formularzy i kontrolek w projekcie .NET Framework i opartych na wzorcach globalizowania plików dodanych do projektów .NET Core, wszystkie nowe lub zmienione pliki zostaną automatycznie uwzględnione w projektach .NET Core.

Gdy program Visual Studio 2019 obsługuje projektanta WPF, można skopiować/wkleić zawartość pliku projektu .NET Core do pliku projektu .NET Framework. Następnie usuń pliki wzorców globalizowania dodane z `<Source>` elementami i. `<EmbeddedResource>` Popraw ścieżki do dowolnych odwołań do projektu używanych przez aplikację. Efektywnie uaktualnia projekt .NET Framework do projektu .NET Core.

## <a name="next-steps"></a>Następne kroki

- Przeczytaj więcej na temat [pakietu zgodności systemu Windows][compat-pack].
- Obejrzyj [film wideo podczas przenoszenia](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) projektu WPF .NET Framework na platformę .NET Core.

[compat-pack]: windows-compat-pack.md
