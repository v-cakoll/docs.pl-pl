---
title: Przenoszenie aplikacji formularzy systemu Windows do usługi .NET Core
description: Naucza, jak przenieść aplikację .NET Framework Windows Forms do .NET Core dla systemu Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.openlocfilehash: dbd522851faa0a4fe435199914a034ee230d3455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116024"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a>Jak przenieść aplikację klasyczną Windows Forms do programu .NET Core

W tym artykule opisano sposób przenoszenia aplikacji klasycznej opartej na formularzach Systemu Windows z platformy .NET Framework do programu .NET Core 3.0 lub nowszej. Zestaw SDK .NET Core 3.0 zawiera obsługę aplikacji windows forms. Formularze systemu Windows są nadal strukturą tylko dla systemu Windows i są uruchamiane tylko w systemie Windows. W tym przykładzie użyto cli sdk.NET Core do tworzenia projektu i zarządzania nim.

W tym artykule różne nazwy są używane do identyfikowania typów plików używanych do migracji. Podczas migracji projektu pliki będą nazywane inaczej, więc psychicznie dopasować je do wymienionych poniżej:

| Plik | Opis |
| ---- | ----------- |
| **Aplikacja MyApps.sln** | Nazwa pliku rozwiązania. |
| **MyForms.csproj** | Nazwa projektu formularzy systemu Windows .NET Framework do portu. |
| **MyFormsCore.csproj** | Nazwa nowego tworzonego projektu .NET Core. |
| **MójAppCore.exe** | Plik wykonywalny aplikacji .NET Core Windows Forms. |

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) dla każdej pracy projektanta, którą chcesz wykonać.

  Zainstaluj następujące obciążenia programu Visual Studio:
  - Tworzenie komputerów stacjonarnych .NET
  - Tworzenie aplikacji dla wielu platform w środowisku .NET Core

- Działający projekt formularzy systemu Windows w rozwiązaniu, które tworzy i działa bez problemu.
- Projekt zakodowany w języku C#.
- [.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3.0 lub nowszym.

> [!NOTE]
> **Program Visual Studio 2017** nie obsługuje projektów programu .NET Core 3.0. **Program Visual Studio 2019** obsługuje projekty programu .NET Core 3.0, ale nie obsługuje jeszcze projektanta wizualnego dla projektów .NET Core 3.0 Windows Forms. Aby użyć projektanta wizualnego, musisz mieć projekt .NET Windows Forms w rozwiązaniu, które udostępnia pliki formularzy z projektem .NET Core.

### <a name="consider"></a>Rozważyć

Podczas przenoszenia aplikacji formularzy systemu Windows .NET Framework należy wziąć pod uwagę kilka rzeczy.

01. Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.

    Użyj [analizatora przenośności .NET,](../../standard/analyzers/portability-analyzer.md) aby określić, czy projekt zostanie migrowany do .NET Core 3.0. Jeśli projekt ma problemy z .NET Core 3.0, analizator pomaga zidentyfikować te problemy.

01. Używasz innej wersji formularzy systemu Windows.

    Po wydaniu programu .NET Core 3.0 Preview 1 formularze systemu Windows zostały udostępnione w usylotach open source w usteercie GitHub. Kod .NET Core Windows Forms jest rozwidlenie .NET Framework Windows Forms codebase. Możliwe, że istnieją pewne różnice, a aplikacja nie będzie portować.

01. [Pakiet zgodności systemu Windows][compat-pack] może pomóc w migracji.

    Niektóre interfejsy API, które są dostępne w platformie .NET Framework nie są dostępne w .NET Core 3.0. [Pakiet zgodności systemu Windows][compat-pack] dodaje wiele z tych interfejsów API i może pomóc aplikacji Windows Forms stać się zgodna z .NET Core.

01. Zaktualizuj pakiety NuGet używane przez projekt.

    Zawsze jest dobrą praktyką, aby używać najnowszych wersji pakietów NuGet przed migracją. Jeśli aplikacja odwołuje się do żadnych pakietów NuGet, zaktualizuj je do najnowszej wersji. Upewnij się, że aplikacja tworzy pomyślnie. Po uaktualnieniu, jeśli występują błędy pakietu, obniżyć pakiet do najnowszej wersji, która nie łamie kodu.

01. Program Visual Studio 2019 nie obsługuje jeszcze projektanta formularzy dla .NET Core 3.0

    Obecnie należy zachować istniejący plik projektu formularzy systemu .NET Framework Windows, jeśli chcesz użyć Projektanta formularzy z programu Visual Studio.

## <a name="create-a-new-sdk-project"></a>Tworzenie nowego projektu SDK

Utworzony nowy projekt .NET Core 3.0 musi znajdować się w innym katalogu niż projekt .NET Framework. Jeśli oba znajdują się w tym samym katalogu, możesz napotkać konflikty z plikami, które są generowane w katalogu **obj.** W tym przykładzie utworzymy katalog o nazwie **MyFormsAppCore** w katalogu **SolutionFolder:**

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

Następnie musisz utworzyć projekt **MyFormsCore.csproj** w katalogu **MyFormsAppCore.** Można utworzyć ten plik ręcznie za pomocą edytora tekstu z wyboru. Wklej w następującym xml:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

Jeśli nie chcesz ręcznie tworzyć pliku projektu, możesz użyć programu Visual Studio lub sdk .NET Core do wygenerowania projektu. Należy jednak usunąć wszystkie inne pliki wygenerowane przez szablon projektu z wyjątkiem pliku projektu. Aby użyć sdk, uruchom następujące polecenie z katalogu **SolutionFolder:**

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

Po utworzeniu **MyFormsCore.csproj**struktura katalogów powinna wyglądać następująco:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

Dodaj projekt **MyFormsCore.csproj** do **pliku MyApps.sln** za pomocą programu Visual Studio lub kontrolera CLI programu .NET Core z katalogu **SolutionFolder:**

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Napraw generowanie informacji o montażu

Projekty formularzy systemu Windows, które zostały `AssemblyInfo.cs` utworzone za pomocą programu .NET Framework, zawierają plik zawierający atrybuty zestawu, takie jak wersja zestawu, który ma zostać wygenerowany. Projekty w stylu SDK automatycznie generują te informacje na podstawie pliku projektu SDK. Posiadanie obu typów "informacji o zestawie" tworzy konflikt. Rozwiąż ten problem, wyłączając automatyczne generowanie, co `AssemblyInfo.cs` wymusza, aby projekt używał istniejącego pliku.

Istnieją trzy ustawienia, które `<PropertyGroup>` należy dodać do węzła głównego.

- **Generuj informacje o zestawie**\
Po ustawieniu tej `false`właściwości , nie będzie generować atrybuty zestawu. Pozwala to uniknąć konfliktu `AssemblyInfo.cs` z istniejącym plikiem z projektu .NET Framework.

- **Assemblyname**\
Wartość tej właściwości jest wyjściowym binarnym utworzonym podczas kompilowania. Nazwa nie wymaga rozszerzenia dodane do niego. Na przykład `MyCoreApp` przy `MyCoreApp.exe`użyciu produkuje .

- **Rootnamespace**\
Domyślny obszar nazw używany przez projekt. Powinno to być zgodne z domyślnym obszarem nazw projektu .NET Framework.

Dodaj te trzy `<PropertyGroup>` elementy do `MyFormsCore.csproj` węzła w pliku:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>WindowsFormsApp1</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a>Dodawanie kodu źródłowego

W tej chwili projekt **MyFormsCore.csproj** nie skompilował żadnego kodu. Domyślnie projekty programu .NET Core automatycznie zawierają cały kod źródłowy w bieżącym katalogu i wszystkie katalogi podrzędne. Należy skonfigurować projekt, aby uwzględnić kod z projektu .NET Framework przy użyciu ścieżki względnej. Jeśli w projekcie .NET Framework użyto plików **.resx** dla ikon i zasobów dla formularzy, należy je również uwzględnić.

Dodaj następujący `<ItemGroup>` węzeł do projektu. Każda instrukcja zawiera wzorzec glob pliku, który zawiera katalogi podrzędne.

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

Alternatywnie można utworzyć `<Compile>` lub `<EmbeddedResource>` wpis dla każdego pliku w projekcie .NET Framework.

## <a name="add-nuget-packages"></a>Dodawanie pakietów NuGet

Dodaj każdy pakiet NuGet, do którego odwołuje się projekt .NET Framework, do projektu .NET Core.

Najprawdopodobniej aplikacja .NET Framework Windows Forms ma plik **packages.config,** który zawiera listę wszystkich pakietów NuGet, do których odwołuje się projekt. Możesz spojrzeć na tej liście, aby określić, które pakiety NuGet, aby dodać do projektu .NET Core. Na przykład jeśli projekt .NET Framework `MetroFramework` `MetroFramework.Design`odwołuje `MetroFramework.Fonts` się do pakietów , i NuGet, dodaj każdy z nich do projektu za pomocą programu Visual Studio lub kontrolera CLI .NET Core z katalogu **SolutionFolder:**

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

Poprzednie polecenia dodają następujące odwołania NuGet do projektu **MyFormsCore.csproj:**

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a>Biblioteki sterowania portem

Jeśli masz projekt biblioteki formantów formularzy systemu Windows do portu, wskazówki są takie same jak przenoszenie projektu aplikacji formularzy .NET Framework Windows Forms, z wyjątkiem kilku ustawień. I zamiast kompilować do pliku wykonywalnego, można skompilować do biblioteki. Różnica między projektem wykonywalnym a projektem biblioteki, oprócz ścieżek dla globs plików, które zawierają kod źródłowy, jest minimalna.

Korzystając z przykładu poprzedniego kroku, pozwala rozwinąć projekty i pliki, z którymi pracujemy.

| Plik | Opis |
| ---- | ----------- |
| **Aplikacja MyApps.sln** | Nazwa pliku rozwiązania. |
| **MyControls.csproj** | Nazwa .NET Framework Windows Forms Controls projektu do portu. |
| **MyControlsCore.csproj** | Nazwa nowego tworzonego projektu biblioteki .NET Core. |
| **Plik MyCoreControls.dll** | Biblioteka formantów formularzy systemu .NET Core Windows. |

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
├───MyFormsAppCore
│   └───MyFormsCore.csproj
│
├───MyFormsControls
│   └───MyControls.csproj
└───MyFormsControlsCore
    └───MyControlsCore.csproj   <--- New project for core controls
```

Należy wziąć pod `MyControlsCore.csproj` uwagę różnice między `MyFormsCore.csproj` projektem a wcześniej utworzonym projektem.

```diff
 <Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

   <PropertyGroup>
-    <OutputType>WinExe</OutputType>
     <TargetFramework>netcoreapp3.0</TargetFramework>
     <UseWindowsForms>true</UseWindowsForms>

     <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
-    <AssemblyName>MyCoreApp</AssemblyName>
-    <RootNamespace>WindowsFormsApp1</RootNamespace>
+    <AssemblyName>MyControlsCore</AssemblyName>
+    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
   </PropertyGroup>

   <ItemGroup>
-    <Compile Include="..\MyFormsApp\**\*.cs" />
-    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
+    <Compile Include="..\MyFormsControls\**\*.cs" />
+    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
   </ItemGroup>

 </Project>
```

Oto przykład tego, jak wyglądałby plik projektu biblioteki formantów formularzy systemu .NET Core Windows:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>

    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreControls</AssemblyName>
    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
  </PropertyGroup>

  <ItemGroup>
    <Compile Include="..\MyFormsControls\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
  </ItemGroup>

</Project>
```

Jak `<OutputType>` widać, węzeł został usunięty, co domyślnie kompilator do produkcji biblioteki zamiast pliku wykonywalnego. I `<AssemblyName>` `<RootNamespace>` zostały zmienione. W szczególności `<RootNamespace>` powinien odpowiadać przestrzeni nazw biblioteki formantów formularzy systemu Windows, które są przenoszeni. I na `<Compile>` koniec `<EmbeddedResource>` węzły i węzły zostały dostosowane do folderu w portingowej bibliotece Formanty formularzy systemu Windows.

Następnie w głównym projekcie **.NET Core MyFormsCore.csproj** dodaj odwołanie do nowej biblioteki kontroli formularzy systemu .NET Core systemu Windows. Dodaj odwołanie do programu Visual Studio lub kontrolera CLI programu .NET Core z katalogu **SolutionFolder:**

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

Poprzednie polecenie dodaje następujące do **projektu MyFormsCore.csproj:**

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a>Problemy z kompilacją

Jeśli masz problemy ze kompilowaniem projektów, być może używasz niektórych interfejsów API tylko dla systemu Windows, które są dostępne w programie .NET Framework, ale nie są dostępne w programie .NET Core. Możesz spróbować dodać pakiet [NuGet pakietu zgodności systemu Windows][compat-pack] do projektu. Ten pakiet działa tylko w systemie Windows i dodaje około 20 000 interfejsów API systemu Windows do projektów .NET Core i .NET Standard.

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

Poprzednie polecenie dodaje następujące do **projektu MyFormsCore.csproj:**

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a>Projektant Windows Forms

Jak opisano w tym artykule program Visual Studio 2019 obsługuje tylko projektanta formularzy w projektach .NET Framework. Tworząc projekt .NET Core obok siebie, można przetestować projekt za pomocą programu .NET Core podczas projektowania formularzy za pomocą projektu .NET Framework. Plik rozwiązania zawiera zarówno projekty .NET Framework, jak i .NET Core. Dodawanie i projektowanie formularzy i formantów w projekcie .NET Framework oraz na podstawie wzorców glob plików dodanych do projektów .NET Core, wszystkie nowe lub zmienione pliki zostaną automatycznie uwzględnione w projektach .NET Core.

Po programie Visual Studio 2019 obsługuje Windows Forms Designer, można skopiować/wkleić zawartość pliku projektu .NET Core do pliku projektu .NET Framework. Następnie usuń wzorce glob `<Source>` pliku `<EmbeddedResource>` dodane z elementami i. Napraw ścieżki do dowolnego odwołania do projektu używanego przez aplikację. To skutecznie uaktualnia projekt .NET Framework do projektu .NET Core.

## <a name="next-steps"></a>Następne kroki

- Dowiedz się więcej o [wprowadzaniu zmian z programu .NET Framework do programu .NET Core](../compatibility/fx-core.md).
- Dowiedz się więcej o [pakiecie zgodności systemu Windows][compat-pack].
- Obejrzyj [klip wideo dotyczący przenoszenia](https://www.youtube.com/watch?v=upVQEUc_KwU) projektu formularzy systemu Windows programu .NET Framework do programu .NET Core.

[compat-pack]: windows-compat-pack.md
