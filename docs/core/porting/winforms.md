---
title: Port, Windows Forms aplikacji platformy .NET Core 3.0
description: Dowiesz się, jak przenieść aplikację .NET Framework Windows Forms do platformy .NET Core 3.0 dla Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: 0f45c053311885c779d394a97f5845119e2b5c82
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186153"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a>Instrukcje: Port aplikacji klasycznych Windows Forms, .NET Core

W tym artykule opisano, jak do portu opartego na formularzach Windows aplikacji komputerowej z .NET Framework .NET Core 3.0. Zestaw SDK programu .NET Core 3.0 obsługuje aplikacje Windows Forms. Formularze Windows jest nadal framework tylko do Windows i działa tylko w Windows. W tym przykładzie używa interfejsu wiersza polecenia platformy .NET Core SDK do tworzenia projektu i zarządzania nim.

W tym artykule różne nazwy są używane do identyfikacji typów plików używany podczas migracji. Podczas migracji projektu, pliki będą miały nazwę nadaną inaczej, dlatego umysłowo dopasować je do wymienione poniżej:

| Plik | Opis |
| ---- | ----------- |
| **MyApps.sln** | Nazwa pliku rozwiązania. |
| **MyForms.csproj** | Nazwa projektu .NET Framework Windows Forms do portu. |
| **MyFormsCore.csproj** | Nazwa nowego tworzonego projektu .NET Core. |
| **MyAppCore.exe** | Pliku wykonywalnego aplikacji .NET Core Windows Forms. |

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=winforms+core) dla wszelkie prace projektanta, co chcesz zrobić.

  Zainstaluj następujące obciążenia w programie Visual Studio:
  - Programowanie aplikacji klasycznych dla platformy .NET
  - Programowanie dla wielu platform na platformie .NET

- Praca projekt Windows Forms w rozwiązaniu, który kompiluje i uruchamia bez problemu.
- Projekt musi być kodowane w C#. 
- Zainstaluj najnowszą wersję [.NET Core 3.0](https://aka.ms/netcore3download) (wersja zapoznawcza).

>[!NOTE]
>**Program Visual Studio 2017** nie obsługuje projektów .NET Core 3.0. **Program Visual Studio 2019 r w wersji zapoznawczej/RC** obsługuje projekty .NET Core 3.0, ale nie obsługuje jeszcze wizualnego projektanta dla projektów .NET Core 3.0 Windows Forms. Aby użyć projektanta wizualnego, musi mieć projektu .NET Windows Forms w danym rozwiązaniu, który udostępnia pliki formularzy z projektem .NET Core.

### <a name="consider"></a>Należy wziąć pod uwagę

Podczas przenoszenia aplikacji .NET Framework Windows Forms, istnieje kilka rzeczy, które należy wziąć pod uwagę.

01. Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.

    Użyj [narzędzia .NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) ustalenie, jeśli projekt będzie migrować do platformy .NET Core 3.0. Jeśli projekt ma problemy z platformy .NET Core 3.0, analizator pomaga zidentyfikować te problemy.

01. Używasz innej wersji programu Windows Forms.

    Po wydaniu była .NET Core 3.0 w wersji zapoznawczej 1, Windows Forms błąd typu open source w serwisie GitHub. Kod platformy .NET Core Windows Forms jest rozwidlenie bazy kodu platformy .NET Framework Windows Forms. Istnieje możliwość, istnieją pewne różnice i aplikacja nie będzie portu.

01. [Systemie Windows Compatibility Pack] [ compat-pack] mogą pomóc w migracji.

    Niektóre interfejsy API, które są dostępne w programie .NET Framework nie są dostępne w programie .NET Core 3.0. [Systemie Windows Compatibility Pack] [ compat-pack] dodaje wiele z tych interfejsów API i może pomóc w aplikacji Windows Forms stać się zgodny z platformą .NET Core.

01. Aktualizowanie pakietów NuGet, używaną w projekcie.

    Zawsze jest dobrą praktyką jest używanie najnowszych wersji pakietów NuGet przed wykonaniem dowolnej migracji. Jeśli aplikacja odwołuje się do żadnych pakietów NuGet, aktualizację do najnowszej wersji. Upewnij się, że Twoja aplikacja pomyślnie skompilowana. Po uaktualnieniu, w przypadku błędów pakietu obniżyć wersję pakietu do najnowszej wersji, który nie przerywa działania kodu.

01. Program Visual Studio 2019 r w wersji zapoznawczej/RC programu .NET Core 3.0 nie obsługuje jeszcze Projektant formularzy

    Obecnie należy zachować istniejący plik projektu programu .NET Framework Windows Forms, jeśli chcesz użyć projektanta formularzy w programie Visual Studio.

## <a name="create-a-new-sdk-project"></a>Utwórz nowy projekt zestawu SDK

Nowe tworzonego projektu .NET Core 3.0 to musi być w innym katalogu z projektu .NET Framework. Jeśli są one w tym samym katalogu, mogą występować konflikty z plikami, które są generowane w **obj** katalogu. W tym przykładzie utworzymy katalog o nazwie **MyFormsAppCore** w **SolutionFolder** katalogu:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

Następnie należy utworzyć **MyFormsCore.csproj** projektu w **MyFormsAppCore** katalogu. Można utworzyć ten plik ręcznie przy użyciu tekstu wybranym edytorze. Wklej następujący kod XML:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

Jeśli nie chcesz ręcznie utworzyć plik projektu, można użyć programu Visual Studio lub zestawu .NET Core SDK do generowania projektu. Jednakże należy usunąć wszystkie inne pliki generowane przez szablon projektu, z wyjątkiem pliku projektu. Aby użyć zestawu SDK, uruchom następujące polecenie z **SolutionFolder** katalogu:

```cli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

Po utworzeniu **MyFormsCore.csproj**, strukturę katalogu powinien wyglądać podobnie do poniższego:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

Będziesz chciał dodać **MyFormsCore.csproj** projekt **MyApps.sln** za pomocą programu Visual Studio lub platformy .NET Core interfejsu wiersza polecenia z **SolutionFolder** katalogu:

```cli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Generowanie informacji zestawu poprawki

Obejmują projekty Windows Forms, które zostały utworzone za pomocą .NET Framework `AssemblyInfo.cs` pliku, który zawiera zestaw atrybutów, takich jak wersja zestawu do wygenerowania. Projektów w stylu zestaw SDK automatycznie generować te informacje w oparciu o plik projektu zestawu SDK. Posiadanie oba rodzaje "informacje o zestawie" spowoduje konflikt. Rozwiązać ten problem, wyłączając automatyczne generowanie, co zmusza projekt, aby używać istniejącej `AssemblyInfo.cs` pliku.

Dostępne są trzy ustawienia, aby dodać do głównego `<PropertyGroup>` węzła. 

- **GenerateAssemblyInfo**\
Po ustawieniu wartości tej właściwości na `false`, nie będzie ona Generowanie atrybutów zestawu. Pozwala to uniknąć konfliktu z istniejącym `AssemblyInfo.cs` pliku z projektem .NET Framework.

- **AssemblyName**\
Wartość tej właściwości jest wynikowy plik binarny utworzony podczas kompilowania. Nazwa nie musi rozszerzenie dodawanych do niego. Na przykład za pomocą `MyCoreApp` tworzy `MyCoreApp.exe`.

- **RootNamespace**\
Domyślna przestrzeń nazw używaną w projekcie. Powinien on odpowiadać domyślny obszar nazw projektu .NET Framework.

Te trzy elementy, aby dodać `<PropertyGroup>` w węźle `MyFormsCore.csproj` pliku:

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

Od razu **MyFormsCore.csproj** projektu nie skompilować jakiegokolwiek kodu. Domyślnie projekty .NET Core automatycznie uwzględnia całego kodu źródłowego w bieżącym katalogu i katalogi podrzędnych. Należy skonfigurować projekt, aby dołączyć kod z projektu .NET Framework za pomocą ścieżki względnej. Jeśli używany projekt .NET Framework **resx** pliki ikon i zasoby dotyczące formularzy, należy włączyć te zbyt. 

Dodaj następujący kod `<ItemGroup>` węzła do projektu. Każda instrukcja zawiera wzorzec glob pliku, która obejmuje katalogach podrzędnych.

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

Alternatywnie można utworzyć `<Compile>` lub `<EmbeddedResource>` wpis dla każdego pliku w projekcie .NET Framework.

## <a name="add-nuget-packages"></a>Dodawanie pakietów NuGet

Dodaj pakiet NuGet, każdy przywoływanego przez projekt programu .NET Framework do projektu .NET Core. 

Prawdopodobnie ma aplikacji .NET Framework Windows Forms **packages.config** pliku, który zawiera listę wszystkich pakietów NuGet, które są przywoływane przez projekt. Zapoznanie się z tą listą, aby określić, które pakiety NuGet, aby dodać do projektu .NET Core. Na przykład, jeśli projekt programu .NET Framework wywoływane `MetroFramework`, `MetroFramework.Design`, i `MetroFramework.Fonts` pakietów NuGet, Dodaj do projektu przy użyciu programu Visual Studio lub platformy .NET Core interfejsu wiersza polecenia z **SolutionFolder** katalogu :

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

Poprzednie polecenia dodać następujące odwołania NuGet do **MyFormsCore.csproj** projektu:

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a>Port bibliotek kontrolek

Jeśli masz Projekt Biblioteka kontrolek formularzy Windows Forms do portu podane są takie same jak eksportowanie projektu aplikacji platformy .NET Framework Windows Forms, z wyjątkiem kilku ustawień. I zamiast kompilacji do pliku wykonywalnego, skompiluj bibliotekę. Różnica między projekt wykonywalny i projekt biblioteki, oprócz ścieżki dla pliku elementy globalne, które zawierają kod źródłowy, jest minimalny.

Przy użyciu przykładu w poprzednim kroku, informuje o tym, jakie projektów i plików pracujemy nad.

| Plik | Opis |
| ---- | ----------- |
| **MyApps.sln** | Nazwa pliku rozwiązania. |
| **MyControls.csproj** | Nazwa projektu formantów formularzy Windows Framework .NET do portu. |
| **MyControlsCore.csproj** | Nazwa nowego projektu platformy .NET Core w bibliotece tworzenia. |
| **MyCoreControls.dll** | Biblioteka formantów formularzy programu .NET Core Windows. |

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

Należy wziąć pod uwagę różnice między `MyControlsCore.csproj` projektu oraz utworzoną wcześniej `MyFormsCore.csproj` projektu.

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

Oto przykład jak będzie wyglądać plik projektu Biblioteka formantów formularzy programu .NET Core Windows:

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

Jak widać, `<OutputType>` węzeł został usunięty, które domyślnie używa kompilator generuje bibliotekę zamiast pliku wykonywalnego. `<AssemblyName>` i `<RootNamespace>` zostały zmienione. W szczególności `<RootNamespace>` powinien być zgodny z przestrzeni nazw są przenoszenie biblioteki kontrolek formularzy Windows Forms. I wreszcie `<Compile>` i `<EmbeddedResource>` węzły zostały dostosowane by wskazywał folder Biblioteka kontrolek formularzy Windows Forms, to przenoszenie.

Następnie na główne platformy .NET Core **MyFormsCore.csproj** projektu Dodaj odwołanie do nowej biblioteki .NET Core Windows Forms kontroli. Dodaj odwołanie za pomocą programu Visual Studio lub platformy .NET Core interfejsu wiersza polecenia z **SolutionFolder** katalogu:

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

Poprzednie polecenie dodaje następujące polecenie, aby **MyFormsCore.csproj** projektu:

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a>Problemy z kompilacji

Jeśli masz problemy z kompilowanie projektów, może być używany niektóre Windows — tylko do interfejsów API, które są dostępne w programie .NET Framework, ale nie jest dostępna w .NET Core. Możesz spróbować dodać [systemie Windows Compatibility Pack] [ compat-pack] pakiet NuGet do projektu. Ten pakiet tylko działa na Windows i dodaje około 20 000 Windows interfejsów API do projektów .NET Core i .NET Standard.

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

Poprzednie polecenie dodaje następujące polecenie, aby **MyFormsCore.csproj** projektu:

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a>Projektant Windows Forms

Zgodnie z opisem w tym artykule program Visual Studio 2019 r w wersji zapoznawczej/RC obsługuje Projektant formularzy czy tylko w projektach .NET Framework. Tworząc projekt .NET Core side-by-side, można przetestować projektu na platformie .NET Core, podczas korzystania z projektu .NET Framework do projektowania formularzy. Plik rozwiązania zawiera projekty .NET Framework i .NET Core. Dodaj projekt formularzy i kontrolek w projekcie .NET Framework i wzorce glob pliku dodaliśmy do projektów .NET Core i wszelkich nowych lub zmienionych plików zostaną automatycznie uwzględnione w projektach .NET Core.

Po 2019 usługi Visual Studio obsługuje Windows Forms Designer, możesz skopiować lub wkleić zawartość pliku projektu .NET Core do pliku projektu .NET Framework. Następnie usuń wzorce glob plików, które są dodawane przy użyciu `<Source>` i `<EmbeddedResource>` elementów. Napraw ścieżki do dowolnego odwołania projektu do używanych przez aplikację. Projekt programu .NET Framework to skutecznie uaktualniania do projektu .NET Core.
 
## <a name="next-steps"></a>Następne kroki

* Przeczytaj więcej na temat [systemie Windows Compatibility Pack][compat-pack].
* Obejrzyj [wideo na przenoszenie](https://www.youtube.com/watch?v=upVQEUc_KwU) projekt formularzy Windows programu .NET Framework i .NET Core.

[compat-pack]: windows-compat-pack.md
