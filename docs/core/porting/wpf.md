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
# <a name="how-to-port-a-wpf-desktop-app-to-net-core"></a><span data-ttu-id="4b408-103">Instrukcje: Port aplikacji klasycznej WPF i .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b408-103">How to: Port a WPF desktop app to .NET Core</span></span>

<span data-ttu-id="4b408-104">W tym artykule opisano, jak do portu oparte na Windows Presentation Foundation (WPF) aplikacji komputerowej z .NET Framework .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="4b408-104">This article describes how to port your Windows Presentation Foundation-based (WPF) desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="4b408-105">Zestaw SDK programu .NET Core 3.0 zawiera obsługę aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="4b408-105">The .NET Core 3.0 SDK includes support for WPF applications.</span></span> <span data-ttu-id="4b408-106">WPF nadal framework tylko do Windows i działa tylko w Windows.</span><span class="sxs-lookup"><span data-stu-id="4b408-106">WPF is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="4b408-107">W tym przykładzie używa interfejsu wiersza polecenia platformy .NET Core SDK do tworzenia projektu i zarządzania nim.</span><span class="sxs-lookup"><span data-stu-id="4b408-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="4b408-108">W tym artykule różne nazwy są używane do identyfikacji typów plików używany podczas migracji.</span><span class="sxs-lookup"><span data-stu-id="4b408-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="4b408-109">Podczas migracji projektu, pliki będą miały nazwę nadaną inaczej, dlatego umysłowo dopasować je do wymienione poniżej:</span><span class="sxs-lookup"><span data-stu-id="4b408-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="4b408-110">Plik</span><span class="sxs-lookup"><span data-stu-id="4b408-110">File</span></span> | <span data-ttu-id="4b408-111">Opis</span><span class="sxs-lookup"><span data-stu-id="4b408-111">Description</span></span> |
| ---- | ----------- |
| **<span data-ttu-id="4b408-112">MyApps.sln</span><span class="sxs-lookup"><span data-stu-id="4b408-112">MyApps.sln</span></span>** | <span data-ttu-id="4b408-113">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4b408-113">The name of the solution file.</span></span> |
| **<span data-ttu-id="4b408-114">MyWPF.csproj</span><span class="sxs-lookup"><span data-stu-id="4b408-114">MyWPF.csproj</span></span>** | <span data-ttu-id="4b408-115">Nazwa projektu .NET Framework WPF do portu.</span><span class="sxs-lookup"><span data-stu-id="4b408-115">The name of the .NET Framework WPF project to port.</span></span> |
| **<span data-ttu-id="4b408-116">MyWPFCore.csproj</span><span class="sxs-lookup"><span data-stu-id="4b408-116">MyWPFCore.csproj</span></span>** | <span data-ttu-id="4b408-117">Nazwa nowego tworzonego projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b408-117">The name of the new .NET Core project you create.</span></span> |
| **<span data-ttu-id="4b408-118">MyAppCore.exe</span><span class="sxs-lookup"><span data-stu-id="4b408-118">MyAppCore.exe</span></span>** | <span data-ttu-id="4b408-119">Pliku wykonywalnego aplikacji .NET Core WPF.</span><span class="sxs-lookup"><span data-stu-id="4b408-119">The .NET Core WPF app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="4b408-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="4b408-120">Prerequisites</span></span>

- <span data-ttu-id="4b408-121">[Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=wpf+core) dla wszelkie prace projektanta, co chcesz zrobić.</span><span class="sxs-lookup"><span data-stu-id="4b408-121">[Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=wpf+core) for any designer work you want to do.</span></span>

  <span data-ttu-id="4b408-122">Zainstaluj następujące obciążenia w programie Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="4b408-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="4b408-123">Programowanie aplikacji klasycznych dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="4b408-123">.NET desktop development</span></span>
  - <span data-ttu-id="4b408-124">Programowanie dla wielu platform na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="4b408-124">.NET cross-platform development</span></span>

- <span data-ttu-id="4b408-125">Projekt WPF pracy w rozwiązaniu, który kompiluje i uruchamia bez problemu.</span><span class="sxs-lookup"><span data-stu-id="4b408-125">A working WPF project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="4b408-126">Projekt musi być kodowane w C#.</span><span class="sxs-lookup"><span data-stu-id="4b408-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="4b408-127">Zainstaluj najnowszą wersję [.NET Core 3.0](https://aka.ms/netcore3download) (wersja zapoznawcza).</span><span class="sxs-lookup"><span data-stu-id="4b408-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="4b408-128">**Program Visual Studio 2017** nie obsługuje projektów .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="4b408-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="4b408-129">**Program Visual Studio 2019 r w wersji zapoznawczej/RC** obsługuje projekty .NET Core 3.0, ale nie obsługuje jeszcze wizualnego projektanta dla projektów .NET Core 3.0 WPF.</span><span class="sxs-lookup"><span data-stu-id="4b408-129">**Visual Studio 2019 Preview/RC** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 WPF projects.</span></span> <span data-ttu-id="4b408-130">Aby użyć projektanta wizualnego, musi mieć projekt .NET WPF w danym rozwiązaniu, który udostępnia swoje pliki z projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b408-130">To use the visual designer, you must have a .NET WPF project in your solution that shares its files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="4b408-131">Należy wziąć pod uwagę</span><span class="sxs-lookup"><span data-stu-id="4b408-131">Consider</span></span>

<span data-ttu-id="4b408-132">Podczas przenoszenia aplikacji .NET Framework WPF, istnieje kilka rzeczy, które należy wziąć pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="4b408-132">When porting a .NET Framework WPF application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="4b408-133">Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.</span><span class="sxs-lookup"><span data-stu-id="4b408-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="4b408-134">Użyj [narzędzia .NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) ustalenie, jeśli projekt będzie migrować do platformy .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="4b408-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="4b408-135">Jeśli projekt ma problemy z platformy .NET Core 3.0, analizator pomaga zidentyfikować te problemy.</span><span class="sxs-lookup"><span data-stu-id="4b408-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="4b408-136">Używasz innej wersji programu WPF.</span><span class="sxs-lookup"><span data-stu-id="4b408-136">You're using a different version of WPF.</span></span>

    <span data-ttu-id="4b408-137">W przypadku platformy .NET Core 3.0 w wersji zapoznawczej 1 został wydany, WPF błąd typu open source w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="4b408-137">When .NET Core 3.0 Preview 1 was released, WPF went open-source on GitHub.</span></span> <span data-ttu-id="4b408-138">Kod platformy .NET Core WPF jest rozwidlenie bazy kodu platformy .NET Framework WPF.</span><span class="sxs-lookup"><span data-stu-id="4b408-138">The code for .NET Core WPF is a fork of the .NET Framework WPF code base.</span></span> <span data-ttu-id="4b408-139">Istnieje możliwość, istnieją pewne różnice i aplikacja nie będzie portu.</span><span class="sxs-lookup"><span data-stu-id="4b408-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="4b408-140">[Systemie Windows Compatibility Pack] [ compat-pack] mogą pomóc w migracji.</span><span class="sxs-lookup"><span data-stu-id="4b408-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="4b408-141">Niektóre interfejsy API, które są dostępne w programie .NET Framework nie są dostępne w programie .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="4b408-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="4b408-142">[Systemie Windows Compatibility Pack] [ compat-pack] dodaje wiele z tych interfejsów API i może pomóc w aplikacji WPF stać się zgodny z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b408-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your WPF app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="4b408-143">Aktualizowanie pakietów NuGet, używaną w projekcie.</span><span class="sxs-lookup"><span data-stu-id="4b408-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="4b408-144">Zawsze jest dobrą praktyką jest używanie najnowszych wersji pakietów NuGet przed wykonaniem dowolnej migracji.</span><span class="sxs-lookup"><span data-stu-id="4b408-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="4b408-145">Jeśli aplikacja odwołuje się do żadnych pakietów NuGet, aktualizację do najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="4b408-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="4b408-146">Upewnij się, że Twoja aplikacja pomyślnie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="4b408-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="4b408-147">Po uaktualnieniu, w przypadku błędów pakietu obniżyć wersję pakietu do najnowszej wersji, który nie przerywa działania kodu.</span><span class="sxs-lookup"><span data-stu-id="4b408-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="4b408-148">Program Visual Studio 2019 r w wersji zapoznawczej/RC programu .NET Core 3.0 nie obsługuje jeszcze projektanta WPF</span><span class="sxs-lookup"><span data-stu-id="4b408-148">Visual Studio 2019 Preview/RC doesn't yet support the WPF Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="4b408-149">Obecnie należy zachować istniejący plik projektu programu .NET Framework WPF, jeśli chcesz użyć projektanta WPF w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4b408-149">Currently, you need to keep your existing .NET Framework WPF project file if you want to use the WPF Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="4b408-150">Utwórz nowy projekt zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="4b408-150">Create a new SDK project</span></span>

<span data-ttu-id="4b408-151">Nowe tworzonego projektu .NET Core 3.0 to musi być w innym katalogu z projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b408-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="4b408-152">Jeśli są one w tym samym katalogu, mogą występować konflikty z plikami, które są generowane w **obj** katalogu.</span><span class="sxs-lookup"><span data-stu-id="4b408-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="4b408-153">W tym przykładzie utworzysz katalog o nazwie **MyWPFAppCore** w **SolutionFolder** katalogu:</span><span class="sxs-lookup"><span data-stu-id="4b408-153">In this example, you'll create a directory named **MyWPFAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore      <--- New folder for core project
```

<span data-ttu-id="4b408-154">Następnie należy utworzyć **MyWPFCore.csproj** projektu w **MyWPFAppCore** katalogu.</span><span class="sxs-lookup"><span data-stu-id="4b408-154">Next, you need to create the **MyWPFCore.csproj** project in the **MyWPFAppCore** directory.</span></span> <span data-ttu-id="4b408-155">Można utworzyć ten plik ręcznie przy użyciu tekstu wybranym edytorze.</span><span class="sxs-lookup"><span data-stu-id="4b408-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="4b408-156">Wklej następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="4b408-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="4b408-157">Jeśli nie chcesz ręcznie utworzyć plik projektu, można użyć programu Visual Studio lub zestawu .NET Core SDK do generowania projektu.</span><span class="sxs-lookup"><span data-stu-id="4b408-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="4b408-158">Jednakże należy usunąć wszystkie inne pliki generowane przez szablon projektu, z wyjątkiem pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="4b408-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="4b408-159">Aby użyć zestawu SDK, uruchom następujące polecenie z **SolutionFolder** katalogu:</span><span class="sxs-lookup"><span data-stu-id="4b408-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new wpf -o MyWPFAppCore -n MyWPFCore
```

<span data-ttu-id="4b408-160">Po utworzeniu **MyWPFCore.csproj**, strukturę katalogu powinien wyglądać podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="4b408-160">After you create the **MyWPFCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyWPFApp
│   └───MyWPF.csproj
└───MyWPFAppCore
    └───MyWPFCore.csproj
```

<span data-ttu-id="4b408-161">Będziesz chciał dodać **MyWPFCore.csproj** projekt **MyApps.sln** za pomocą programu Visual Studio lub platformy .NET Core interfejsu wiersza polecenia z **SolutionFolder** katalogu:</span><span class="sxs-lookup"><span data-stu-id="4b408-161">You'll want to add the **MyWPFCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyWPFAppCore\MyWPFCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="4b408-162">Generowanie informacji zestawu poprawki</span><span class="sxs-lookup"><span data-stu-id="4b408-162">Fix assembly info generation</span></span>

<span data-ttu-id="4b408-163">Projekty Windows Presentation Foundation, które zostały utworzone za pomocą .NET Framework obejmują `AssemblyInfo.cs` pliku, który zawiera zestaw atrybutów, takich jak wersja zestawu do wygenerowania.</span><span class="sxs-lookup"><span data-stu-id="4b408-163">Windows Presentation Foundation projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="4b408-164">Projektów w stylu zestaw SDK automatycznie generować te informacje w oparciu o plik projektu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="4b408-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="4b408-165">Posiadanie oba rodzaje "informacje o zestawie" spowoduje konflikt.</span><span class="sxs-lookup"><span data-stu-id="4b408-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="4b408-166">Rozwiązać ten problem, wyłączając automatyczne generowanie, co zmusza projekt, aby używać istniejącej `AssemblyInfo.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="4b408-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="4b408-167">Dostępne są trzy ustawienia, aby dodać do głównego `<PropertyGroup>` węzła.</span><span class="sxs-lookup"><span data-stu-id="4b408-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- **<span data-ttu-id="4b408-168">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="4b408-168">GenerateAssemblyInfo</span></span>**\
<span data-ttu-id="4b408-169">Po ustawieniu wartości tej właściwości na `false`, nie będzie ona Generowanie atrybutów zestawu.</span><span class="sxs-lookup"><span data-stu-id="4b408-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="4b408-170">Pozwala to uniknąć konfliktu z istniejącym `AssemblyInfo.cs` pliku z projektem .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b408-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- **<span data-ttu-id="4b408-171">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="4b408-171">AssemblyName</span></span>**\
<span data-ttu-id="4b408-172">Wartość tej właściwości jest wynikowy plik binarny utworzony podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="4b408-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="4b408-173">Nazwa nie musi rozszerzenie dodawanych do niego.</span><span class="sxs-lookup"><span data-stu-id="4b408-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="4b408-174">Na przykład za pomocą `MyCoreApp` tworzy `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="4b408-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- **<span data-ttu-id="4b408-175">RootNamespace</span><span class="sxs-lookup"><span data-stu-id="4b408-175">RootNamespace</span></span>**\
<span data-ttu-id="4b408-176">Domyślna przestrzeń nazw używaną w projekcie.</span><span class="sxs-lookup"><span data-stu-id="4b408-176">The default namespace used by your project.</span></span> <span data-ttu-id="4b408-177">Powinien on odpowiadać domyślny obszar nazw projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b408-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="4b408-178">Te trzy elementy, aby dodać `<PropertyGroup>` w węźle `MyWPFCore.csproj` pliku:</span><span class="sxs-lookup"><span data-stu-id="4b408-178">Add these three elements to the `<PropertyGroup>` node in the `MyWPFCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="4b408-179">Dodawanie kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="4b408-179">Add source code</span></span>
<span data-ttu-id="4b408-180">Od razu **MyWPFCore.csproj** projektu nie skompilować jakiegokolwiek kodu.</span><span class="sxs-lookup"><span data-stu-id="4b408-180">Right now, the **MyWPFCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="4b408-181">Domyślnie projekty .NET Core automatycznie uwzględnia całego kodu źródłowego w bieżącym katalogu i katalogi podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4b408-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="4b408-182">Należy skonfigurować projekt, aby dołączyć kod z projektu .NET Framework za pomocą ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="4b408-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="4b408-183">Jeśli używany projekt .NET Framework **resx** pliki ikon i zasoby dla systemów windows i kontrolek, należy włączyć te zbyt.</span><span class="sxs-lookup"><span data-stu-id="4b408-183">If your .NET Framework project used **.resx** files for icons and resources for your windows and controls, you'll need to include those too.</span></span> 

<span data-ttu-id="4b408-184">Pierwszy `<ItemGroup>` węzeł należy dodać do projektu **App.xaml** pliku, który reprezentuje konfiguracji uruchamiania i zasoby używany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="4b408-184">The first `<ItemGroup>` node you need to add to your project includes the **App.xaml** file that represents the startup config and resources your app uses.</span></span> <span data-ttu-id="4b408-185">**App.xaml** plik ma również towarzyszący **App.xaml.cs** plik, ale zostaną automatycznie uwzględnione w innej `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="4b408-185">The **App.xaml** file also has an accompanying **App.xaml.cs** file, but it will be automatically included in a different `<ItemGroup>`.</span></span>

```xml
  <ItemGroup>
    <ApplicationDefinition Include="..\MyWPFApp\App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
  </ItemGroup>
```

<span data-ttu-id="4b408-186">Następnie dodaj następujące `<ItemGroup>` węzła do projektu.</span><span class="sxs-lookup"><span data-stu-id="4b408-186">Next, add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="4b408-187">Każda instrukcja zawiera wzorzec glob pliku, która obejmuje katalogach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="4b408-187">Each statement includes a file glob pattern that includes child directories.</span></span> <span data-ttu-id="4b408-188">Zawiera kod źródłowy dla projektu, wszystkie pliki ustawień i zasobów.</span><span class="sxs-lookup"><span data-stu-id="4b408-188">It includes the source code for your project, any settings files, and any resources.</span></span> <span data-ttu-id="4b408-189">**Obj** katalogu jest jawnie wykluczone.</span><span class="sxs-lookup"><span data-stu-id="4b408-189">The **obj** directory is explicitly excluded.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyWPFApp\**\*.cs" Exclude="..\MyWPFApp\obj\**" />
    <None Include="..\MyWPFApp\**\*.settings" />
    <EmbeddedResource Include="..\MyWPFApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="4b408-190">Następnie uwzględnić innego `<ItemGroup>` węzeł, który zawiera `<Page>` wpis dla każdego **xaml** pliku w projekcie, z wyjątkiem **App.xaml** pliku.</span><span class="sxs-lookup"><span data-stu-id="4b408-190">Next, include another `<ItemGroup>` node that contains a `<Page>` entry for every **xaml** file in your project except the **App.xaml** file.</span></span> <span data-ttu-id="4b408-191">Zawierają one wszystkie systemu windows, strony i zasoby, które znajdują się w **xaml** formatu.</span><span class="sxs-lookup"><span data-stu-id="4b408-191">These contain all of the windows, pages, and resources that are in **xaml** format.</span></span> <span data-ttu-id="4b408-192">Nie można tutaj użyć wzorca globalizowania i należy dodać wpis dla każdego pliku i wskazują `<Generator>` używane.</span><span class="sxs-lookup"><span data-stu-id="4b408-192">You cannot use a glob pattern here and must add an entry for every file and indicate the `<Generator>` used.</span></span>

```xml
  <ItemGroup>
    <Page Include="..\MyWPFApp\MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
  </ItemGroup>
```

## <a name="add-nuget-packages"></a><span data-ttu-id="4b408-193">Dodawanie pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="4b408-193">Add NuGet packages</span></span>

<span data-ttu-id="4b408-194">Dodaj pakiet NuGet, każdy przywoływanego przez projekt programu .NET Framework do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b408-194">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="4b408-195">Prawdopodobnie ma aplikację .NET Framework WPF **packages.config** pliku, który zawiera listę wszystkich pakietów NuGet, które są przywoływane przez projekt.</span><span class="sxs-lookup"><span data-stu-id="4b408-195">Most likely your .NET Framework WPF app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="4b408-196">Zapoznanie się z tą listą, aby określić, które pakiety NuGet, aby dodać do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b408-196">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="4b408-197">Na przykład, jeśli odwołuje się projekt programu .NET Framework `MahApps.Metro` NuGet pakietu, dodaj go do projektu przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4b408-197">For example, if the .NET Framework project references the `MahApps.Metro` NuGet package, add it to the project with Visual Studio.</span></span> <span data-ttu-id="4b408-198">Możesz również dodać odwołanie do pakietu przy użyciu platformy .NET Core interfejsu wiersza polecenia z **SolutionFolder** katalogu:</span><span class="sxs-lookup"><span data-stu-id="4b408-198">You can also add the package reference with the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package MahApps.Metro -v 2.0.0-alpha0262
```

<span data-ttu-id="4b408-199">Poprzednie polecenie dodać następujące odwołanie NuGet do **MyWPFCore.csproj** projektu:</span><span class="sxs-lookup"><span data-stu-id="4b408-199">The previous command would add the following NuGet reference to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MahApps.Metro" Version="2.0.0-alpha0262" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="4b408-200">Problemy z kompilacji</span><span class="sxs-lookup"><span data-stu-id="4b408-200">Problems compiling</span></span>

<span data-ttu-id="4b408-201">Jeśli masz problemy z kompilowanie projektów, może być używany niektóre Windows — tylko do interfejsów API, które są dostępne w programie .NET Framework, ale nie jest dostępna w .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b408-201">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="4b408-202">Możesz spróbować dodać [systemie Windows Compatibility Pack] [ compat-pack] pakiet NuGet do projektu.</span><span class="sxs-lookup"><span data-stu-id="4b408-202">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="4b408-203">Ten pakiet tylko działa na Windows i dodaje około 20 000 Windows interfejsów API do projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4b408-203">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyWPFAppCore\MyWPFCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="4b408-204">Poprzednie polecenie dodaje następujące polecenie, aby **MyWPFCore.csproj** projektu:</span><span class="sxs-lookup"><span data-stu-id="4b408-204">The previous command adds the following to the **MyWPFCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="wpf-designer"></a><span data-ttu-id="4b408-205">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="4b408-205">WPF Designer</span></span>

<span data-ttu-id="4b408-206">Zgodnie z opisem w tym artykule program Visual Studio 2019 r w wersji zapoznawczej/RC obsługuje projektanta WPF tylko w projektach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b408-206">As detailed in this article, Visual Studio 2019 Preview/RC only supports the WPF Designer in .NET Framework projects.</span></span> <span data-ttu-id="4b408-207">Tworząc projekt .NET Core side-by-side, można przetestować projektu na platformie .NET Core, podczas korzystania z projektu .NET Framework do projektowania formularzy.</span><span class="sxs-lookup"><span data-stu-id="4b408-207">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="4b408-208">Plik rozwiązania zawiera projekty .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b408-208">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="4b408-209">Dodaj projekt formularzy i kontrolek w projekcie .NET Framework i wzorce glob pliku dodaliśmy do projektów .NET Core i wszelkich nowych lub zmienionych plików zostaną automatycznie uwzględnione w projektach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b408-209">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="4b408-210">Gdy program Visual Studio 2019 obsługuje projektanta WPF, można kopiujesz/wklejasz zawartość pliku projektu .NET Core do pliku projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b408-210">Once Visual Studio 2019 supports the WPF Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="4b408-211">Następnie usuń wzorce glob plików, które są dodawane przy użyciu `<Source>` i `<EmbeddedResource>` elementów.</span><span class="sxs-lookup"><span data-stu-id="4b408-211">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="4b408-212">Napraw ścieżki do dowolnego odwołania projektu do używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="4b408-212">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="4b408-213">Projekt programu .NET Framework to skutecznie uaktualniania do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b408-213">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="4b408-214">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="4b408-214">Next steps</span></span>

* <span data-ttu-id="4b408-215">Przeczytaj więcej na temat [systemie Windows Compatibility Pack][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="4b408-215">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
* <span data-ttu-id="4b408-216">Obejrzyj [wideo na przenoszenie](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) projektu .NET Framework WPF i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b408-216">Watch a [video on porting](https://www.youtube.com/watch?v=5MomsgkWkVw&list=PLS__JrkRveTMiWxG-Lv4cBwYfMQ6m2gmt) your .NET Framework WPF project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
