---
title: Przenoszenie aplikacji Formularze systemu Windows do programu .NET Core
description: Uczy, jak przenieść aplikację .NET Framework Windows Forms do platformy .NET Core dla systemu Windows.
author: Thraka
ms.author: adegeo
ms.date: 01/24/2020
ms.openlocfilehash: 80b4bb225d6a6748743d91a4c70e8b09c10cc94b
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635515"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a>Jak przenieść aplikację klasyczną Windows Forms do programu .NET Core

W tym artykule opisano sposób przenoszenia aplikacji klasycznej opartej na formularzach systemu Windows z programu .NET Framework na platformę .NET Core 3.0 lub nowszą. Zestaw .NET Core 3.0 SDK zawiera obsługę aplikacji Windows Forms. Formularze systemu Windows nadal są platformą systemu Windows i są uruchamiane tylko w systemie Windows. W tym przykładzie użyto interfejsu wiersza polecenia .NET Core SDK do tworzenia projektu i zarządzania nim.

W tym artykule różne nazwy są używane do identyfikowania typów plików używanych do migracji. Podczas migracji projektu pliki zostaną nazwane inaczej, więc mentalnie dopasuj je do tych wymienionych poniżej:

| Plik | Opis |
| ---- | ----------- |
| **MyApps.sln** | Nazwa pliku rozwiązania. |
| **MyForms.csproj** | Nazwa projektu .NET Framework Windows Forms do portu. |
| **MyFormsCore.csproj** | Nazwa nowego projektu .NET Core, który tworzysz. |
| **Plik MyAppCore.exe** | Plik wykonywalny aplikacji .NET Core Windows Forms. |

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019 16.5 Wersja zapoznawcza 1](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&ch=pre&rel=16) lub nowsza dla każdej pracy projektanta, które chcesz wykonać. Zalecamy aktualizację do najnowszej [wersji preview programu Visual Studio](https://visualstudio.microsoft.com/vs/preview/)

  Zainstaluj następujące obciążenia programu Visual Studio:
  - Programowa firma .NET
  - Tworzenie aplikacji dla wielu platform w środowisku .NET Core

- Działający projekt windows forms w rozwiązaniu, które tworzy i działa bez problemu.
- Projekt zakodowany w języku C#.

> [!NOTE]
> Projekty programu .NET Core 3.0 są obsługiwane tylko w **programie Visual Studio 2019** lub nowszej wersji. Począwszy od **programu Visual Studio 2019 w wersji 16.5 Wersja zapoznawcza 1,** obsługiwany jest również projektant formularzy systemu Windows .NET Core.
>
> Aby włączyć projektanta, przejdź do pozycji Opcje **narzędzi** > **Options** > **W wersji zapoznawczej** **Environment** > i wybierz opcję Użyj **projektanta formularzy systemu Windows w wersji zapoznawczej dla aplikacji .NET Core.**

### <a name="consider"></a>Rozważyć

Podczas przenoszenia aplikacji .NET Framework Windows Forms, istnieje kilka rzeczy, które należy wziąć pod uwagę.

01. Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.

    Użyj [analizatora przenoszenia platformy .NET,](../../standard/analyzers/portability-analyzer.md) aby ustalić, czy projekt zostanie zmigrowane do platformy .NET Core 3.0. Jeśli projekt ma problemy z .NET Core 3.0, analizator pomaga zidentyfikować te problemy.

01. Używasz innej wersji formularzy systemu Windows.

    Po wydaniu programu .NET Core 3.0 Preview 1 formularze windowsowe zostały otwarte w usłudze GitHub. Kod dla .NET Core Windows Forms jest rozwidlią bazy kodu formularzy systemu Windows .NET Framework. Możliwe, że istnieją pewne różnice i aplikacja nie zostanie portowa.

01. [Pakiet zgodności systemu Windows][compat-pack] może pomóc w migracji.

    Niektóre interfejsy API, które są dostępne w .NET Framework nie są dostępne w .NET Core 3.0. [Pakiet zgodności systemu Windows][compat-pack] dodaje wiele z tych interfejsów API i może pomóc aplikacji Windows Forms w yciu w zgodności z programem .NET Core.

01. Zaktualizuj pakiety NuGet używane przez projekt.

    Zawsze jest dobrą praktyką, aby użyć najnowszych wersji pakietów NuGet przed migracją. Jeśli aplikacja odwołuje się do wszystkich pakietów NuGet, zaktualizuj je do najnowszej wersji. Upewnij się, że aplikacja tworzy pomyślnie. Po uaktualnieniu, jeśli występują błędy pakietu, przejdź do najnowszej wersji, która nie przerywa kodu.

## <a name="create-a-new-sdk-project"></a>Tworzenie nowego projektu SDK

Nowy projekt .NET Core 3.0, który tworzysz, musi znajdować się w innym katalogu niż projekt programu .NET Framework. Jeśli oba znajdują się w tym samym katalogu, można napotkać konflikty z plikami, które są generowane w katalogu **obj.** W tym przykładzie utworzymy katalog o nazwie **MyFormsAppCore** w katalogu **SolutionFolder:**

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

Następnie należy utworzyć projekt **MyFormsCore.csproj** w katalogu **MyFormsAppCore.** Plik można utworzyć ręcznie za pomocą wybranego edytora tekstu. Wklej w następującym formacie XML:

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

Jeśli nie chcesz ręcznie utworzyć pliku projektu, możesz użyć programu Visual Studio lub rdzenia SDK .NET do wygenerowania projektu. Należy jednak usunąć wszystkie inne pliki wygenerowane przez szablon projektu, z wyjątkiem pliku projektu. Aby użyć sdk, uruchom następujące polecenie z katalogu **SolutionFolder:**

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

Po utworzeniu **pliku MyFormsCore.csproj**struktura katalogu powinna wyglądać następująco:

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

Dodaj projekt **MyFormsCore.csproj** do **myapps.sln** za pomocą programu Visual Studio lub interfejsu wiersza polecenia .NET Core z katalogu **SolutionFolder:**

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a>Napraw generowanie informacji o zestawie

Projekty formularzy systemu Windows, które `AssemblyInfo.cs` zostały utworzone za pomocą programu .NET Framework zawierają plik, który zawiera atrybuty zestawu, takie jak wersja zestawu, który ma zostać wygenerowany. Projekty w stylu SDK automatycznie generują te informacje na podstawie pliku projektu SDK. Posiadanie obu typów "informacji o zestawieniu" tworzy konflikt. Rozwiąż ten problem, wyłączając automatyczne generowanie, `AssemblyInfo.cs` co wymusza użycie istniejącego pliku przez projekt.

Istnieją trzy ustawienia, aby `<PropertyGroup>` dodać do węzła głównego.

- **Generowanie AssemblyInfo**\
Po ustawieniu tej `false`właściwości na , nie wygeneruje atrybutów zestawu. Pozwala to uniknąć konfliktu `AssemblyInfo.cs` z istniejącym plikiem z projektu .NET Framework.

- **Assemblyname**\
Wartość tej właściwości jest binarny danych utworzonych podczas kompilowania. Nazwa nie wymaga dodania rozszerzenia. Na przykład `MyCoreApp` przy `MyCoreApp.exe`użyciu produkuje .

- **Rootnamespace**\
Domyślna przestrzeń nazw używana przez projekt. Powinno to odpowiadać domyślnej przestrzeni nazw projektu .NET Framework.

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

W tej chwili projekt **MyFormsCore.csproj** nie skompiluje żadnego kodu. Domyślnie projekty .NET Core automatycznie zawierają cały kod źródłowy w bieżącym katalogu i katalogach podrzędnych. Należy skonfigurować projekt, aby uwzględnić kod z projektu .NET Framework przy użyciu ścieżki względnej. Jeśli w projekcie programu .NET Framework użyto plików **.resx** dla ikon i zasobów dla formularzy, należy je również uwzględnić.

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

Najprawdopodobniej aplikacja .NET Framework Windows Forms ma plik **packages.config,** który zawiera listę wszystkich pakietów NuGet, do których odwołuje się projekt. Można spojrzeć na tej liście, aby ustalić, które pakiety NuGet dodać do projektu .NET Core. Na przykład jeśli projekt .NET Framework `MetroFramework` `MetroFramework.Design`odwołuje `MetroFramework.Fonts` się do pakietów , i NuGet, dodaj każdy do projektu za pomocą programu Visual Studio lub .NET Core CLI z katalogu **SolutionFolder:**

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

Poprzednie polecenia dodadzą następujące odwołania NuGet do projektu **MyFormsCore.csproj:**

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a>Biblioteki sterowania portami

Jeśli masz projekt biblioteki formantów systemu Windows do portu, wskazówki są takie same jak przenoszenie projektu aplikacji .NET Framework Windows Forms, z wyjątkiem kilku ustawień. I zamiast kompilować do pliku wykonywalnego, skompilować do biblioteki. Różnica między projektem wykonywalnym a projektem biblioteki, oprócz ścieżek dla plików globs, które zawierają kod źródłowy, jest minimalna.

W przykładzie poprzedniego kroku można rozwinąć projekty i pliki, z którymi pracujemy.

| Plik | Opis |
| ---- | ----------- |
| **MyApps.sln** | Nazwa pliku rozwiązania. |
| **MyControls.csproj** | Nazwa projektu .NET Framework Windows Forms Controls do portu. |
| **MyControlsCore.csproj** | Nazwa nowego projektu biblioteki .NET Core, który tworzysz. |
| **Plik MyCoreControls.dll** | Biblioteka formantów formularzy systemu .NET Core Windows Forms. |

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

Należy wziąć pod `MyControlsCore.csproj` uwagę różnice między `MyFormsCore.csproj` projektem a poprzednio utworzonym projektem.

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

Oto przykład tego, jak wyglądałby plik projektu biblioteki .NET Core Windows Forms Controls:

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

Jak widać, `<OutputType>` węzeł został usunięty, który domyślnie kompilator do tworzenia biblioteki zamiast pliku wykonywalnego. I `<AssemblyName>` `<RootNamespace>` zostały zmienione. W szczególności `<RootNamespace>` powinien odpowiadać przestrzeni nazw biblioteki formantów formularzy systemu Windows, które są porting. Na koniec `<Compile>` węzły `<EmbeddedResource>` i węzły zostały dostosowane do folderu biblioteki formantów windows, którą przenosisz.

Następnie w głównym projekcie **.NET Core MyFormsCore.csproj** dodaj odwołanie do nowej biblioteki .NET Core Windows Forms Control. Dodaj odwołanie za pomocą programu Visual Studio lub interfejsu wiersza polecenia .NET Core z katalogu **SolutionFolder:**

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

Poprzednie polecenie dodaje następujące elementy do projektu **MyFormsCore.csproj:**

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a>Problemy z kompilacją

Jeśli masz problemy z kompilowanie projektów, może być przy użyciu niektórych interfejsów API tylko dla systemu Windows, które są dostępne w programie .NET Framework, ale nie są dostępne w programie .NET Core. Możesz spróbować dodać pakiet NuGet [pakietu zgodności systemu Windows][compat-pack] do projektu. Ten pakiet działa tylko w systemie Windows i dodaje około 20 000 interfejsów API systemu Windows do projektów .NET Core i .NET Standard.

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

Poprzednie polecenie dodaje następujące elementy do projektu **MyFormsCore.csproj:**

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a>Projektant Windows Forms

Jak opisano w tym artykule, program Visual Studio 2019 obsługuje tylko Projektanta formularzy w projektach programu .NET Framework. Tworząc projekt .NET Core obok siebie, można przetestować projekt za pomocą programu .NET Core podczas projektowania formularzy za pomocą projektu programu .NET Framework. Plik rozwiązania zawiera zarówno .NET Framework i .NET Core projektów. Dodaj i zaprojektuj formularze i formanty w projekcie .NET Framework, a na podstawie wzorców glob plików dodaliśmy do projektów .NET Core, wszystkie nowe lub zmienione pliki zostaną automatycznie uwzględnione w projektach .NET Core.

Gdy program Visual Studio 2019 obsługuje projektanta formularzy systemu Windows, można skopiować/wkleić zawartość pliku projektu .NET Core do pliku projektu .NET Framework. Następnie usuń wzorce glob pliku `<Source>` `<EmbeddedResource>` dodane z i elementów. Napraw ścieżki do dowolnego odwołania do projektu używanego przez aplikację. To skutecznie uaktualnia projekt programu .NET Framework do projektu .NET Core.

## <a name="next-steps"></a>Następne kroki

- Dowiedz się więcej o [przerywaniu zmian z programu .NET Framework na platformę .NET Core](../compatibility/fx-core.md).
- Dowiedz się więcej o pakiecie [zgodności systemu Windows][compat-pack].
- Obejrzyj [klip wideo dotyczący przenoszenia](https://www.youtube.com/watch?v=upVQEUc_KwU) projektu formularzy systemu Windows framework do programu .NET Core.

[compat-pack]: windows-compat-pack.md
