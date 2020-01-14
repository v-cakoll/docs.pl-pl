---
title: Port aplikacji Windows Forms do programu .NET Core
description: Naucz się, w jaki sposób portować .NET Framework aplikację Windows Forms do programu .NET Core dla systemu Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.openlocfilehash: b1048c2d725a2bcf8398af1d2d53f40efc36c82e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936965"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="c6cd9-103">Jak przenieść aplikację klasyczną Windows Forms na platformę .NET Core</span><span class="sxs-lookup"><span data-stu-id="c6cd9-103">How to port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="c6cd9-104">W tym artykule opisano sposób przenoszenia aplikacji klasycznej opartej na Windows Forms z .NET Framework do programu .NET Core 3,0 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0 or later.</span></span> <span data-ttu-id="c6cd9-105">Zestaw .NET Core 3,0 SDK obejmuje obsługę aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="c6cd9-106">Windows Forms nadal jest strukturą tylko dla systemu Windows i działa tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="c6cd9-107">W tym przykładzie jest używany interfejs wiersza polecenia zestaw .NET Core SDK do tworzenia projektu i zarządzania nim.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="c6cd9-108">W tym artykule różne nazwy są używane do identyfikowania typów plików używanych do migracji.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="c6cd9-109">Podczas migrowania projektu pliki będą wyglądać inaczej, dlatego można je dopasować do nich w sposób psychiczny do wymienionych poniżej:</span><span class="sxs-lookup"><span data-stu-id="c6cd9-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="c6cd9-110">Plik</span><span class="sxs-lookup"><span data-stu-id="c6cd9-110">File</span></span> | <span data-ttu-id="c6cd9-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c6cd9-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="c6cd9-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="c6cd9-112">**MyApps.sln**</span></span> | <span data-ttu-id="c6cd9-113">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-113">The name of the solution file.</span></span> |
| <span data-ttu-id="c6cd9-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="c6cd9-114">**MyForms.csproj**</span></span> | <span data-ttu-id="c6cd9-115">Nazwa .NET Framework Windows Forms projektu do portów.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="c6cd9-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="c6cd9-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="c6cd9-117">Nazwa nowego projektu .NET Core, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="c6cd9-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="c6cd9-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="c6cd9-119">Plik wykonywalny aplikacji .NET Core Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="c6cd9-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c6cd9-120">Prerequisites</span></span>

- <span data-ttu-id="c6cd9-121">[Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) dla wszystkich zadań, które chcesz wykonać.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="c6cd9-122">Zainstaluj następujące obciążenia programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="c6cd9-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="c6cd9-123">Programowanie aplikacji klasycznych dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="c6cd9-123">.NET desktop development</span></span>
  - <span data-ttu-id="c6cd9-124">Programowanie dla wielu platform .NET core</span><span class="sxs-lookup"><span data-stu-id="c6cd9-124">.NET Core cross-platform development</span></span>

- <span data-ttu-id="c6cd9-125">Projekt działającego Windows Forms w rozwiązaniu, które kompiluje i uruchamia bez problemu.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="c6cd9-126">Projekt zakodowany w C#.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-126">A project coded in C#.</span></span>
- <span data-ttu-id="c6cd9-127">[.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3,0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-127">[.NET Core](https://dotnet.microsoft.com/download/dotnet-core) 3.0 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="c6cd9-128">**Program Visual Studio 2017** nie obsługuje projektów programu .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="c6cd9-129">**Program Visual Studio 2019** obsługuje projekty platformy .net Core 3,0, ale nie obsługuje jeszcze projektanta wizualizacji dla projektów .net core 3,0 Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="c6cd9-130">Aby użyć projektanta wizualnego, musisz mieć projekt .NET Windows Forms w rozwiązaniu, które współużytkuje pliki formularzy z projektem platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-130">To use the visual designer, you must have a .NET Windows Forms project in a solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="c6cd9-131">Pod</span><span class="sxs-lookup"><span data-stu-id="c6cd9-131">Consider</span></span>

<span data-ttu-id="c6cd9-132">Podczas przenoszenia aplikacji Windows Forms .NET Framework należy wziąć pod uwagę kilka rzeczy.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="c6cd9-133">Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="c6cd9-134">Użyj [analizatora przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md) , aby określić, czy projekt zostanie zmigrowany do programu .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="c6cd9-135">Jeśli projekt zawiera problemy z platformą .NET Core 3,0, Analizator pomaga zidentyfikować te problemy.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="c6cd9-136">Używasz innej wersji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="c6cd9-137">Po wydaniu programu .NET Core 3,0 w wersji zapoznawczej 1 Windows Forms mógł zostać otwartym źródłem w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open source on GitHub.</span></span> <span data-ttu-id="c6cd9-138">Kod dla Windows Forms .NET Core jest rozwidleniem bazy kodu .NET Framework Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms codebase.</span></span> <span data-ttu-id="c6cd9-139">Istnieją pewne różnice, które nie są dostępne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="c6cd9-140">[Pakiet zgodności systemu Windows][compat-pack] może pomóc w migracji.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="c6cd9-141">Niektóre interfejsy API, które są dostępne w .NET Framework nie są dostępne w programie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="c6cd9-142">[Pakiet zgodności systemu Windows][compat-pack] dodaje wiele z tych interfejsów API i może pomóc aplikacji Windows Forms być zgodny z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="c6cd9-143">Zaktualizuj pakiety NuGet używane przez Twój projekt.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="c6cd9-144">Zawsze dobrym sposobem jest użycie najnowszych wersji pakietów NuGet przed migracją.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="c6cd9-145">Jeśli aplikacja odwołuje się do wszystkich pakietów NuGet, zaktualizuj je do najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="c6cd9-146">Upewnij się, że aplikacja została pomyślnie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="c6cd9-147">Po uaktualnieniu, jeśli występują jakiekolwiek błędy pakietów, można obniżyć pakiet do najnowszej wersji, która nie powoduje przerwania kodu.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="c6cd9-148">Program Visual Studio 2019 jeszcze nie obsługuje projektanta formularzy dla programu .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="c6cd9-148">Visual Studio 2019 doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="c6cd9-149">Obecnie należy zachować istniejące .NET Framework Windows Forms pliku projektu, jeśli chcesz użyć projektanta formularzy z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="c6cd9-150">Utwórz nowy projekt zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="c6cd9-150">Create a new SDK project</span></span>

<span data-ttu-id="c6cd9-151">Nowy projekt platformy .NET Core 3,0, który tworzysz, musi znajdować się w innym katalogu niż projekt .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="c6cd9-152">Jeśli oba te elementy znajdują się w tym samym katalogu, może wystąpić konflikt z plikami, które są generowane w katalogu **obj** .</span><span class="sxs-lookup"><span data-stu-id="c6cd9-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="c6cd9-153">W tym przykładzie utworzymy katalog o nazwie **MyFormsAppCore** w katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="c6cd9-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="c6cd9-154">Następnie należy utworzyć projekt **MyFormsCore. csproj** w katalogu **MyFormsAppCore** .</span><span class="sxs-lookup"><span data-stu-id="c6cd9-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="c6cd9-155">Ten plik można utworzyć ręcznie przy użyciu edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="c6cd9-156">Wklej następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="c6cd9-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="c6cd9-157">Jeśli nie chcesz tworzyć pliku projektu ręcznie, możesz użyć programu Visual Studio lub zestaw .NET Core SDK do wygenerowania projektu.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="c6cd9-158">Należy jednak usunąć wszystkie inne pliki wygenerowane przez szablon projektu, z wyjątkiem pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="c6cd9-159">Aby użyć zestawu SDK, uruchom następujące polecenie w katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="c6cd9-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="c6cd9-160">Po utworzeniu **MyFormsCore. csproj**struktura katalogów powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="c6cd9-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="c6cd9-161">Dodaj projekt **MyFormsCore. csproj** do elementu **webapps. sln** z programem Visual Studio lub interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="c6cd9-161">Add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="c6cd9-162">Napraw generowanie informacji o zestawie</span><span class="sxs-lookup"><span data-stu-id="c6cd9-162">Fix assembly info generation</span></span>

<span data-ttu-id="c6cd9-163">Windows Forms projekty, które zostały utworzone za pomocą .NET Framework obejmują plik `AssemblyInfo.cs`, który zawiera atrybuty zestawu, takie jak wersja zestawu do wygenerowania.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="c6cd9-164">Projekty w stylu zestawu SDK automatycznie generują te informacje na podstawie pliku projektu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="c6cd9-165">W przypadku obu typów "informacje o zestawie" powstaje konflikt.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="c6cd9-166">Rozwiąż ten problem, wyłączając automatyczne generowanie, co wymusza, aby projekt korzystał z istniejącego pliku `AssemblyInfo.cs`.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="c6cd9-167">Istnieją trzy ustawienia do dodania do głównego węzła `<PropertyGroup>`.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span>

- <span data-ttu-id="c6cd9-168">**GenerateAssemblyInfo**</span><span class="sxs-lookup"><span data-stu-id="c6cd9-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="c6cd9-169">Ustawienie tej właściwości na `false`nie spowoduje wygenerowanie atrybutów zestawu.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="c6cd9-170">Pozwala to uniknąć konfliktu z istniejącym plikiem `AssemblyInfo.cs` z projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="c6cd9-171">\ **AssemblyName**</span><span class="sxs-lookup"><span data-stu-id="c6cd9-171">**AssemblyName**\</span></span>
<span data-ttu-id="c6cd9-172">Wartością tej właściwości jest wyjściowy plik binarny tworzony podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="c6cd9-173">Nazwa nie wymaga dodanego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="c6cd9-174">Na przykład przy użyciu `MyCoreApp` tworzy `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="c6cd9-175">**RootNamespace**</span><span class="sxs-lookup"><span data-stu-id="c6cd9-175">**RootNamespace**</span></span>\
<span data-ttu-id="c6cd9-176">Domyślna przestrzeń nazw używana przez projekt.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-176">The default namespace used by your project.</span></span> <span data-ttu-id="c6cd9-177">Powinna być zgodna z domyślną przestrzenią nazw projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="c6cd9-178">Dodaj te trzy elementy do węzła `<PropertyGroup>` w pliku `MyFormsCore.csproj`:</span><span class="sxs-lookup"><span data-stu-id="c6cd9-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="c6cd9-179">Dodaj kod źródłowy</span><span class="sxs-lookup"><span data-stu-id="c6cd9-179">Add source code</span></span>

<span data-ttu-id="c6cd9-180">Teraz projekt **MyFormsCore. csproj** nie kompiluje żadnego kodu.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="c6cd9-181">Domyślnie projekty platformy .NET Core automatycznie uwzględniają cały kod źródłowy w bieżącym katalogu i wszystkich katalogach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="c6cd9-182">Należy skonfigurować projekt do dołączania kodu z projektu .NET Framework przy użyciu ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="c6cd9-183">Jeśli projekt .NET Framework używał plików **resx** dla ikon i zasobów formularzy, należy uwzględnić te pliki.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span>

<span data-ttu-id="c6cd9-184">Dodaj następujący węzeł `<ItemGroup>` do projektu.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="c6cd9-185">Każda instrukcja zawiera wzorzec globalizowania pliku, który zawiera katalogi podrzędne.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="c6cd9-186">Alternatywnie można utworzyć wpis `<Compile>` lub `<EmbeddedResource>` dla każdego pliku w .NET Framework projekcie.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="c6cd9-187">Dodaj pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="c6cd9-187">Add NuGet packages</span></span>

<span data-ttu-id="c6cd9-188">Dodaj każdy pakiet NuGet, do którego odwołuje się projekt .NET Framework, do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span>

<span data-ttu-id="c6cd9-189">Prawdopodobnie aplikacja Windows Forms .NET Framework ma plik **Packages. config** zawierający listę wszystkich pakietów NuGet, do których odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="c6cd9-190">Możesz zapoznać się z tą listą, aby określić, które pakiety NuGet dodać do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="c6cd9-191">Na przykład jeśli projekt .NET Framework odwołuje się do `MetroFramework`, `MetroFramework.Design`i `MetroFramework.Fonts` pakietów NuGet, należy dodać każdy do projektu z Visual Studio lub interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="c6cd9-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="c6cd9-192">Poprzednie polecenia spowodują dodanie następujących odwołań NuGet do projektu **MyFormsCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="c6cd9-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="c6cd9-193">Biblioteki kontrolek portu</span><span class="sxs-lookup"><span data-stu-id="c6cd9-193">Port control libraries</span></span>

<span data-ttu-id="c6cd9-194">Jeśli masz projekt biblioteki formantów Windows Forms do portu, kierunki są takie same jak w przypadku portów .NET Framework projektu aplikacji Windows Forms, z wyjątkiem kilku ustawień.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="c6cd9-195">I zamiast kompilowania do pliku wykonywalnego, należy skompilować do biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="c6cd9-196">Różnica między projektem wykonywalnym i projektem biblioteki, oprócz ścieżki dla pliku elementy globalne, który zawiera kod źródłowy, jest minimalna.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="c6cd9-197">Korzystając z przykładu poprzedniego kroku, program umożliwia rozwinięcie projektów i plików, z którymi pracujemy.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="c6cd9-198">Plik</span><span class="sxs-lookup"><span data-stu-id="c6cd9-198">File</span></span> | <span data-ttu-id="c6cd9-199">Opis</span><span class="sxs-lookup"><span data-stu-id="c6cd9-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="c6cd9-200">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="c6cd9-200">**MyApps.sln**</span></span> | <span data-ttu-id="c6cd9-201">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-201">The name of the solution file.</span></span> |
| <span data-ttu-id="c6cd9-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="c6cd9-202">**MyControls.csproj**</span></span> | <span data-ttu-id="c6cd9-203">Nazwa .NET Framework Windows Forms kontroluje projekt do portu.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="c6cd9-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="c6cd9-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="c6cd9-205">Nazwa nowego projektu biblioteki .NET Core, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="c6cd9-206">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="c6cd9-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="c6cd9-207">Biblioteka formantów Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-207">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="c6cd9-208">Należy wziąć pod uwagę różnice między projektem `MyControlsCore.csproj` i wcześniej utworzonym projektem `MyFormsCore.csproj`.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="c6cd9-209">Poniżej znajduje się przykład pliku projektu biblioteki formantów Windows Forms .NET Core:</span><span class="sxs-lookup"><span data-stu-id="c6cd9-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="c6cd9-210">Jak widać, węzeł `<OutputType>` został usunięty, który domyślnie kompilator tworzy bibliotekę zamiast pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="c6cd9-211">`<AssemblyName>` i `<RootNamespace>` zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="c6cd9-212">W `<RootNamespace>` powinna być zgodna z przestrzenią nazw biblioteki formantów Windows Forms, która jest przeprojektowana.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="c6cd9-213">A wreszcie węzły `<Compile>` i `<EmbeddedResource>` zostały dostosowane do folderu bibliotek formantów Windows Forms, które są przełączone.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="c6cd9-214">Następnie w głównym projekcie programu .NET Core **MyFormsCore. csproj** Dodaj odwołanie do nowej biblioteki formantów Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-214">Next, in the main .NET Core **MyFormsCore.csproj** project add reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="c6cd9-215">Dodaj odwołanie z programu Visual Studio lub interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="c6cd9-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="c6cd9-216">Poprzednie polecenie dodaje następujący do projektu **MyFormsCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="c6cd9-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a><span data-ttu-id="c6cd9-217">Problemy z kompilacją</span><span class="sxs-lookup"><span data-stu-id="c6cd9-217">Compilation problems</span></span>

<span data-ttu-id="c6cd9-218">Jeśli masz problemy z kompilowaniem projektów, możesz używać niektórych interfejsów API tylko dla systemu Windows, które są dostępne w .NET Framework ale nie są dostępne w środowisku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="c6cd9-219">Możesz spróbować dodać pakiet NuGet pakietu [zgodności systemu Windows][compat-pack] do projektu.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="c6cd9-220">Ten pakiet działa tylko w systemie Windows i dodaje około 20 000 interfejsów API systemu Windows do projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="c6cd9-221">Poprzednie polecenie dodaje następujący do projektu **MyFormsCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="c6cd9-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="c6cd9-222">Projektant Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6cd9-222">Windows Forms Designer</span></span>

<span data-ttu-id="c6cd9-223">Zgodnie z opisem w tym artykule program Visual Studio 2019 obsługuje tylko projektanta formularzy w projektach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-223">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="c6cd9-224">Tworząc równoległy projekt platformy .NET Core, można testować projekt przy użyciu platformy .NET Core podczas projektowania formularzy przy użyciu projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="c6cd9-225">Plik rozwiązania zawiera zarówno projekty .NET Framework, jak i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="c6cd9-226">Dodawanie i projektowanie formularzy i kontrolek w projekcie .NET Framework i opartych na wzorcach globalizowania plików dodanych do projektów .NET Core, wszystkie nowe lub zmienione pliki zostaną automatycznie uwzględnione w projektach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="c6cd9-227">Gdy program Visual Studio 2019 obsługuje Projektant formularzy systemu Windows, można skopiować/wkleić zawartość pliku projektu .NET Core do pliku projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="c6cd9-228">Następnie usuń pliki wzorców globalizowania dodane z `<Source>` i `<EmbeddedResource>` elementów.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="c6cd9-229">Popraw ścieżki do dowolnych odwołań do projektu używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="c6cd9-230">Efektywnie uaktualnia projekt .NET Framework do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c6cd9-231">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="c6cd9-231">Next steps</span></span>

- <span data-ttu-id="c6cd9-232">Informacje o istotnych [zmianach z .NET Framework na platformę .NET Core](../compatibility/fx-core.md).</span><span class="sxs-lookup"><span data-stu-id="c6cd9-232">Learn about [breaking changes from .NET Framework to .NET Core](../compatibility/fx-core.md).</span></span>
- <span data-ttu-id="c6cd9-233">Przeczytaj więcej na temat [pakietu zgodności systemu Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="c6cd9-233">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="c6cd9-234">Obejrzyj [film wideo podczas przenoszenia](https://www.youtube.com/watch?v=upVQEUc_KwU) projektu Windows Forms .NET Framework do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6cd9-234">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
