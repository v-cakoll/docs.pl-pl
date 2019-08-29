---
title: Port aplikacji Windows Forms do programu .NET Core 3,0
description: Naucz się, w jaki sposób portować .NET Framework aplikację Windows Forms do programu .NET Core 3,0 dla systemu Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: 7ef36be47648ae338b5fe70b75431006c99be31f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105215"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="6855f-103">Instrukcje: Port aplikacji klasycznej Windows Forms do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="6855f-103">How to: Port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="6855f-104">W tym artykule opisano sposób przenoszenia aplikacji klasycznej opartej na Windows Forms z .NET Framework do programu .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6855f-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="6855f-105">Zestaw .NET Core 3,0 SDK obejmuje obsługę aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6855f-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="6855f-106">Windows Forms nadal jest strukturą tylko dla systemu Windows i działa tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="6855f-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="6855f-107">W tym przykładzie jest używany interfejs wiersza polecenia zestaw .NET Core SDK do tworzenia projektu i zarządzania nim.</span><span class="sxs-lookup"><span data-stu-id="6855f-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="6855f-108">W tym artykule różne nazwy są używane do identyfikowania typów plików używanych do migracji.</span><span class="sxs-lookup"><span data-stu-id="6855f-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="6855f-109">Podczas migrowania projektu pliki będą wyglądać inaczej, dlatego można je dopasować do nich w sposób psychiczny do wymienionych poniżej:</span><span class="sxs-lookup"><span data-stu-id="6855f-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="6855f-110">Plik</span><span class="sxs-lookup"><span data-stu-id="6855f-110">File</span></span> | <span data-ttu-id="6855f-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6855f-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="6855f-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="6855f-112">**MyApps.sln**</span></span> | <span data-ttu-id="6855f-113">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="6855f-113">The name of the solution file.</span></span> |
| <span data-ttu-id="6855f-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="6855f-114">**MyForms.csproj**</span></span> | <span data-ttu-id="6855f-115">Nazwa .NET Framework Windows Forms projektu do portów.</span><span class="sxs-lookup"><span data-stu-id="6855f-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="6855f-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="6855f-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="6855f-117">Nazwa nowego projektu .NET Core, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="6855f-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="6855f-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="6855f-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="6855f-119">Plik wykonywalny aplikacji .NET Core Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6855f-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="6855f-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="6855f-120">Prerequisites</span></span>

- <span data-ttu-id="6855f-121">[Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) dla wszystkich zadań, które chcesz wykonać.</span><span class="sxs-lookup"><span data-stu-id="6855f-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="6855f-122">Zainstaluj następujące obciążenia programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="6855f-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="6855f-123">Programowanie aplikacji klasycznych dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="6855f-123">.NET desktop development</span></span>
  - <span data-ttu-id="6855f-124">Programowanie dla wielu platform w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="6855f-124">.NET cross-platform development</span></span>

- <span data-ttu-id="6855f-125">Projekt działającego Windows Forms w rozwiązaniu, które kompiluje i uruchamia bez problemu.</span><span class="sxs-lookup"><span data-stu-id="6855f-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="6855f-126">Projekt musi być zakodowany w C#.</span><span class="sxs-lookup"><span data-stu-id="6855f-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="6855f-127">Zainstaluj najnowszą wersję zapoznawczą [programu .NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="6855f-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="6855f-128">**Program Visual Studio 2017** nie obsługuje projektów programu .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6855f-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="6855f-129">**Program Visual Studio 2019** obsługuje projekty platformy .net Core 3,0, ale nie obsługuje jeszcze projektanta wizualizacji dla projektów .net core 3,0 Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6855f-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="6855f-130">Aby użyć projektanta wizualnego, musisz mieć projekt .NET Windows Forms w rozwiązaniu, które współużytkuje pliki formularzy z projektem platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6855f-130">To use the visual designer, you must have a .NET Windows Forms project in your solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="6855f-131">Pod</span><span class="sxs-lookup"><span data-stu-id="6855f-131">Consider</span></span>

<span data-ttu-id="6855f-132">Podczas przenoszenia aplikacji Windows Forms .NET Framework należy wziąć pod uwagę kilka rzeczy.</span><span class="sxs-lookup"><span data-stu-id="6855f-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="6855f-133">Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.</span><span class="sxs-lookup"><span data-stu-id="6855f-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="6855f-134">Użyj [analizatora przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md) , aby określić, czy projekt zostanie zmigrowany do programu .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6855f-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="6855f-135">Jeśli projekt zawiera problemy z platformą .NET Core 3,0, Analizator pomaga zidentyfikować te problemy.</span><span class="sxs-lookup"><span data-stu-id="6855f-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="6855f-136">Używasz innej wersji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6855f-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="6855f-137">Po wydaniu programu .NET Core 3,0 w wersji zapoznawczej 1 Windows Forms poszło do otwarcia źródła w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="6855f-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open-source on GitHub.</span></span> <span data-ttu-id="6855f-138">Kod dla Windows Forms .NET Core jest rozwidleniem podstawy kodu .NET Framework Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6855f-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms code base.</span></span> <span data-ttu-id="6855f-139">Istnieją pewne różnice, które nie są dostępne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6855f-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="6855f-140">[Pakiet zgodności systemu Windows][compat-pack] może pomóc w migracji.</span><span class="sxs-lookup"><span data-stu-id="6855f-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="6855f-141">Niektóre interfejsy API, które są dostępne w .NET Framework nie są dostępne w programie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6855f-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="6855f-142">[Pakiet zgodności systemu Windows][compat-pack] dodaje wiele z tych interfejsów API i może pomóc aplikacji Windows Forms być zgodny z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6855f-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="6855f-143">Zaktualizuj pakiety NuGet używane przez Twój projekt.</span><span class="sxs-lookup"><span data-stu-id="6855f-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="6855f-144">Zawsze dobrym sposobem jest użycie najnowszych wersji pakietów NuGet przed migracją.</span><span class="sxs-lookup"><span data-stu-id="6855f-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="6855f-145">Jeśli aplikacja odwołuje się do wszystkich pakietów NuGet, zaktualizuj je do najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="6855f-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="6855f-146">Upewnij się, że aplikacja została pomyślnie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="6855f-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="6855f-147">Po uaktualnieniu, jeśli występują jakiekolwiek błędy pakietów, można obniżyć pakiet do najnowszej wersji, która nie powoduje przerwania kodu.</span><span class="sxs-lookup"><span data-stu-id="6855f-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="6855f-148">Program Visual Studio 2019 jeszcze nie obsługuje projektanta formularzy dla programu .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="6855f-148">Visual Studio 2019 doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="6855f-149">Obecnie należy zachować istniejące .NET Framework Windows Forms pliku projektu, jeśli chcesz użyć projektanta formularzy z programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6855f-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="6855f-150">Utwórz nowy projekt zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6855f-150">Create a new SDK project</span></span>

<span data-ttu-id="6855f-151">Nowy projekt platformy .NET Core 3,0, który tworzysz, musi znajdować się w innym katalogu niż projekt .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6855f-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="6855f-152">Jeśli oba te elementy znajdują się w tym samym katalogu, może wystąpić konflikt z plikami, które są generowane w katalogu **obj** .</span><span class="sxs-lookup"><span data-stu-id="6855f-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="6855f-153">W tym przykładzie utworzymy katalog o nazwie **MyFormsAppCore** w katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="6855f-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="6855f-154">Następnie należy utworzyć projekt **MyFormsCore. csproj** w katalogu **MyFormsAppCore** .</span><span class="sxs-lookup"><span data-stu-id="6855f-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="6855f-155">Ten plik można utworzyć ręcznie przy użyciu edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="6855f-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="6855f-156">Wklej następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="6855f-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="6855f-157">Jeśli nie chcesz tworzyć pliku projektu ręcznie, możesz użyć programu Visual Studio lub zestaw .NET Core SDK do wygenerowania projektu.</span><span class="sxs-lookup"><span data-stu-id="6855f-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="6855f-158">Należy jednak usunąć wszystkie inne pliki wygenerowane przez szablon projektu, z wyjątkiem pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="6855f-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="6855f-159">Aby użyć zestawu SDK, uruchom następujące polecenie w katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="6855f-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="6855f-160">Po utworzeniu **MyFormsCore. csproj**struktura katalogów powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="6855f-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="6855f-161">Należy dodać projekt **MyFormsCore. csproj** do elementu webapps **. sln** z programem Visual Studio lub interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="6855f-161">You'll want to add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="6855f-162">Napraw generowanie informacji o zestawie</span><span class="sxs-lookup"><span data-stu-id="6855f-162">Fix assembly info generation</span></span>

<span data-ttu-id="6855f-163">Windows Forms projekty, które zostały utworzone za pomocą .NET Framework `AssemblyInfo.cs` obejmują plik, który zawiera atrybuty zestawu, takie jak wersja zestawu do wygenerowania.</span><span class="sxs-lookup"><span data-stu-id="6855f-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="6855f-164">Projekty w stylu zestawu SDK automatycznie generują te informacje na podstawie pliku projektu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="6855f-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="6855f-165">W przypadku obu typów "informacje o zestawie" powstaje konflikt.</span><span class="sxs-lookup"><span data-stu-id="6855f-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="6855f-166">Rozwiąż ten problem, wyłączając automatyczne generowanie, co wymusza, aby projekt korzystał `AssemblyInfo.cs` z istniejącego pliku.</span><span class="sxs-lookup"><span data-stu-id="6855f-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="6855f-167">Istnieją trzy ustawienia do dodania do węzła głównego `<PropertyGroup>` .</span><span class="sxs-lookup"><span data-stu-id="6855f-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="6855f-168">**GenerateAssemblyInfo**</span><span class="sxs-lookup"><span data-stu-id="6855f-168">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="6855f-169">Ustawienie tej właściwości na `false`, nie spowoduje wygenerowanie atrybutów zestawu.</span><span class="sxs-lookup"><span data-stu-id="6855f-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="6855f-170">Pozwala to uniknąć konfliktu z istniejącym `AssemblyInfo.cs` plikiem z projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6855f-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="6855f-171">**AssemblyName**</span><span class="sxs-lookup"><span data-stu-id="6855f-171">**AssemblyName**</span></span>\
<span data-ttu-id="6855f-172">Wartością tej właściwości jest wyjściowy plik binarny tworzony podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="6855f-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="6855f-173">Nazwa nie wymaga dodanego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="6855f-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="6855f-174">Na przykład przy użyciu `MyCoreApp` polecenia `MyCoreApp.exe`Generuj.</span><span class="sxs-lookup"><span data-stu-id="6855f-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="6855f-175">**RootNamespace**</span><span class="sxs-lookup"><span data-stu-id="6855f-175">**RootNamespace**</span></span>\
<span data-ttu-id="6855f-176">Domyślna przestrzeń nazw używana przez projekt.</span><span class="sxs-lookup"><span data-stu-id="6855f-176">The default namespace used by your project.</span></span> <span data-ttu-id="6855f-177">Powinna być zgodna z domyślną przestrzenią nazw projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6855f-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="6855f-178">Dodaj te trzy elementy do `<PropertyGroup>` węzła `MyFormsCore.csproj` w pliku:</span><span class="sxs-lookup"><span data-stu-id="6855f-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="6855f-179">Dodaj kod źródłowy</span><span class="sxs-lookup"><span data-stu-id="6855f-179">Add source code</span></span>

<span data-ttu-id="6855f-180">Teraz projekt **MyFormsCore. csproj** nie kompiluje żadnego kodu.</span><span class="sxs-lookup"><span data-stu-id="6855f-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="6855f-181">Domyślnie projekty platformy .NET Core automatycznie uwzględniają cały kod źródłowy w bieżącym katalogu i wszystkich katalogach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="6855f-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="6855f-182">Należy skonfigurować projekt do dołączania kodu z projektu .NET Framework przy użyciu ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="6855f-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="6855f-183">Jeśli projekt .NET Framework używał plików **resx** dla ikon i zasobów formularzy, należy uwzględnić te pliki.</span><span class="sxs-lookup"><span data-stu-id="6855f-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span> 

<span data-ttu-id="6855f-184">Dodaj następujący `<ItemGroup>` węzeł do projektu.</span><span class="sxs-lookup"><span data-stu-id="6855f-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="6855f-185">Każda instrukcja zawiera wzorzec globalizowania pliku, który zawiera katalogi podrzędne.</span><span class="sxs-lookup"><span data-stu-id="6855f-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="6855f-186">Alternatywnie można utworzyć `<Compile>` wpis lub `<EmbeddedResource>` dla każdego pliku w projekcie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6855f-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="6855f-187">Dodaj pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="6855f-187">Add NuGet packages</span></span>

<span data-ttu-id="6855f-188">Dodaj każdy pakiet NuGet, do którego odwołuje się projekt .NET Framework, do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6855f-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="6855f-189">Prawdopodobnie aplikacja Windows Forms .NET Framework ma plik Packages **. config** zawierający listę wszystkich pakietów NuGet, do których odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="6855f-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="6855f-190">Możesz zapoznać się z tą listą, aby określić, które pakiety NuGet dodać do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6855f-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="6855f-191">Na przykład jeśli projekt .NET Framework, do `MetroFramework`którego odwołuje się pakiety `MetroFramework.Fonts` , `MetroFramework.Design`i NuGet, należy dodać każdy do projektu z Visual Studio lub interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="6855f-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="6855f-192">Poprzednie polecenia spowodują dodanie następujących odwołań NuGet do projektu **MyFormsCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="6855f-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="6855f-193">Biblioteki kontrolek portu</span><span class="sxs-lookup"><span data-stu-id="6855f-193">Port control libraries</span></span>

<span data-ttu-id="6855f-194">Jeśli masz projekt biblioteki formantów Windows Forms do portu, kierunki są takie same jak w przypadku portów .NET Framework projektu aplikacji Windows Forms, z wyjątkiem kilku ustawień.</span><span class="sxs-lookup"><span data-stu-id="6855f-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="6855f-195">I zamiast kompilowania do pliku wykonywalnego, należy skompilować do biblioteki.</span><span class="sxs-lookup"><span data-stu-id="6855f-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="6855f-196">Różnica między projektem wykonywalnym i projektem biblioteki, oprócz ścieżki dla pliku elementy globalne, który zawiera kod źródłowy, jest minimalna.</span><span class="sxs-lookup"><span data-stu-id="6855f-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="6855f-197">Korzystając z przykładu poprzedniego kroku, program umożliwia rozwinięcie projektów i plików, z którymi pracujemy.</span><span class="sxs-lookup"><span data-stu-id="6855f-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="6855f-198">Plik</span><span class="sxs-lookup"><span data-stu-id="6855f-198">File</span></span> | <span data-ttu-id="6855f-199">Opis</span><span class="sxs-lookup"><span data-stu-id="6855f-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="6855f-200">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="6855f-200">**MyApps.sln**</span></span> | <span data-ttu-id="6855f-201">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="6855f-201">The name of the solution file.</span></span> |
| <span data-ttu-id="6855f-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="6855f-202">**MyControls.csproj**</span></span> | <span data-ttu-id="6855f-203">Nazwa .NET Framework Windows Forms kontroluje projekt do portu.</span><span class="sxs-lookup"><span data-stu-id="6855f-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="6855f-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="6855f-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="6855f-205">Nazwa nowego projektu biblioteki .NET Core, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="6855f-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="6855f-206">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="6855f-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="6855f-207">Biblioteka formantów Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6855f-207">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="6855f-208">Uwzględnij różnice między `MyControlsCore.csproj` projektem i wcześniej utworzonym `MyFormsCore.csproj` projektem.</span><span class="sxs-lookup"><span data-stu-id="6855f-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="6855f-209">Poniżej znajduje się przykład pliku projektu biblioteki formantów Windows Forms .NET Core:</span><span class="sxs-lookup"><span data-stu-id="6855f-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="6855f-210">Jak widać, `<OutputType>` węzeł został usunięty, który domyślnie kompilator tworzy bibliotekę zamiast pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="6855f-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="6855f-211">`<AssemblyName>` I`<RootNamespace>` zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="6855f-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="6855f-212">W `<RootNamespace>` odróżnieniu od przestrzeni nazw biblioteki formantów Windows Forms, która jest przeprojektowana.</span><span class="sxs-lookup"><span data-stu-id="6855f-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="6855f-213">A wreszcie węzły `<Compile>` i `<EmbeddedResource>` zostały dostosowane tak, aby wskazywały folder bibliotek formantów Windows Forms, które są przełączone.</span><span class="sxs-lookup"><span data-stu-id="6855f-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="6855f-214">Następnie w głównym projekcie programu .NET Core **MyFormsCore. csproj** Dodaj odwołanie do nowej biblioteki formantów Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6855f-214">Next, in the main .NET Core **MyFormsCore.csproj** project add reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="6855f-215">Dodaj odwołanie z programu Visual Studio lub interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="6855f-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="6855f-216">Poprzednie polecenie dodaje następujący do projektu **MyFormsCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="6855f-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="6855f-217">Problemy skompilowane</span><span class="sxs-lookup"><span data-stu-id="6855f-217">Problems compiling</span></span>

<span data-ttu-id="6855f-218">Jeśli masz problemy z kompilowaniem projektów, możesz używać niektórych interfejsów API tylko dla systemu Windows, które są dostępne w .NET Framework ale nie są dostępne w środowisku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6855f-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="6855f-219">Możesz spróbować dodać pakiet NuGet pakietu [zgodności systemu Windows][compat-pack] do projektu.</span><span class="sxs-lookup"><span data-stu-id="6855f-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="6855f-220">Ten pakiet działa tylko w systemie Windows i dodaje około 20 000 interfejsów API systemu Windows do projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="6855f-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="6855f-221">Poprzednie polecenie dodaje następujący do projektu **MyFormsCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="6855f-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="6855f-222">Projektant Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6855f-222">Windows Forms Designer</span></span>

<span data-ttu-id="6855f-223">Zgodnie z opisem w tym artykule program Visual Studio 2019 obsługuje tylko projektanta formularzy w projektach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6855f-223">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="6855f-224">Tworząc równoległy projekt platformy .NET Core, można testować projekt przy użyciu platformy .NET Core podczas projektowania formularzy przy użyciu projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6855f-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="6855f-225">Plik rozwiązania zawiera zarówno projekty .NET Framework, jak i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6855f-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="6855f-226">Dodawanie i projektowanie formularzy i kontrolek w projekcie .NET Framework i opartych na wzorcach globalizowania plików dodanych do projektów .NET Core, wszystkie nowe lub zmienione pliki zostaną automatycznie uwzględnione w projektach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6855f-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="6855f-227">Gdy program Visual Studio 2019 obsługuje Projektant formularzy systemu Windows, można skopiować/wkleić zawartość pliku projektu .NET Core do pliku projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6855f-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="6855f-228">Następnie usuń pliki wzorców globalizowania dodane z `<Source>` elementami i. `<EmbeddedResource>`</span><span class="sxs-lookup"><span data-stu-id="6855f-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="6855f-229">Popraw ścieżki do dowolnych odwołań do projektu używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="6855f-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="6855f-230">Efektywnie uaktualnia projekt .NET Framework do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6855f-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="6855f-231">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="6855f-231">Next steps</span></span>

- <span data-ttu-id="6855f-232">Przeczytaj więcej na temat [pakietu zgodności systemu Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="6855f-232">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="6855f-233">Obejrzyj [film wideo podczas przenoszenia](https://www.youtube.com/watch?v=upVQEUc_KwU) projektu Windows Forms .NET Framework do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6855f-233">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
