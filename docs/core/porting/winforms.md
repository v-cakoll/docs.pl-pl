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
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="aed91-103">Jak przenieść aplikację klasyczną Windows Forms do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="aed91-103">How to port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="aed91-104">W tym artykule opisano sposób przenoszenia aplikacji klasycznej opartej na formularzach systemu Windows z programu .NET Framework na platformę .NET Core 3.0 lub nowszą.</span><span class="sxs-lookup"><span data-stu-id="aed91-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0 or later.</span></span> <span data-ttu-id="aed91-105">Zestaw .NET Core 3.0 SDK zawiera obsługę aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="aed91-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="aed91-106">Formularze systemu Windows nadal są platformą systemu Windows i są uruchamiane tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="aed91-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="aed91-107">W tym przykładzie użyto interfejsu wiersza polecenia .NET Core SDK do tworzenia projektu i zarządzania nim.</span><span class="sxs-lookup"><span data-stu-id="aed91-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="aed91-108">W tym artykule różne nazwy są używane do identyfikowania typów plików używanych do migracji.</span><span class="sxs-lookup"><span data-stu-id="aed91-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="aed91-109">Podczas migracji projektu pliki zostaną nazwane inaczej, więc mentalnie dopasuj je do tych wymienionych poniżej:</span><span class="sxs-lookup"><span data-stu-id="aed91-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="aed91-110">Plik</span><span class="sxs-lookup"><span data-stu-id="aed91-110">File</span></span> | <span data-ttu-id="aed91-111">Opis</span><span class="sxs-lookup"><span data-stu-id="aed91-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="aed91-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="aed91-112">**MyApps.sln**</span></span> | <span data-ttu-id="aed91-113">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="aed91-113">The name of the solution file.</span></span> |
| <span data-ttu-id="aed91-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="aed91-114">**MyForms.csproj**</span></span> | <span data-ttu-id="aed91-115">Nazwa projektu .NET Framework Windows Forms do portu.</span><span class="sxs-lookup"><span data-stu-id="aed91-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="aed91-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="aed91-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="aed91-117">Nazwa nowego projektu .NET Core, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="aed91-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="aed91-118">**Plik MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="aed91-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="aed91-119">Plik wykonywalny aplikacji .NET Core Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="aed91-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="aed91-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="aed91-120">Prerequisites</span></span>

- <span data-ttu-id="aed91-121">[Visual Studio 2019 16.5 Wersja zapoznawcza 1](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&ch=pre&rel=16) lub nowsza dla każdej pracy projektanta, które chcesz wykonać.</span><span class="sxs-lookup"><span data-stu-id="aed91-121">[Visual Studio 2019 16.5 Preview 1](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&ch=pre&rel=16) or later for any designer work you want to do.</span></span> <span data-ttu-id="aed91-122">Zalecamy aktualizację do najnowszej [wersji preview programu Visual Studio](https://visualstudio.microsoft.com/vs/preview/)</span><span class="sxs-lookup"><span data-stu-id="aed91-122">We recommend to update to the latest [Preview version of Visual Studio](https://visualstudio.microsoft.com/vs/preview/)</span></span>

  <span data-ttu-id="aed91-123">Zainstaluj następujące obciążenia programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="aed91-123">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="aed91-124">Programowa firma .NET</span><span class="sxs-lookup"><span data-stu-id="aed91-124">.NET desktop development</span></span>
  - <span data-ttu-id="aed91-125">Tworzenie aplikacji dla wielu platform w środowisku .NET Core</span><span class="sxs-lookup"><span data-stu-id="aed91-125">.NET Core cross-platform development</span></span>

- <span data-ttu-id="aed91-126">Działający projekt windows forms w rozwiązaniu, które tworzy i działa bez problemu.</span><span class="sxs-lookup"><span data-stu-id="aed91-126">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="aed91-127">Projekt zakodowany w języku C#.</span><span class="sxs-lookup"><span data-stu-id="aed91-127">A project coded in C#.</span></span>

> [!NOTE]
> <span data-ttu-id="aed91-128">Projekty programu .NET Core 3.0 są obsługiwane tylko w **programie Visual Studio 2019** lub nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="aed91-128">.NET Core 3.0 projects are only supported in **Visual Studio 2019** or a later version.</span></span> <span data-ttu-id="aed91-129">Począwszy od **programu Visual Studio 2019 w wersji 16.5 Wersja zapoznawcza 1,** obsługiwany jest również projektant formularzy systemu Windows .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aed91-129">Starting with **Visual Studio 2019 version 16.5 Preview 1**, the .NET Core Windows Forms designer is also supported.</span></span>
>
> <span data-ttu-id="aed91-130">Aby włączyć projektanta, przejdź do pozycji Opcje **narzędzi** > **Options** > **W wersji zapoznawczej** **Environment** > i wybierz opcję Użyj **projektanta formularzy systemu Windows w wersji zapoznawczej dla aplikacji .NET Core.**</span><span class="sxs-lookup"><span data-stu-id="aed91-130">To enable the designer, go to **Tools** > **Options** > **Environment** > **Preview Features** and select the **Use the preview Windows Forms designer for .NET Core apps** option.</span></span>

### <a name="consider"></a><span data-ttu-id="aed91-131">Rozważyć</span><span class="sxs-lookup"><span data-stu-id="aed91-131">Consider</span></span>

<span data-ttu-id="aed91-132">Podczas przenoszenia aplikacji .NET Framework Windows Forms, istnieje kilka rzeczy, które należy wziąć pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="aed91-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="aed91-133">Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.</span><span class="sxs-lookup"><span data-stu-id="aed91-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="aed91-134">Użyj [analizatora przenoszenia platformy .NET,](../../standard/analyzers/portability-analyzer.md) aby ustalić, czy projekt zostanie zmigrowane do platformy .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="aed91-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="aed91-135">Jeśli projekt ma problemy z .NET Core 3.0, analizator pomaga zidentyfikować te problemy.</span><span class="sxs-lookup"><span data-stu-id="aed91-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="aed91-136">Używasz innej wersji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="aed91-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="aed91-137">Po wydaniu programu .NET Core 3.0 Preview 1 formularze windowsowe zostały otwarte w usłudze GitHub.</span><span class="sxs-lookup"><span data-stu-id="aed91-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open source on GitHub.</span></span> <span data-ttu-id="aed91-138">Kod dla .NET Core Windows Forms jest rozwidlią bazy kodu formularzy systemu Windows .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aed91-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms codebase.</span></span> <span data-ttu-id="aed91-139">Możliwe, że istnieją pewne różnice i aplikacja nie zostanie portowa.</span><span class="sxs-lookup"><span data-stu-id="aed91-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="aed91-140">[Pakiet zgodności systemu Windows][compat-pack] może pomóc w migracji.</span><span class="sxs-lookup"><span data-stu-id="aed91-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="aed91-141">Niektóre interfejsy API, które są dostępne w .NET Framework nie są dostępne w .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="aed91-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="aed91-142">[Pakiet zgodności systemu Windows][compat-pack] dodaje wiele z tych interfejsów API i może pomóc aplikacji Windows Forms w yciu w zgodności z programem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aed91-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="aed91-143">Zaktualizuj pakiety NuGet używane przez projekt.</span><span class="sxs-lookup"><span data-stu-id="aed91-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="aed91-144">Zawsze jest dobrą praktyką, aby użyć najnowszych wersji pakietów NuGet przed migracją.</span><span class="sxs-lookup"><span data-stu-id="aed91-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="aed91-145">Jeśli aplikacja odwołuje się do wszystkich pakietów NuGet, zaktualizuj je do najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="aed91-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="aed91-146">Upewnij się, że aplikacja tworzy pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aed91-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="aed91-147">Po uaktualnieniu, jeśli występują błędy pakietu, przejdź do najnowszej wersji, która nie przerywa kodu.</span><span class="sxs-lookup"><span data-stu-id="aed91-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="aed91-148">Tworzenie nowego projektu SDK</span><span class="sxs-lookup"><span data-stu-id="aed91-148">Create a new SDK project</span></span>

<span data-ttu-id="aed91-149">Nowy projekt .NET Core 3.0, który tworzysz, musi znajdować się w innym katalogu niż projekt programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aed91-149">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="aed91-150">Jeśli oba znajdują się w tym samym katalogu, można napotkać konflikty z plikami, które są generowane w katalogu **obj.**</span><span class="sxs-lookup"><span data-stu-id="aed91-150">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="aed91-151">W tym przykładzie utworzymy katalog o nazwie **MyFormsAppCore** w katalogu **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="aed91-151">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="aed91-152">Następnie należy utworzyć projekt **MyFormsCore.csproj** w katalogu **MyFormsAppCore.**</span><span class="sxs-lookup"><span data-stu-id="aed91-152">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="aed91-153">Plik można utworzyć ręcznie za pomocą wybranego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="aed91-153">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="aed91-154">Wklej w następującym formacie XML:</span><span class="sxs-lookup"><span data-stu-id="aed91-154">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="aed91-155">Jeśli nie chcesz ręcznie utworzyć pliku projektu, możesz użyć programu Visual Studio lub rdzenia SDK .NET do wygenerowania projektu.</span><span class="sxs-lookup"><span data-stu-id="aed91-155">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="aed91-156">Należy jednak usunąć wszystkie inne pliki wygenerowane przez szablon projektu, z wyjątkiem pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="aed91-156">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="aed91-157">Aby użyć sdk, uruchom następujące polecenie z katalogu **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="aed91-157">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="aed91-158">Po utworzeniu **pliku MyFormsCore.csproj**struktura katalogu powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="aed91-158">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="aed91-159">Dodaj projekt **MyFormsCore.csproj** do **myapps.sln** za pomocą programu Visual Studio lub interfejsu wiersza polecenia .NET Core z katalogu **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="aed91-159">Add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="aed91-160">Napraw generowanie informacji o zestawie</span><span class="sxs-lookup"><span data-stu-id="aed91-160">Fix assembly info generation</span></span>

<span data-ttu-id="aed91-161">Projekty formularzy systemu Windows, które `AssemblyInfo.cs` zostały utworzone za pomocą programu .NET Framework zawierają plik, który zawiera atrybuty zestawu, takie jak wersja zestawu, który ma zostać wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="aed91-161">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="aed91-162">Projekty w stylu SDK automatycznie generują te informacje na podstawie pliku projektu SDK.</span><span class="sxs-lookup"><span data-stu-id="aed91-162">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="aed91-163">Posiadanie obu typów "informacji o zestawieniu" tworzy konflikt.</span><span class="sxs-lookup"><span data-stu-id="aed91-163">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="aed91-164">Rozwiąż ten problem, wyłączając automatyczne generowanie, `AssemblyInfo.cs` co wymusza użycie istniejącego pliku przez projekt.</span><span class="sxs-lookup"><span data-stu-id="aed91-164">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="aed91-165">Istnieją trzy ustawienia, aby `<PropertyGroup>` dodać do węzła głównego.</span><span class="sxs-lookup"><span data-stu-id="aed91-165">There are three settings to add to the main `<PropertyGroup>` node.</span></span>

- <span data-ttu-id="aed91-166">**Generowanie AssemblyInfo**</span><span class="sxs-lookup"><span data-stu-id="aed91-166">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="aed91-167">Po ustawieniu tej `false`właściwości na , nie wygeneruje atrybutów zestawu.</span><span class="sxs-lookup"><span data-stu-id="aed91-167">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="aed91-168">Pozwala to uniknąć konfliktu `AssemblyInfo.cs` z istniejącym plikiem z projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aed91-168">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="aed91-169">**Assemblyname**</span><span class="sxs-lookup"><span data-stu-id="aed91-169">**AssemblyName**</span></span>\
<span data-ttu-id="aed91-170">Wartość tej właściwości jest binarny danych utworzonych podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="aed91-170">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="aed91-171">Nazwa nie wymaga dodania rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="aed91-171">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="aed91-172">Na przykład `MyCoreApp` przy `MyCoreApp.exe`użyciu produkuje .</span><span class="sxs-lookup"><span data-stu-id="aed91-172">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="aed91-173">**Rootnamespace**</span><span class="sxs-lookup"><span data-stu-id="aed91-173">**RootNamespace**</span></span>\
<span data-ttu-id="aed91-174">Domyślna przestrzeń nazw używana przez projekt.</span><span class="sxs-lookup"><span data-stu-id="aed91-174">The default namespace used by your project.</span></span> <span data-ttu-id="aed91-175">Powinno to odpowiadać domyślnej przestrzeni nazw projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aed91-175">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="aed91-176">Dodaj te trzy `<PropertyGroup>` elementy do `MyFormsCore.csproj` węzła w pliku:</span><span class="sxs-lookup"><span data-stu-id="aed91-176">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="aed91-177">Dodawanie kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="aed91-177">Add source code</span></span>

<span data-ttu-id="aed91-178">W tej chwili projekt **MyFormsCore.csproj** nie skompiluje żadnego kodu.</span><span class="sxs-lookup"><span data-stu-id="aed91-178">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="aed91-179">Domyślnie projekty .NET Core automatycznie zawierają cały kod źródłowy w bieżącym katalogu i katalogach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="aed91-179">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="aed91-180">Należy skonfigurować projekt, aby uwzględnić kod z projektu .NET Framework przy użyciu ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="aed91-180">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="aed91-181">Jeśli w projekcie programu .NET Framework użyto plików **.resx** dla ikon i zasobów dla formularzy, należy je również uwzględnić.</span><span class="sxs-lookup"><span data-stu-id="aed91-181">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span>

<span data-ttu-id="aed91-182">Dodaj następujący `<ItemGroup>` węzeł do projektu.</span><span class="sxs-lookup"><span data-stu-id="aed91-182">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="aed91-183">Każda instrukcja zawiera wzorzec glob pliku, który zawiera katalogi podrzędne.</span><span class="sxs-lookup"><span data-stu-id="aed91-183">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="aed91-184">Alternatywnie można utworzyć `<Compile>` lub `<EmbeddedResource>` wpis dla każdego pliku w projekcie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aed91-184">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="aed91-185">Dodawanie pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="aed91-185">Add NuGet packages</span></span>

<span data-ttu-id="aed91-186">Dodaj każdy pakiet NuGet, do którego odwołuje się projekt .NET Framework, do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aed91-186">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span>

<span data-ttu-id="aed91-187">Najprawdopodobniej aplikacja .NET Framework Windows Forms ma plik **packages.config,** który zawiera listę wszystkich pakietów NuGet, do których odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="aed91-187">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="aed91-188">Można spojrzeć na tej liście, aby ustalić, które pakiety NuGet dodać do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aed91-188">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="aed91-189">Na przykład jeśli projekt .NET Framework `MetroFramework` `MetroFramework.Design`odwołuje `MetroFramework.Fonts` się do pakietów , i NuGet, dodaj każdy do projektu za pomocą programu Visual Studio lub .NET Core CLI z katalogu **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="aed91-189">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="aed91-190">Poprzednie polecenia dodadzą następujące odwołania NuGet do projektu **MyFormsCore.csproj:**</span><span class="sxs-lookup"><span data-stu-id="aed91-190">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="aed91-191">Biblioteki sterowania portami</span><span class="sxs-lookup"><span data-stu-id="aed91-191">Port control libraries</span></span>

<span data-ttu-id="aed91-192">Jeśli masz projekt biblioteki formantów systemu Windows do portu, wskazówki są takie same jak przenoszenie projektu aplikacji .NET Framework Windows Forms, z wyjątkiem kilku ustawień.</span><span class="sxs-lookup"><span data-stu-id="aed91-192">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="aed91-193">I zamiast kompilować do pliku wykonywalnego, skompilować do biblioteki.</span><span class="sxs-lookup"><span data-stu-id="aed91-193">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="aed91-194">Różnica między projektem wykonywalnym a projektem biblioteki, oprócz ścieżek dla plików globs, które zawierają kod źródłowy, jest minimalna.</span><span class="sxs-lookup"><span data-stu-id="aed91-194">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="aed91-195">W przykładzie poprzedniego kroku można rozwinąć projekty i pliki, z którymi pracujemy.</span><span class="sxs-lookup"><span data-stu-id="aed91-195">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="aed91-196">Plik</span><span class="sxs-lookup"><span data-stu-id="aed91-196">File</span></span> | <span data-ttu-id="aed91-197">Opis</span><span class="sxs-lookup"><span data-stu-id="aed91-197">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="aed91-198">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="aed91-198">**MyApps.sln**</span></span> | <span data-ttu-id="aed91-199">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="aed91-199">The name of the solution file.</span></span> |
| <span data-ttu-id="aed91-200">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="aed91-200">**MyControls.csproj**</span></span> | <span data-ttu-id="aed91-201">Nazwa projektu .NET Framework Windows Forms Controls do portu.</span><span class="sxs-lookup"><span data-stu-id="aed91-201">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="aed91-202">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="aed91-202">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="aed91-203">Nazwa nowego projektu biblioteki .NET Core, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="aed91-203">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="aed91-204">**Plik MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="aed91-204">**MyCoreControls.dll**</span></span> | <span data-ttu-id="aed91-205">Biblioteka formantów formularzy systemu .NET Core Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="aed91-205">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="aed91-206">Należy wziąć pod `MyControlsCore.csproj` uwagę różnice między `MyFormsCore.csproj` projektem a poprzednio utworzonym projektem.</span><span class="sxs-lookup"><span data-stu-id="aed91-206">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="aed91-207">Oto przykład tego, jak wyglądałby plik projektu biblioteki .NET Core Windows Forms Controls:</span><span class="sxs-lookup"><span data-stu-id="aed91-207">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="aed91-208">Jak widać, `<OutputType>` węzeł został usunięty, który domyślnie kompilator do tworzenia biblioteki zamiast pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="aed91-208">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="aed91-209">I `<AssemblyName>` `<RootNamespace>` zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="aed91-209">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="aed91-210">W szczególności `<RootNamespace>` powinien odpowiadać przestrzeni nazw biblioteki formantów formularzy systemu Windows, które są porting.</span><span class="sxs-lookup"><span data-stu-id="aed91-210">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="aed91-211">Na koniec `<Compile>` węzły `<EmbeddedResource>` i węzły zostały dostosowane do folderu biblioteki formantów windows, którą przenosisz.</span><span class="sxs-lookup"><span data-stu-id="aed91-211">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="aed91-212">Następnie w głównym projekcie **.NET Core MyFormsCore.csproj** dodaj odwołanie do nowej biblioteki .NET Core Windows Forms Control.</span><span class="sxs-lookup"><span data-stu-id="aed91-212">Next, in the main .NET Core **MyFormsCore.csproj** project, add a reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="aed91-213">Dodaj odwołanie za pomocą programu Visual Studio lub interfejsu wiersza polecenia .NET Core z katalogu **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="aed91-213">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="aed91-214">Poprzednie polecenie dodaje następujące elementy do projektu **MyFormsCore.csproj:**</span><span class="sxs-lookup"><span data-stu-id="aed91-214">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a><span data-ttu-id="aed91-215">Problemy z kompilacją</span><span class="sxs-lookup"><span data-stu-id="aed91-215">Compilation problems</span></span>

<span data-ttu-id="aed91-216">Jeśli masz problemy z kompilowanie projektów, może być przy użyciu niektórych interfejsów API tylko dla systemu Windows, które są dostępne w programie .NET Framework, ale nie są dostępne w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aed91-216">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="aed91-217">Możesz spróbować dodać pakiet NuGet [pakietu zgodności systemu Windows][compat-pack] do projektu.</span><span class="sxs-lookup"><span data-stu-id="aed91-217">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="aed91-218">Ten pakiet działa tylko w systemie Windows i dodaje około 20 000 interfejsów API systemu Windows do projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="aed91-218">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="aed91-219">Poprzednie polecenie dodaje następujące elementy do projektu **MyFormsCore.csproj:**</span><span class="sxs-lookup"><span data-stu-id="aed91-219">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="aed91-220">Projektant Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aed91-220">Windows Forms Designer</span></span>

<span data-ttu-id="aed91-221">Jak opisano w tym artykule, program Visual Studio 2019 obsługuje tylko Projektanta formularzy w projektach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aed91-221">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="aed91-222">Tworząc projekt .NET Core obok siebie, można przetestować projekt za pomocą programu .NET Core podczas projektowania formularzy za pomocą projektu programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aed91-222">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="aed91-223">Plik rozwiązania zawiera zarówno .NET Framework i .NET Core projektów.</span><span class="sxs-lookup"><span data-stu-id="aed91-223">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="aed91-224">Dodaj i zaprojektuj formularze i formanty w projekcie .NET Framework, a na podstawie wzorców glob plików dodaliśmy do projektów .NET Core, wszystkie nowe lub zmienione pliki zostaną automatycznie uwzględnione w projektach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aed91-224">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="aed91-225">Gdy program Visual Studio 2019 obsługuje projektanta formularzy systemu Windows, można skopiować/wkleić zawartość pliku projektu .NET Core do pliku projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aed91-225">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="aed91-226">Następnie usuń wzorce glob pliku `<Source>` `<EmbeddedResource>` dodane z i elementów.</span><span class="sxs-lookup"><span data-stu-id="aed91-226">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="aed91-227">Napraw ścieżki do dowolnego odwołania do projektu używanego przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="aed91-227">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="aed91-228">To skutecznie uaktualnia projekt programu .NET Framework do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aed91-228">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="aed91-229">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="aed91-229">Next steps</span></span>

- <span data-ttu-id="aed91-230">Dowiedz się więcej o [przerywaniu zmian z programu .NET Framework na platformę .NET Core](../compatibility/fx-core.md).</span><span class="sxs-lookup"><span data-stu-id="aed91-230">Learn about [breaking changes from .NET Framework to .NET Core](../compatibility/fx-core.md).</span></span>
- <span data-ttu-id="aed91-231">Dowiedz się więcej o pakiecie [zgodności systemu Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="aed91-231">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="aed91-232">Obejrzyj [klip wideo dotyczący przenoszenia](https://www.youtube.com/watch?v=upVQEUc_KwU) projektu formularzy systemu Windows framework do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aed91-232">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
