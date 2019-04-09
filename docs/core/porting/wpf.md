---
title: Port aplikacji WPF, .NET Core 3.0
description: Dowiesz się, jak przenieść aplikację .NET Framework Windows Presentation Foundation, do programu .NET Core 3.0 dla Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/27/2019
ms.custom: ''
ms.openlocfilehash: 80c55b45067405b1204cad0435b46b376f783c57
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151492"
---
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a>Instrukcje: Port aplikacji klasycznej WPF i .NET Core

W tym artykule opisano, jak do portu oparte na Windows Presentation Foundation (WPF) aplikacji komputerowej z .NET Framework .NET Core 3.0. Zestaw SDK programu .NET Core 3.0 zawiera obsługę aplikacji WPF. WPF nadal framework tylko do Windows i działa tylko w Windows. W tym przykładzie używa interfejsu wiersza polecenia platformy .NET Core SDK do tworzenia projektu i zarządzania nim.

W tym artykule różne nazwy są używane do identyfikacji typów plików używany podczas migracji. Podczas migracji projektu, pliki będą miały nazwę nadaną inaczej, dlatego umysłowo dopasować je do wymienione poniżej:

| Plik | Opis |
| ---- | ----------- |
| **MyApps.sln** | Nazwa pliku rozwiązania. |
| **MyWPF.csproj** | Nazwa projektu .NET Framework WPF do portu. |
| **MyWPFCore.csproj** | Nazwa nowego tworzonego projektu .NET Core. |
| **MyAppCore.exe** | Pliku wykonywalnego aplikacji .NET Core WPF. |

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=wpf+core) dla wszelkie prace projektanta, co chcesz zrobić.

  Zainstaluj następujące obciążenia w programie Visual Studio:
  - Programowanie aplikacji klasycznych dla platformy .NET
  - Programowanie dla wielu platform na platformie .NET

- Projekt WPF pracy w rozwiązaniu, który kompiluje i uruchamia bez problemu.
- Projekt musi być kodowane w C#. 
- Zainstaluj najnowszą wersję [.NET Core 3.0](https://aka.ms/netcore3download) (wersja zapoznawcza).

>[!NOTE]
>**Program Visual Studio 2017** nie obsługuje projektów .NET Core 3.0. **Program Visual Studio 2019 r w wersji zapoznawczej/RC** obsługuje projekty .NET Core 3.0, ale nie obsługuje jeszcze wizualnego projektanta dla projektów .NET Core 3.0 WPF. Aby użyć projektanta wizualnego, musi mieć projekt .NET WPF w danym rozwiązaniu, który udostępnia swoje pliki z projektu .NET Core.

### <a name="consider"></a>Należy wziąć pod uwagę

Podczas przenoszenia aplikacji .NET Framework WPF, istnieje kilka rzeczy, które należy wziąć pod uwagę.

01. Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.

    Użyj [narzędzia .NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) ustalenie, jeśli projekt będzie migrować do platformy .NET Core 3.0. Jeśli projekt ma problemy z platformy .NET Core 3.0, analizator pomaga zidentyfikować te problemy.

01. Używasz innej wersji programu WPF.

    W przypadku platformy .NET Core 3.0 w wersji zapoznawczej 1 został wydany, WPF błąd typu open source w serwisie GitHub. Kod platformy .NET Core WPF jest rozwidlenie bazy kodu platformy .NET Framework WPF. Istnieje możliwość, istnieją pewne różnice i aplikacja nie będzie portu.

01. [Systemie Windows Compatibility Pack] [ compat-pack] mogą pomóc w migracji.

    Niektóre interfejsy API, które są dostępne w programie .NET Framework nie są dostępne w programie .NET Core 3.0. [Systemie Windows Compatibility Pack] [ compat-pack] dodaje wiele z tych interfejsów API i może pomóc w aplikacji WPF stać się zgodny z platformą .NET Core.

01. Aktualizowanie pakietów NuGet, używaną w projekcie.

    Zawsze jest dobrą praktyką jest używanie najnowszych wersji pakietów NuGet przed wykonaniem dowolnej migracji. Jeśli aplikacja odwołuje się do żadnych pakietów NuGet, aktualizację do najnowszej wersji. Upewnij się, że Twoja aplikacja pomyślnie skompilowana. Po uaktualnieniu, w przypadku błędów pakietu obniżyć wersję pakietu do najnowszej wersji, który nie przerywa działania kodu.

01. Program Visual Studio 2019 r w wersji zapoznawczej/RC programu .NET Core 3.0 nie obsługuje jeszcze projektanta WPF

    Obecnie należy zachować istniejący plik projektu programu .NET Framework WPF, jeśli chcesz użyć projektanta WPF w programie Visual Studio.

## <a name="create-a-new-sdk-project"></a>Utwórz nowy projekt zestawu SDK

Nowe tworzonego projektu .NET Core 3.0 to musi być w innym katalogu z projektu .NET Framework. Jeśli są one w tym samym katalogu, mogą występować konflikty z plikami, które są generowane w **obj** katalogu. W tym przykładzie utworzysz katalog o nazwie **MyWPFAppCore** w **SolutionFolder** katalogu:

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

Następnie należy utworzyć **MyWPFCore.csproj** projektu w **MyWPFAppCore** katalogu. Można utworzyć ten plik ręcznie przy użyciu tekstu wybranym edytorze. Wklej następujący kod XML:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

Jeśli nie chcesz ręcznie utworzyć plik projektu, można użyć programu Visual Studio lub zestawu .NET Core SDK do generowania projektu. Jednakże należy usunąć wszystkie inne pliki generowane przez szablon projektu, z wyjątkiem pliku projektu. Aby użyć zestawu SDK, uruchom następujące polecenie z **SolutionFolder** katalogu:

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

Po utworzeniu **MyWPFCore.csproj**, strukturę katalogu powinien wyglądać podobnie do poniższego:

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

Będziesz chciał dodać **MyWPFCore.csproj** projekt **MyApps.sln** za pomocą programu Visual Studio lub platformy .NET Core interfejsu wiersza polecenia z **SolutionFolder** katalogu:

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Generowanie informacji zestawu poprawki

Projekty Windows Presentation Foundation, które zostały utworzone za pomocą .NET Framework obejmują `AssemblyInfo.cs` pliku, który zawiera zestaw atrybutów, takich jak wersja zestawu do wygenerowania. Projektów w stylu zestaw SDK automatycznie generować te informacje w oparciu o plik projektu zestawu SDK. Posiadanie oba rodzaje "informacje o zestawie" spowoduje konflikt. Rozwiązać ten problem, wyłączając automatyczne generowanie, co zmusza projekt, aby używać istniejącej `AssemblyInfo.cs` pliku.

Dostępne są trzy ustawienia, aby dodać do głównego `<PropertyGroup>` węzła. 

- **GenerateAssemblyInfo**\
Po ustawieniu wartości tej właściwości na `false`, nie będzie ona Generowanie atrybutów zestawu. Pozwala to uniknąć konfliktu z istniejącym `AssemblyInfo.cs` pliku z projektem .NET Framework.

- **AssemblyName**\
Wartość tej właściwości jest wynikowy plik binarny utworzony podczas kompilowania. Nazwa nie musi rozszerzenie dodawanych do niego. Na przykład za pomocą `MyCoreApp` tworzy `MyCoreApp.exe`.

- **RootNamespace**\
Domyślna przestrzeń nazw używaną w projekcie. Powinien on odpowiadać domyślny obszar nazw projektu .NET Framework.

Te trzy elementy, aby dodać `<PropertyGroup>` w węźle `MyWPFCore.csproj` pliku:

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

## <a name="add-source-code"></a>Dodawanie kodu źródłowego
Od razu **MyWPFCore.csproj** projektu nie skompilować jakiegokolwiek kodu. Domyślnie projekty .NET Core automatycznie uwzględnia całego kodu źródłowego w bieżącym katalogu i katalogi podrzędnych. Należy skonfigurować projekt, aby dołączyć kod z projektu .NET Framework za pomocą ścieżki względnej. Jeśli używany projekt .NET Framework **resx** pliki ikon i zasoby dla systemów windows i kontrolek, należy włączyć te zbyt. 

Pierwszy `<ItemGroup>` węzeł należy dodać do projektu **App.xaml** pliku, który reprezentuje konfiguracji uruchamiania i zasoby używany przez aplikację. **App.xaml** plik ma również towarzyszący **App.xaml.cs** plik, ale zostaną automatycznie uwzględnione w innej `<ItemGroup>`.

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

Następnie dodaj następujące `<ItemGroup>` węzła do projektu. Każda instrukcja zawiera wzorzec glob pliku, która obejmuje katalogach podrzędnych. Zawiera kod źródłowy dla projektu, wszystkie pliki ustawień i zasobów. **Obj** katalogu jest jawnie wykluczone.

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

Następnie uwzględnić innego `<ItemGroup>` węzeł, który zawiera `<Page>` wpis dla każdego **xaml** pliku w projekcie, z wyjątkiem **App.xaml** pliku. Zawierają one wszystkie systemu windows, strony i zasoby, które znajdują się w **xaml** formatu. Nie można tutaj użyć wzorca globalizowania i należy dodać wpis dla każdego pliku i wskazują `<Generator>` używane.

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a>Dodawanie pakietów NuGet

Dodaj pakiet NuGet, każdy przywoływanego przez projekt programu .NET Framework do projektu .NET Core. 

Prawdopodobnie ma aplikację .NET Framework WPF **packages.config** pliku, który zawiera listę wszystkich pakietów NuGet, które są przywoływane przez projekt. Zapoznanie się z tą listą, aby określić, które pakiety NuGet, aby dodać do projektu .NET Core. Na przykład, jeśli odwołuje się projekt programu .NET Framework `MahApps.Metro` NuGet pakietu, dodaj go do projektu przy użyciu programu Visual Studio. Możesz również dodać odwołanie do pakietu przy użyciu platformy .NET Core interfejsu wiersza polecenia z **SolutionFolder** katalogu:

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

Poprzednie polecenie dodać następujące odwołanie NuGet do **MyWPFCore.csproj** projektu:

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Problemy z kompilacji

Jeśli masz problemy z kompilowanie projektów, może być używany niektóre Windows — tylko do interfejsów API, które są dostępne w programie .NET Framework, ale nie jest dostępna w .NET Core. Możesz spróbować dodać [systemie Windows Compatibility Pack] [ compat-pack] pakiet NuGet do projektu. Ten pakiet tylko działa na Windows i dodaje około 20 000 Windows interfejsów API do projektów .NET Core i .NET Standard.

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

Poprzednie polecenie dodaje następujące polecenie, aby **MyWPFCore.csproj** projektu:

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a>Projektant WPF

Zgodnie z opisem w tym artykule program Visual Studio 2019 r w wersji zapoznawczej/RC obsługuje projektanta WPF tylko w projektach .NET Framework. Tworząc projekt .NET Core side-by-side, można przetestować projektu na platformie .NET Core, podczas korzystania z projektu .NET Framework do projektowania formularzy. Plik rozwiązania zawiera projekty .NET Framework i .NET Core. Dodaj projekt formularzy i kontrolek w projekcie .NET Framework i wzorce glob pliku dodaliśmy do projektów .NET Core i wszelkich nowych lub zmienionych plików zostaną automatycznie uwzględnione w projektach .NET Core.

Gdy program Visual Studio 2019 obsługuje projektanta WPF, można kopiujesz/wklejasz zawartość pliku projektu .NET Core do pliku projektu .NET Framework. Następnie usuń wzorce glob plików, które są dodawane przy użyciu `<Source>` i `<EmbeddedResource>` elementów. Napraw ścieżki do dowolnego odwołania projektu do używanych przez aplikację. Projekt programu .NET Framework to skutecznie uaktualniania do projektu .NET Core.
 
## <a name="next-steps"></a>Następne kroki

* Przeczytaj więcej na temat [systemie Windows Compatibility Pack][compat-pack].
* Obejrzyj [wideo na przenoszenie](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) projektu .NET Framework WPF i .NET Core.

[compat-pack]: windows-compat-pack.md
