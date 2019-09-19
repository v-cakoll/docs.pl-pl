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
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a><span data-ttu-id="16037-103">Instrukcje: Port aplikacji klasycznej WPF do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="16037-103">How to: Port a WPF desktop app to .NET Core</span></span>

<span data-ttu-id="16037-104">W tym artykule opisano sposób przenoszenia aplikacji klasycznej opartej na Windows Presentation Foundation (WPF) z .NET Framework do programu .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="16037-104">This article describes how to port your Windows Presentation Foundation-based (WPF) desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="16037-105">Zestaw SDK platformy .NET Core 3,0 obsługuje aplikacje WPF.</span><span class="sxs-lookup"><span data-stu-id="16037-105">The .NET Core 3.0 SDK includes support for WPF applications.</span></span> <span data-ttu-id="16037-106">WPF jest nadal strukturą tylko dla systemu Windows i działa tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="16037-106">WPF is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="16037-107">W tym przykładzie jest używany interfejs wiersza polecenia zestaw .NET Core SDK do tworzenia projektu i zarządzania nim.</span><span class="sxs-lookup"><span data-stu-id="16037-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="16037-108">W tym artykule różne nazwy są używane do identyfikowania typów plików używanych do migracji.</span><span class="sxs-lookup"><span data-stu-id="16037-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="16037-109">Podczas migrowania projektu pliki będą wyglądać inaczej, dlatego można je dopasować do nich w sposób psychiczny do wymienionych poniżej:</span><span class="sxs-lookup"><span data-stu-id="16037-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="16037-110">Plik</span><span class="sxs-lookup"><span data-stu-id="16037-110">File</span></span> | <span data-ttu-id="16037-111">Opis</span><span class="sxs-lookup"><span data-stu-id="16037-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="16037-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="16037-112">**MyApps.sln**</span></span> | <span data-ttu-id="16037-113">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="16037-113">The name of the solution file.</span></span> |
| <span data-ttu-id="16037-114">**MyWPF.csproj**</span><span class="sxs-lookup"><span data-stu-id="16037-114">**MyWPF.csproj**</span></span> | <span data-ttu-id="16037-115">Nazwa .NET Framework projektu WPF do port.</span><span class="sxs-lookup"><span data-stu-id="16037-115">The name of the .NET Framework WPF project to port.</span></span> |
| <span data-ttu-id="16037-116">**MyWPFCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="16037-116">**MyWPFCore.csproj**</span></span> | <span data-ttu-id="16037-117">Nazwa nowego projektu .NET Core, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="16037-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="16037-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="16037-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="16037-119">Plik wykonywalny aplikacji WPF platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16037-119">The .NET Core WPF app executable.</span></span> |

>[!IMPORTANT]
><span data-ttu-id="16037-120">Mimo że w tym artykule C# jest stosowany język docelowy, kroki są takie same dla VB.NET, z tą różnicą, że VB.NET używa plików *. vbproj* i *. vb* zamiast plików *. csproj* i *. cs* .</span><span class="sxs-lookup"><span data-stu-id="16037-120">Even though this article uses C# as the target language, the steps are the same for VB.NET, except that VB.NET uses *.vbproj* and *.vb* files instead of *.csproj* and *.cs* files, respectively.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="16037-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="16037-121">Prerequisites</span></span>

- <span data-ttu-id="16037-122">[Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) dla wszystkich zadań, które chcesz wykonać.</span><span class="sxs-lookup"><span data-stu-id="16037-122">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="16037-123">Zainstaluj następujące obciążenia programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="16037-123">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="16037-124">Programowanie aplikacji klasycznych dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="16037-124">.NET desktop development</span></span>
  - <span data-ttu-id="16037-125">Programowanie dla wielu platform w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="16037-125">.NET cross-platform development</span></span>

- <span data-ttu-id="16037-126">Roboczy projekt WPF w rozwiązaniu, które kompiluje i uruchamia bez problemu.</span><span class="sxs-lookup"><span data-stu-id="16037-126">A working WPF project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="16037-127">Zainstaluj najnowszą wersję zapoznawczą [programu .NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="16037-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="16037-128">**Program Visual Studio 2017** nie obsługuje projektów programu .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="16037-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="16037-129">**Program Visual Studio 2019** obsługuje projekty platformy .net Core 3,0, ale ma ograniczoną obsługę programu .NET Core WPF Visual Designer.</span><span class="sxs-lookup"><span data-stu-id="16037-129">**Visual Studio 2019** supports .NET Core 3.0 projects but has limited support for the .NET Core WPF visual designer.</span></span> <span data-ttu-id="16037-130">Aby użyć w pełni obsługiwanego projektanta wizualnego, musisz mieć .NET Framework projekt WPF w rozwiązaniu, które udostępnia swoje pliki w projekcie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16037-130">To use a fully-supported visual designer, you must have a .NET Framework WPF project in your solution that shares its files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="16037-131">Pod</span><span class="sxs-lookup"><span data-stu-id="16037-131">Consider</span></span>

<span data-ttu-id="16037-132">Podczas przenoszenia aplikacji .NET Framework WPF należy wziąć pod uwagę kilka rzeczy.</span><span class="sxs-lookup"><span data-stu-id="16037-132">When porting a .NET Framework WPF application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="16037-133">Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.</span><span class="sxs-lookup"><span data-stu-id="16037-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="16037-134">Użyj [analizatora przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md) , aby określić, czy projekt zostanie zmigrowany do programu .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="16037-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="16037-135">Jeśli projekt zawiera problemy z platformą .NET Core 3,0, Analizator pomaga zidentyfikować te problemy.</span><span class="sxs-lookup"><span data-stu-id="16037-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="16037-136">Używasz innej wersji WPF.</span><span class="sxs-lookup"><span data-stu-id="16037-136">You're using a different version of WPF.</span></span>

    <span data-ttu-id="16037-137">Po wydaniu programu .NET Core 3,0 wersja zapoznawcza 1 program WPF otrzymał wartość Open Source w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="16037-137">When .NET Core 3.0 Preview 1 was released, WPF went open-source on GitHub.</span></span> <span data-ttu-id="16037-138">Kod dla platformy .NET Core WPF jest rozwidleniem bazy kodu .NET Framework WPF.</span><span class="sxs-lookup"><span data-stu-id="16037-138">The code for .NET Core WPF is a fork of the .NET Framework WPF code base.</span></span> <span data-ttu-id="16037-139">Istnieją pewne różnice, które nie są dostępne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16037-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="16037-140">[Pakiet zgodności systemu Windows][compat-pack] może pomóc w migracji.</span><span class="sxs-lookup"><span data-stu-id="16037-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="16037-141">Niektóre interfejsy API, które są dostępne w .NET Framework nie są dostępne w programie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="16037-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="16037-142">[Pakiet zgodności systemu Windows][compat-pack] dodaje wiele z tych interfejsów API i może pomóc aplikacji WPF z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16037-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your WPF app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="16037-143">Zaktualizuj pakiety NuGet używane przez Twój projekt.</span><span class="sxs-lookup"><span data-stu-id="16037-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="16037-144">Zawsze dobrym sposobem jest użycie najnowszych wersji pakietów NuGet przed migracją.</span><span class="sxs-lookup"><span data-stu-id="16037-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="16037-145">Jeśli aplikacja odwołuje się do wszystkich pakietów NuGet, zaktualizuj je do najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="16037-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="16037-146">Upewnij się, że aplikacja została pomyślnie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="16037-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="16037-147">Po uaktualnieniu, jeśli występują jakiekolwiek błędy pakietów, można obniżyć pakiet do najnowszej wersji, która nie powoduje przerwania kodu.</span><span class="sxs-lookup"><span data-stu-id="16037-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="16037-148">Program Visual Studio 2019 nie obsługuje jeszcze projektanta WPF dla platformy .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="16037-148">Visual Studio 2019 doesn't yet support the WPF Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="16037-149">Obecnie należy zachować istniejący plik programu .NET Framework WPF, jeśli chcesz używać projektanta WPF w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="16037-149">Currently, you need to keep your existing .NET Framework WPF project file if you want to use the WPF Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="16037-150">Utwórz nowy projekt zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="16037-150">Create a new SDK project</span></span>

<span data-ttu-id="16037-151">Nowy projekt platformy .NET Core 3,0, który tworzysz, musi znajdować się w innym katalogu niż projekt .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16037-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="16037-152">Jeśli oba te elementy znajdują się w tym samym katalogu, może wystąpić konflikt z plikami, które są generowane w katalogu **obj** .</span><span class="sxs-lookup"><span data-stu-id="16037-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="16037-153">W tym przykładzie utworzysz katalog o nazwie **MyWPFAppCore** w katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="16037-153">In this example, you'll create a directory named **MyWPFAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

<span data-ttu-id="16037-154">Następnie należy utworzyć projekt **MyWPFCore. csproj** w katalogu **MyWPFAppCore** .</span><span class="sxs-lookup"><span data-stu-id="16037-154">Next, you need to create the **MyWPFCore.csproj** project in the **MyWPFAppCore** directory.</span></span> <span data-ttu-id="16037-155">Ten plik można utworzyć ręcznie przy użyciu edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="16037-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="16037-156">Wklej następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="16037-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="16037-157">Jeśli nie chcesz tworzyć pliku projektu ręcznie, możesz użyć programu Visual Studio lub zestaw .NET Core SDK do wygenerowania projektu.</span><span class="sxs-lookup"><span data-stu-id="16037-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="16037-158">Należy jednak usunąć wszystkie inne pliki wygenerowane przez szablon projektu, z wyjątkiem pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="16037-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="16037-159">Aby użyć zestawu SDK, uruchom następujące polecenie w katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="16037-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

<span data-ttu-id="16037-160">Po utworzeniu **MyWPFCore. csproj**struktura katalogów powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="16037-160">After you create the **MyWPFCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

<span data-ttu-id="16037-161">Należy dodać projekt **MyWPFCore. csproj** do elementu **webapps. sln** z programem Visual Studio lub interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="16037-161">You'll want to add the **MyWPFCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="16037-162">Napraw generowanie informacji o zestawie</span><span class="sxs-lookup"><span data-stu-id="16037-162">Fix assembly info generation</span></span>

<span data-ttu-id="16037-163">Windows Presentation Foundation projekty, które zostały utworzone za pomocą .NET Framework `AssemblyInfo.cs` obejmują plik, który zawiera atrybuty zestawu, takie jak wersja zestawu do wygenerowania.</span><span class="sxs-lookup"><span data-stu-id="16037-163">Windows Presentation Foundation projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="16037-164">Projekty w stylu zestawu SDK automatycznie generują te informacje na podstawie pliku projektu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="16037-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="16037-165">W przypadku obu typów "informacje o zestawie" powstaje konflikt.</span><span class="sxs-lookup"><span data-stu-id="16037-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="16037-166">Rozwiąż ten problem, wyłączając automatyczne generowanie, co wymusza, aby projekt korzystał `AssemblyInfo.cs` z istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="16037-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="16037-167">Istnieją trzy ustawienia do dodania do węzła głównego `<PropertyGroup>` .</span><span class="sxs-lookup"><span data-stu-id="16037-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="16037-168">**GenerateAssemblyInfo**</span><span class="sxs-lookup"><span data-stu-id="16037-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="16037-169">Ustawienie tej właściwości na `false`, nie spowoduje wygenerowanie atrybutów zestawu.</span><span class="sxs-lookup"><span data-stu-id="16037-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="16037-170">Pozwala to uniknąć konfliktu z istniejącym `AssemblyInfo.cs` plikiem z projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16037-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="16037-171">**AssemblyName**</span><span class="sxs-lookup"><span data-stu-id="16037-171">**AssemblyName**</span></span>\
<span data-ttu-id="16037-172">Wartością tej właściwości jest wyjściowy plik binarny tworzony podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="16037-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="16037-173">Nazwa nie wymaga dodanego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="16037-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="16037-174">Na przykład przy użyciu `MyCoreApp` polecenia `MyCoreApp.exe`Generuj.</span><span class="sxs-lookup"><span data-stu-id="16037-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="16037-175">**RootNamespace**</span><span class="sxs-lookup"><span data-stu-id="16037-175">**RootNamespace**</span></span>\
<span data-ttu-id="16037-176">Domyślna przestrzeń nazw używana przez projekt.</span><span class="sxs-lookup"><span data-stu-id="16037-176">The default namespace used by your project.</span></span> <span data-ttu-id="16037-177">Powinna być zgodna z domyślną przestrzenią nazw projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16037-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="16037-178">Dodaj te trzy elementy do `<PropertyGroup>` węzła `MyWPFCore.csproj` w pliku:</span><span class="sxs-lookup"><span data-stu-id="16037-178">Add these three elements to the `<PropertyGroup>` node in the `MyWPFCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="16037-179">Dodaj kod źródłowy</span><span class="sxs-lookup"><span data-stu-id="16037-179">Add source code</span></span>
<span data-ttu-id="16037-180">Teraz projekt **MyWPFCore. csproj** nie kompiluje żadnego kodu.</span><span class="sxs-lookup"><span data-stu-id="16037-180">Right now, the **MyWPFCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="16037-181">Domyślnie projekty platformy .NET Core automatycznie uwzględniają cały kod źródłowy w bieżącym katalogu i wszystkich katalogach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="16037-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="16037-182">Należy skonfigurować projekt do dołączania kodu z projektu .NET Framework przy użyciu ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="16037-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="16037-183">Jeśli projekt .NET Framework używał plików **resx** dla ikon i zasobów dla okien i kontrolek, należy uwzględnić te pliki.</span><span class="sxs-lookup"><span data-stu-id="16037-183">If your .NET Framework project used **.resx** files for icons and resources for your windows and controls, you'll need to include those too.</span></span> 

<span data-ttu-id="16037-184">Pierwszy `<ItemGroup>` węzeł, który należy dodać do projektu, zawiera plik **App. XAML** , który reprezentuje konfigurację startową i zasoby używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="16037-184">The first `<ItemGroup>` node you need to add to your project includes the **App.xaml** file that represents the startup config and resources your app uses.</span></span> <span data-ttu-id="16037-185">Plik **App. XAML** ma także towarzyszący plik **App.XAML.cs** , ale zostanie automatycznie dołączony do innego `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="16037-185">The **App.xaml** file also has an accompanying **App.xaml.cs** file, but it will be automatically included in a different `<ItemGroup>`.</span></span>

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

<span data-ttu-id="16037-186">Następnie Dodaj następujący `<ItemGroup>` węzeł do projektu.</span><span class="sxs-lookup"><span data-stu-id="16037-186">Next, add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="16037-187">Każda instrukcja zawiera wzorzec globalizowania pliku, który zawiera katalogi podrzędne.</span><span class="sxs-lookup"><span data-stu-id="16037-187">Each statement includes a file glob pattern that includes child directories.</span></span> <span data-ttu-id="16037-188">Zawiera kod źródłowy projektu, wszystkie pliki ustawień i wszystkie zasoby.</span><span class="sxs-lookup"><span data-stu-id="16037-188">It includes the source code for your project, any settings files, and any resources.</span></span> <span data-ttu-id="16037-189">Katalog **obj** jest jawnie wykluczony.</span><span class="sxs-lookup"><span data-stu-id="16037-189">The **obj** directory is explicitly excluded.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="16037-190">`<ItemGroup>` Następnie Dołącz inny `<Page>` węzeł zawierający wpis dla każdego pliku **XAML** w projekcie, z wyjątkiem pliku **App. XAML** .</span><span class="sxs-lookup"><span data-stu-id="16037-190">Next, include another `<ItemGroup>` node that contains a `<Page>` entry for every **xaml** file in your project except the **App.xaml** file.</span></span> <span data-ttu-id="16037-191">Zawierają one wszystkie okna, strony i zasoby, które są w formacie **XAML** .</span><span class="sxs-lookup"><span data-stu-id="16037-191">These contain all of the windows, pages, and resources that are in **xaml** format.</span></span> <span data-ttu-id="16037-192">Nie można użyć w tym miejscu wzorca globalizowania i musi on dodać wpis dla każdego pliku i wskazać `<Generator>` używany.</span><span class="sxs-lookup"><span data-stu-id="16037-192">You cannot use a glob pattern here and must add an entry for every file and indicate the `<Generator>` used.</span></span>

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a><span data-ttu-id="16037-193">Dodaj pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="16037-193">Add NuGet packages</span></span>

<span data-ttu-id="16037-194">Dodaj każdy pakiet NuGet, do którego odwołuje się projekt .NET Framework, do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16037-194">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="16037-195">Prawdopodobnie aplikacja WPF .NET Framework ma plik **Packages. config** zawierający listę wszystkich pakietów NuGet, do których odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="16037-195">Most likely your .NET Framework WPF app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="16037-196">Możesz zapoznać się z tą listą, aby określić, które pakiety NuGet dodać do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16037-196">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="16037-197">Na przykład jeśli projekt .NET Framework odwołuje `MahApps.Metro` się do pakietu NuGet, Dodaj go do projektu za pomocą programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="16037-197">For example, if the .NET Framework project references the `MahApps.Metro` NuGet package, add it to the project with Visual Studio.</span></span> <span data-ttu-id="16037-198">Możesz również dodać odwołanie do pakietu przy użyciu interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="16037-198">You can also add the package reference with the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

<span data-ttu-id="16037-199">Poprzednie polecenie doda następujące odwołanie NuGet do projektu **MyWPFCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="16037-199">The previous command would add the following NuGet reference to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="16037-200">Problemy skompilowane</span><span class="sxs-lookup"><span data-stu-id="16037-200">Problems compiling</span></span>

<span data-ttu-id="16037-201">Jeśli masz problemy z kompilowaniem projektów, możesz używać niektórych interfejsów API tylko dla systemu Windows, które są dostępne w .NET Framework ale nie są dostępne w środowisku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16037-201">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="16037-202">Możesz spróbować dodać pakiet NuGet pakietu [zgodności systemu Windows][compat-pack] do projektu.</span><span class="sxs-lookup"><span data-stu-id="16037-202">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="16037-203">Ten pakiet działa tylko w systemie Windows i dodaje około 20 000 interfejsów API systemu Windows do projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="16037-203">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="16037-204">Poprzednie polecenie dodaje następujący do projektu **MyWPFCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="16037-204">The previous command adds the following to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a><span data-ttu-id="16037-205">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="16037-205">WPF Designer</span></span>

<span data-ttu-id="16037-206">Zgodnie z opisem w tym artykule program Visual Studio 2019 obsługuje tylko projektanta WPF w projektach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16037-206">As detailed in this article, Visual Studio 2019 only supports the WPF Designer in .NET Framework projects.</span></span> <span data-ttu-id="16037-207">Tworząc równoległy projekt platformy .NET Core, można testować projekt przy użyciu platformy .NET Core podczas projektowania formularzy przy użyciu projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16037-207">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="16037-208">Plik rozwiązania zawiera zarówno projekty .NET Framework, jak i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16037-208">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="16037-209">Dodawanie i projektowanie formularzy i kontrolek w projekcie .NET Framework i opartych na wzorcach globalizowania plików dodanych do projektów .NET Core, wszystkie nowe lub zmienione pliki zostaną automatycznie uwzględnione w projektach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16037-209">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="16037-210">Gdy program Visual Studio 2019 obsługuje projektanta WPF, można skopiować/wkleić zawartość pliku projektu .NET Core do pliku projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16037-210">Once Visual Studio 2019 supports the WPF Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="16037-211">Następnie usuń pliki wzorców globalizowania dodane z `<Source>` elementami i. `<EmbeddedResource>`</span><span class="sxs-lookup"><span data-stu-id="16037-211">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="16037-212">Popraw ścieżki do dowolnych odwołań do projektu używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="16037-212">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="16037-213">Efektywnie uaktualnia projekt .NET Framework do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16037-213">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="16037-214">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="16037-214">Next steps</span></span>

- <span data-ttu-id="16037-215">Przeczytaj więcej na temat [pakietu zgodności systemu Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="16037-215">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="16037-216">Obejrzyj [film wideo podczas przenoszenia](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) projektu WPF .NET Framework na platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="16037-216">Watch a [video on porting](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) your .NET Framework WPF project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
