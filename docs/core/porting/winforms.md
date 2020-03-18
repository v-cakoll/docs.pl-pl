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
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="e5c92-103">Jak przenieść aplikację klasyczną Windows Forms do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="e5c92-103">How to port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="e5c92-104">W tym artykule opisano sposób przenoszenia aplikacji klasycznej opartej na formularzach Systemu Windows z platformy .NET Framework do programu .NET Core 3.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="e5c92-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0 or later.</span></span> <span data-ttu-id="e5c92-105">Zestaw SDK .NET Core 3.0 zawiera obsługę aplikacji windows forms.</span><span class="sxs-lookup"><span data-stu-id="e5c92-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="e5c92-106">Formularze systemu Windows są nadal strukturą tylko dla systemu Windows i są uruchamiane tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="e5c92-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="e5c92-107">W tym przykładzie użyto cli sdk.NET Core do tworzenia projektu i zarządzania nim.</span><span class="sxs-lookup"><span data-stu-id="e5c92-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="e5c92-108">W tym artykule różne nazwy są używane do identyfikowania typów plików używanych do migracji.</span><span class="sxs-lookup"><span data-stu-id="e5c92-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="e5c92-109">Podczas migracji projektu pliki będą nazywane inaczej, więc psychicznie dopasować je do wymienionych poniżej:</span><span class="sxs-lookup"><span data-stu-id="e5c92-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="e5c92-110">Plik</span><span class="sxs-lookup"><span data-stu-id="e5c92-110">File</span></span> | <span data-ttu-id="e5c92-111">Opis</span><span class="sxs-lookup"><span data-stu-id="e5c92-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="e5c92-112">**Aplikacja MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="e5c92-112">**MyApps.sln**</span></span> | <span data-ttu-id="e5c92-113">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e5c92-113">The name of the solution file.</span></span> |
| <span data-ttu-id="e5c92-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="e5c92-114">**MyForms.csproj**</span></span> | <span data-ttu-id="e5c92-115">Nazwa projektu formularzy systemu Windows .NET Framework do portu.</span><span class="sxs-lookup"><span data-stu-id="e5c92-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="e5c92-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="e5c92-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="e5c92-117">Nazwa nowego tworzonego projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5c92-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="e5c92-118">**MójAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="e5c92-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="e5c92-119">Plik wykonywalny aplikacji .NET Core Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e5c92-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="e5c92-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e5c92-120">Prerequisites</span></span>

- <span data-ttu-id="e5c92-121">[Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) dla każdej pracy projektanta, którą chcesz wykonać.</span><span class="sxs-lookup"><span data-stu-id="e5c92-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="e5c92-122">Zainstaluj następujące obciążenia programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="e5c92-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="e5c92-123">Tworzenie komputerów stacjonarnych .NET</span><span class="sxs-lookup"><span data-stu-id="e5c92-123">.NET desktop development</span></span>
  - <span data-ttu-id="e5c92-124">Tworzenie aplikacji dla wielu platform w środowisku .NET Core</span><span class="sxs-lookup"><span data-stu-id="e5c92-124">.NET Core cross-platform development</span></span>

- <span data-ttu-id="e5c92-125">Działający projekt formularzy systemu Windows w rozwiązaniu, które tworzy i działa bez problemu.</span><span class="sxs-lookup"><span data-stu-id="e5c92-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="e5c92-126">Projekt zakodowany w języku C#.</span><span class="sxs-lookup"><span data-stu-id="e5c92-126">A project coded in C#.</span></span>
- <span data-ttu-id="e5c92-127">[.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3.0 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="e5c92-127">[.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3.0 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="e5c92-128">**Program Visual Studio 2017** nie obsługuje projektów programu .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e5c92-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="e5c92-129">**Program Visual Studio 2019** obsługuje projekty programu .NET Core 3.0, ale nie obsługuje jeszcze projektanta wizualnego dla projektów .NET Core 3.0 Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e5c92-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="e5c92-130">Aby użyć projektanta wizualnego, musisz mieć projekt .NET Windows Forms w rozwiązaniu, które udostępnia pliki formularzy z projektem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5c92-130">To use the visual designer, you must have a .NET Windows Forms project in a solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="e5c92-131">Rozważyć</span><span class="sxs-lookup"><span data-stu-id="e5c92-131">Consider</span></span>

<span data-ttu-id="e5c92-132">Podczas przenoszenia aplikacji formularzy systemu Windows .NET Framework należy wziąć pod uwagę kilka rzeczy.</span><span class="sxs-lookup"><span data-stu-id="e5c92-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="e5c92-133">Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.</span><span class="sxs-lookup"><span data-stu-id="e5c92-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="e5c92-134">Użyj [analizatora przenośności .NET,](../../standard/analyzers/portability-analyzer.md) aby określić, czy projekt zostanie migrowany do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e5c92-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="e5c92-135">Jeśli projekt ma problemy z .NET Core 3.0, analizator pomaga zidentyfikować te problemy.</span><span class="sxs-lookup"><span data-stu-id="e5c92-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="e5c92-136">Używasz innej wersji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e5c92-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="e5c92-137">Po wydaniu programu .NET Core 3.0 Preview 1 formularze systemu Windows zostały udostępnione w usylotach open source w usteercie GitHub.</span><span class="sxs-lookup"><span data-stu-id="e5c92-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open source on GitHub.</span></span> <span data-ttu-id="e5c92-138">Kod .NET Core Windows Forms jest rozwidlenie .NET Framework Windows Forms codebase.</span><span class="sxs-lookup"><span data-stu-id="e5c92-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms codebase.</span></span> <span data-ttu-id="e5c92-139">Możliwe, że istnieją pewne różnice, a aplikacja nie będzie portować.</span><span class="sxs-lookup"><span data-stu-id="e5c92-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="e5c92-140">[Pakiet zgodności systemu Windows][compat-pack] może pomóc w migracji.</span><span class="sxs-lookup"><span data-stu-id="e5c92-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="e5c92-141">Niektóre interfejsy API, które są dostępne w platformie .NET Framework nie są dostępne w .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e5c92-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="e5c92-142">[Pakiet zgodności systemu Windows][compat-pack] dodaje wiele z tych interfejsów API i może pomóc aplikacji Windows Forms stać się zgodna z .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5c92-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="e5c92-143">Zaktualizuj pakiety NuGet używane przez projekt.</span><span class="sxs-lookup"><span data-stu-id="e5c92-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="e5c92-144">Zawsze jest dobrą praktyką, aby używać najnowszych wersji pakietów NuGet przed migracją.</span><span class="sxs-lookup"><span data-stu-id="e5c92-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="e5c92-145">Jeśli aplikacja odwołuje się do żadnych pakietów NuGet, zaktualizuj je do najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="e5c92-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="e5c92-146">Upewnij się, że aplikacja tworzy pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e5c92-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="e5c92-147">Po uaktualnieniu, jeśli występują błędy pakietu, obniżyć pakiet do najnowszej wersji, która nie łamie kodu.</span><span class="sxs-lookup"><span data-stu-id="e5c92-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="e5c92-148">Program Visual Studio 2019 nie obsługuje jeszcze projektanta formularzy dla .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e5c92-148">Visual Studio 2019 doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="e5c92-149">Obecnie należy zachować istniejący plik projektu formularzy systemu .NET Framework Windows, jeśli chcesz użyć Projektanta formularzy z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e5c92-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="e5c92-150">Tworzenie nowego projektu SDK</span><span class="sxs-lookup"><span data-stu-id="e5c92-150">Create a new SDK project</span></span>

<span data-ttu-id="e5c92-151">Utworzony nowy projekt .NET Core 3.0 musi znajdować się w innym katalogu niż projekt .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5c92-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="e5c92-152">Jeśli oba znajdują się w tym samym katalogu, możesz napotkać konflikty z plikami, które są generowane w katalogu **obj.**</span><span class="sxs-lookup"><span data-stu-id="e5c92-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="e5c92-153">W tym przykładzie utworzymy katalog o nazwie **MyFormsAppCore** w katalogu **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="e5c92-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="e5c92-154">Następnie musisz utworzyć projekt **MyFormsCore.csproj** w katalogu **MyFormsAppCore.**</span><span class="sxs-lookup"><span data-stu-id="e5c92-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="e5c92-155">Można utworzyć ten plik ręcznie za pomocą edytora tekstu z wyboru.</span><span class="sxs-lookup"><span data-stu-id="e5c92-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="e5c92-156">Wklej w następującym xml:</span><span class="sxs-lookup"><span data-stu-id="e5c92-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="e5c92-157">Jeśli nie chcesz ręcznie tworzyć pliku projektu, możesz użyć programu Visual Studio lub sdk .NET Core do wygenerowania projektu.</span><span class="sxs-lookup"><span data-stu-id="e5c92-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="e5c92-158">Należy jednak usunąć wszystkie inne pliki wygenerowane przez szablon projektu z wyjątkiem pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e5c92-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="e5c92-159">Aby użyć sdk, uruchom następujące polecenie z katalogu **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="e5c92-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="e5c92-160">Po utworzeniu **MyFormsCore.csproj**struktura katalogów powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="e5c92-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="e5c92-161">Dodaj projekt **MyFormsCore.csproj** do **pliku MyApps.sln** za pomocą programu Visual Studio lub kontrolera CLI programu .NET Core z katalogu **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="e5c92-161">Add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="e5c92-162">Napraw generowanie informacji o montażu</span><span class="sxs-lookup"><span data-stu-id="e5c92-162">Fix assembly info generation</span></span>

<span data-ttu-id="e5c92-163">Projekty formularzy systemu Windows, które zostały `AssemblyInfo.cs` utworzone za pomocą programu .NET Framework, zawierają plik zawierający atrybuty zestawu, takie jak wersja zestawu, który ma zostać wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="e5c92-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="e5c92-164">Projekty w stylu SDK automatycznie generują te informacje na podstawie pliku projektu SDK.</span><span class="sxs-lookup"><span data-stu-id="e5c92-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="e5c92-165">Posiadanie obu typów "informacji o zestawie" tworzy konflikt.</span><span class="sxs-lookup"><span data-stu-id="e5c92-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="e5c92-166">Rozwiąż ten problem, wyłączając automatyczne generowanie, co `AssemblyInfo.cs` wymusza, aby projekt używał istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="e5c92-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="e5c92-167">Istnieją trzy ustawienia, które `<PropertyGroup>` należy dodać do węzła głównego.</span><span class="sxs-lookup"><span data-stu-id="e5c92-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span>

- <span data-ttu-id="e5c92-168">**Generuj informacje o zestawie**</span><span class="sxs-lookup"><span data-stu-id="e5c92-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="e5c92-169">Po ustawieniu tej `false`właściwości , nie będzie generować atrybuty zestawu.</span><span class="sxs-lookup"><span data-stu-id="e5c92-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="e5c92-170">Pozwala to uniknąć konfliktu `AssemblyInfo.cs` z istniejącym plikiem z projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5c92-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="e5c92-171">**Assemblyname**</span><span class="sxs-lookup"><span data-stu-id="e5c92-171">**AssemblyName**</span></span>\
<span data-ttu-id="e5c92-172">Wartość tej właściwości jest wyjściowym binarnym utworzonym podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="e5c92-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="e5c92-173">Nazwa nie wymaga rozszerzenia dodane do niego.</span><span class="sxs-lookup"><span data-stu-id="e5c92-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="e5c92-174">Na przykład `MyCoreApp` przy `MyCoreApp.exe`użyciu produkuje .</span><span class="sxs-lookup"><span data-stu-id="e5c92-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="e5c92-175">**Rootnamespace**</span><span class="sxs-lookup"><span data-stu-id="e5c92-175">**RootNamespace**</span></span>\
<span data-ttu-id="e5c92-176">Domyślny obszar nazw używany przez projekt.</span><span class="sxs-lookup"><span data-stu-id="e5c92-176">The default namespace used by your project.</span></span> <span data-ttu-id="e5c92-177">Powinno to być zgodne z domyślnym obszarem nazw projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5c92-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="e5c92-178">Dodaj te trzy `<PropertyGroup>` elementy do `MyFormsCore.csproj` węzła w pliku:</span><span class="sxs-lookup"><span data-stu-id="e5c92-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="e5c92-179">Dodawanie kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="e5c92-179">Add source code</span></span>

<span data-ttu-id="e5c92-180">W tej chwili projekt **MyFormsCore.csproj** nie skompilował żadnego kodu.</span><span class="sxs-lookup"><span data-stu-id="e5c92-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="e5c92-181">Domyślnie projekty programu .NET Core automatycznie zawierają cały kod źródłowy w bieżącym katalogu i wszystkie katalogi podrzędne.</span><span class="sxs-lookup"><span data-stu-id="e5c92-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="e5c92-182">Należy skonfigurować projekt, aby uwzględnić kod z projektu .NET Framework przy użyciu ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="e5c92-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="e5c92-183">Jeśli w projekcie .NET Framework użyto plików **.resx** dla ikon i zasobów dla formularzy, należy je również uwzględnić.</span><span class="sxs-lookup"><span data-stu-id="e5c92-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span>

<span data-ttu-id="e5c92-184">Dodaj następujący `<ItemGroup>` węzeł do projektu.</span><span class="sxs-lookup"><span data-stu-id="e5c92-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="e5c92-185">Każda instrukcja zawiera wzorzec glob pliku, który zawiera katalogi podrzędne.</span><span class="sxs-lookup"><span data-stu-id="e5c92-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="e5c92-186">Alternatywnie można utworzyć `<Compile>` lub `<EmbeddedResource>` wpis dla każdego pliku w projekcie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5c92-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="e5c92-187">Dodawanie pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="e5c92-187">Add NuGet packages</span></span>

<span data-ttu-id="e5c92-188">Dodaj każdy pakiet NuGet, do którego odwołuje się projekt .NET Framework, do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5c92-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span>

<span data-ttu-id="e5c92-189">Najprawdopodobniej aplikacja .NET Framework Windows Forms ma plik **packages.config,** który zawiera listę wszystkich pakietów NuGet, do których odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="e5c92-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="e5c92-190">Możesz spojrzeć na tej liście, aby określić, które pakiety NuGet, aby dodać do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5c92-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="e5c92-191">Na przykład jeśli projekt .NET Framework `MetroFramework` `MetroFramework.Design`odwołuje `MetroFramework.Fonts` się do pakietów , i NuGet, dodaj każdy z nich do projektu za pomocą programu Visual Studio lub kontrolera CLI .NET Core z katalogu **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="e5c92-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="e5c92-192">Poprzednie polecenia dodają następujące odwołania NuGet do projektu **MyFormsCore.csproj:**</span><span class="sxs-lookup"><span data-stu-id="e5c92-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="e5c92-193">Biblioteki sterowania portem</span><span class="sxs-lookup"><span data-stu-id="e5c92-193">Port control libraries</span></span>

<span data-ttu-id="e5c92-194">Jeśli masz projekt biblioteki formantów formularzy systemu Windows do portu, wskazówki są takie same jak przenoszenie projektu aplikacji formularzy .NET Framework Windows Forms, z wyjątkiem kilku ustawień.</span><span class="sxs-lookup"><span data-stu-id="e5c92-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="e5c92-195">I zamiast kompilować do pliku wykonywalnego, można skompilować do biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e5c92-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="e5c92-196">Różnica między projektem wykonywalnym a projektem biblioteki, oprócz ścieżek dla globs plików, które zawierają kod źródłowy, jest minimalna.</span><span class="sxs-lookup"><span data-stu-id="e5c92-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="e5c92-197">Korzystając z przykładu poprzedniego kroku, pozwala rozwinąć projekty i pliki, z którymi pracujemy.</span><span class="sxs-lookup"><span data-stu-id="e5c92-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="e5c92-198">Plik</span><span class="sxs-lookup"><span data-stu-id="e5c92-198">File</span></span> | <span data-ttu-id="e5c92-199">Opis</span><span class="sxs-lookup"><span data-stu-id="e5c92-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="e5c92-200">**Aplikacja MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="e5c92-200">**MyApps.sln**</span></span> | <span data-ttu-id="e5c92-201">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e5c92-201">The name of the solution file.</span></span> |
| <span data-ttu-id="e5c92-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="e5c92-202">**MyControls.csproj**</span></span> | <span data-ttu-id="e5c92-203">Nazwa .NET Framework Windows Forms Controls projektu do portu.</span><span class="sxs-lookup"><span data-stu-id="e5c92-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="e5c92-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="e5c92-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="e5c92-205">Nazwa nowego tworzonego projektu biblioteki .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5c92-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="e5c92-206">**Plik MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="e5c92-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="e5c92-207">Biblioteka formantów formularzy systemu .NET Core Windows.</span><span class="sxs-lookup"><span data-stu-id="e5c92-207">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="e5c92-208">Należy wziąć pod `MyControlsCore.csproj` uwagę różnice między `MyFormsCore.csproj` projektem a wcześniej utworzonym projektem.</span><span class="sxs-lookup"><span data-stu-id="e5c92-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="e5c92-209">Oto przykład tego, jak wyglądałby plik projektu biblioteki formantów formularzy systemu .NET Core Windows:</span><span class="sxs-lookup"><span data-stu-id="e5c92-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="e5c92-210">Jak `<OutputType>` widać, węzeł został usunięty, co domyślnie kompilator do produkcji biblioteki zamiast pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="e5c92-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="e5c92-211">I `<AssemblyName>` `<RootNamespace>` zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="e5c92-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="e5c92-212">W szczególności `<RootNamespace>` powinien odpowiadać przestrzeni nazw biblioteki formantów formularzy systemu Windows, które są przenoszeni.</span><span class="sxs-lookup"><span data-stu-id="e5c92-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="e5c92-213">I na `<Compile>` koniec `<EmbeddedResource>` węzły i węzły zostały dostosowane do folderu w portingowej bibliotece Formanty formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e5c92-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="e5c92-214">Następnie w głównym projekcie **.NET Core MyFormsCore.csproj** dodaj odwołanie do nowej biblioteki kontroli formularzy systemu .NET Core systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e5c92-214">Next, in the main .NET Core **MyFormsCore.csproj** project, add a reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="e5c92-215">Dodaj odwołanie do programu Visual Studio lub kontrolera CLI programu .NET Core z katalogu **SolutionFolder:**</span><span class="sxs-lookup"><span data-stu-id="e5c92-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="e5c92-216">Poprzednie polecenie dodaje następujące do **projektu MyFormsCore.csproj:**</span><span class="sxs-lookup"><span data-stu-id="e5c92-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a><span data-ttu-id="e5c92-217">Problemy z kompilacją</span><span class="sxs-lookup"><span data-stu-id="e5c92-217">Compilation problems</span></span>

<span data-ttu-id="e5c92-218">Jeśli masz problemy ze kompilowaniem projektów, być może używasz niektórych interfejsów API tylko dla systemu Windows, które są dostępne w programie .NET Framework, ale nie są dostępne w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5c92-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="e5c92-219">Możesz spróbować dodać pakiet [NuGet pakietu zgodności systemu Windows][compat-pack] do projektu.</span><span class="sxs-lookup"><span data-stu-id="e5c92-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="e5c92-220">Ten pakiet działa tylko w systemie Windows i dodaje około 20 000 interfejsów API systemu Windows do projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e5c92-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="e5c92-221">Poprzednie polecenie dodaje następujące do **projektu MyFormsCore.csproj:**</span><span class="sxs-lookup"><span data-stu-id="e5c92-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="e5c92-222">Projektant Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5c92-222">Windows Forms Designer</span></span>

<span data-ttu-id="e5c92-223">Jak opisano w tym artykule program Visual Studio 2019 obsługuje tylko projektanta formularzy w projektach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5c92-223">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="e5c92-224">Tworząc projekt .NET Core obok siebie, można przetestować projekt za pomocą programu .NET Core podczas projektowania formularzy za pomocą projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5c92-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="e5c92-225">Plik rozwiązania zawiera zarówno projekty .NET Framework, jak i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5c92-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="e5c92-226">Dodawanie i projektowanie formularzy i formantów w projekcie .NET Framework oraz na podstawie wzorców glob plików dodanych do projektów .NET Core, wszystkie nowe lub zmienione pliki zostaną automatycznie uwzględnione w projektach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5c92-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="e5c92-227">Po programie Visual Studio 2019 obsługuje Windows Forms Designer, można skopiować/wkleić zawartość pliku projektu .NET Core do pliku projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5c92-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="e5c92-228">Następnie usuń wzorce glob `<Source>` pliku `<EmbeddedResource>` dodane z elementami i.</span><span class="sxs-lookup"><span data-stu-id="e5c92-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="e5c92-229">Napraw ścieżki do dowolnego odwołania do projektu używanego przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e5c92-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="e5c92-230">To skutecznie uaktualnia projekt .NET Framework do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5c92-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e5c92-231">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="e5c92-231">Next steps</span></span>

- <span data-ttu-id="e5c92-232">Dowiedz się więcej o [wprowadzaniu zmian z programu .NET Framework do programu .NET Core](../compatibility/fx-core.md).</span><span class="sxs-lookup"><span data-stu-id="e5c92-232">Learn about [breaking changes from .NET Framework to .NET Core](../compatibility/fx-core.md).</span></span>
- <span data-ttu-id="e5c92-233">Dowiedz się więcej o [pakiecie zgodności systemu Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="e5c92-233">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="e5c92-234">Obejrzyj [klip wideo dotyczący przenoszenia](https://www.youtube.com/watch?v=upVQEUc_KwU) projektu formularzy systemu Windows programu .NET Framework do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5c92-234">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
