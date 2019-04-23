---
title: Port, Windows Forms aplikacji platformy .NET Core 3.0
description: Dowiesz się, jak przenieść aplikację .NET Framework Windows Forms do platformy .NET Core 3.0 dla Windows.
author: Thraka
ms.author: adegeo
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: aebfaa85338e014ca47256b85a1bd6529ad803bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327168"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="ce390-103">Instrukcje: Port aplikacji klasycznych Windows Forms, .NET Core</span><span class="sxs-lookup"><span data-stu-id="ce390-103">How to: Port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="ce390-104">W tym artykule opisano, jak do portu opartego na formularzach Windows aplikacji komputerowej z .NET Framework .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce390-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="ce390-105">Zestaw SDK programu .NET Core 3.0 obsługuje aplikacje Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ce390-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="ce390-106">Formularze Windows jest nadal framework tylko do Windows i działa tylko w Windows.</span><span class="sxs-lookup"><span data-stu-id="ce390-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="ce390-107">W tym przykładzie używa interfejsu wiersza polecenia platformy .NET Core SDK do tworzenia projektu i zarządzania nim.</span><span class="sxs-lookup"><span data-stu-id="ce390-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="ce390-108">W tym artykule różne nazwy są używane do identyfikacji typów plików używany podczas migracji.</span><span class="sxs-lookup"><span data-stu-id="ce390-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="ce390-109">Podczas migracji projektu, pliki będą miały nazwę nadaną inaczej, dlatego umysłowo dopasować je do wymienione poniżej:</span><span class="sxs-lookup"><span data-stu-id="ce390-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="ce390-110">Plik</span><span class="sxs-lookup"><span data-stu-id="ce390-110">File</span></span> | <span data-ttu-id="ce390-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ce390-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="ce390-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="ce390-112">**MyApps.sln**</span></span> | <span data-ttu-id="ce390-113">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ce390-113">The name of the solution file.</span></span> |
| <span data-ttu-id="ce390-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="ce390-114">**MyForms.csproj**</span></span> | <span data-ttu-id="ce390-115">Nazwa projektu .NET Framework Windows Forms do portu.</span><span class="sxs-lookup"><span data-stu-id="ce390-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="ce390-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="ce390-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="ce390-117">Nazwa nowego tworzonego projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce390-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="ce390-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="ce390-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="ce390-119">Pliku wykonywalnego aplikacji .NET Core Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ce390-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="ce390-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ce390-120">Prerequisites</span></span>

- <span data-ttu-id="ce390-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) dla wszelkie prace projektanta, co chcesz zrobić.</span><span class="sxs-lookup"><span data-stu-id="ce390-121">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for any designer work you want to do.</span></span>

  <span data-ttu-id="ce390-122">Zainstaluj następujące obciążenia w programie Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="ce390-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="ce390-123">Programowanie aplikacji klasycznych dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="ce390-123">.NET desktop development</span></span>
  - <span data-ttu-id="ce390-124">Programowanie dla wielu platform na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="ce390-124">.NET cross-platform development</span></span>

- <span data-ttu-id="ce390-125">Praca projekt Windows Forms w rozwiązaniu, który kompiluje i uruchamia bez problemu.</span><span class="sxs-lookup"><span data-stu-id="ce390-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="ce390-126">Projekt musi być kodowane w C#.</span><span class="sxs-lookup"><span data-stu-id="ce390-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="ce390-127">Zainstaluj najnowszą wersję [.NET Core 3.0](https://aka.ms/netcore3download) (wersja zapoznawcza).</span><span class="sxs-lookup"><span data-stu-id="ce390-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>

>[!NOTE]
><span data-ttu-id="ce390-128">**Program Visual Studio 2017** nie obsługuje projektów .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce390-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="ce390-129">**Visual Studio 2019** obsługuje projekty .NET Core 3.0, ale nie obsługuje jeszcze wizualnego projektanta dla projektów .NET Core 3.0 Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ce390-129">**Visual Studio 2019** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="ce390-130">Aby użyć projektanta wizualnego, musi mieć projektu .NET Windows Forms w danym rozwiązaniu, który udostępnia pliki formularzy z projektem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce390-130">To use the visual designer, you must have a .NET Windows Forms project in your solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="ce390-131">Należy wziąć pod uwagę</span><span class="sxs-lookup"><span data-stu-id="ce390-131">Consider</span></span>

<span data-ttu-id="ce390-132">Podczas przenoszenia aplikacji .NET Framework Windows Forms, istnieje kilka rzeczy, które należy wziąć pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="ce390-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="ce390-133">Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.</span><span class="sxs-lookup"><span data-stu-id="ce390-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="ce390-134">Użyj [narzędzia .NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) ustalenie, jeśli projekt będzie migrować do platformy .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce390-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="ce390-135">Jeśli projekt ma problemy z platformy .NET Core 3.0, analizator pomaga zidentyfikować te problemy.</span><span class="sxs-lookup"><span data-stu-id="ce390-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="ce390-136">Używasz innej wersji programu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ce390-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="ce390-137">Po wydaniu była .NET Core 3.0 w wersji zapoznawczej 1, Windows Forms błąd typu open source w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="ce390-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open-source on GitHub.</span></span> <span data-ttu-id="ce390-138">Kod platformy .NET Core Windows Forms jest rozwidlenie bazy kodu platformy .NET Framework Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ce390-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms code base.</span></span> <span data-ttu-id="ce390-139">Istnieje możliwość, istnieją pewne różnice i aplikacja nie będzie portu.</span><span class="sxs-lookup"><span data-stu-id="ce390-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="ce390-140">[Systemie Windows Compatibility Pack] [ compat-pack] mogą pomóc w migracji.</span><span class="sxs-lookup"><span data-stu-id="ce390-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="ce390-141">Niektóre interfejsy API, które są dostępne w programie .NET Framework nie są dostępne w programie .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce390-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="ce390-142">[Systemie Windows Compatibility Pack] [ compat-pack] dodaje wiele z tych interfejsów API i może pomóc w aplikacji Windows Forms stać się zgodny z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce390-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="ce390-143">Aktualizowanie pakietów NuGet, używaną w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ce390-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="ce390-144">Zawsze jest dobrą praktyką jest używanie najnowszych wersji pakietów NuGet przed wykonaniem dowolnej migracji.</span><span class="sxs-lookup"><span data-stu-id="ce390-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="ce390-145">Jeśli aplikacja odwołuje się do żadnych pakietów NuGet, aktualizację do najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="ce390-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="ce390-146">Upewnij się, że Twoja aplikacja pomyślnie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="ce390-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="ce390-147">Po uaktualnieniu, w przypadku błędów pakietu obniżyć wersję pakietu do najnowszej wersji, który nie przerywa działania kodu.</span><span class="sxs-lookup"><span data-stu-id="ce390-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="ce390-148">Visual Studio 2019 nie obsługuje jeszcze projektanta formularzy platformy .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ce390-148">Visual Studio 2019 doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="ce390-149">Obecnie należy zachować istniejący plik projektu programu .NET Framework Windows Forms, jeśli chcesz użyć projektanta formularzy w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ce390-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="ce390-150">Utwórz nowy projekt zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="ce390-150">Create a new SDK project</span></span>

<span data-ttu-id="ce390-151">Nowe tworzonego projektu .NET Core 3.0 to musi być w innym katalogu z projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce390-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="ce390-152">Jeśli są one w tym samym katalogu, mogą występować konflikty z plikami, które są generowane w **obj** katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce390-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="ce390-153">W tym przykładzie utworzymy katalog o nazwie **MyFormsAppCore** w **SolutionFolder** katalogu:</span><span class="sxs-lookup"><span data-stu-id="ce390-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="ce390-154">Następnie należy utworzyć **MyFormsCore.csproj** projektu w **MyFormsAppCore** katalogu.</span><span class="sxs-lookup"><span data-stu-id="ce390-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="ce390-155">Można utworzyć ten plik ręcznie przy użyciu tekstu wybranym edytorze.</span><span class="sxs-lookup"><span data-stu-id="ce390-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="ce390-156">Wklej następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="ce390-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="ce390-157">Jeśli nie chcesz ręcznie utworzyć plik projektu, można użyć programu Visual Studio lub zestawu .NET Core SDK do generowania projektu.</span><span class="sxs-lookup"><span data-stu-id="ce390-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="ce390-158">Jednakże należy usunąć wszystkie inne pliki generowane przez szablon projektu, z wyjątkiem pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ce390-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="ce390-159">Aby użyć zestawu SDK, uruchom następujące polecenie z **SolutionFolder** katalogu:</span><span class="sxs-lookup"><span data-stu-id="ce390-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="ce390-160">Po utworzeniu **MyFormsCore.csproj**, strukturę katalogu powinien wyglądać podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="ce390-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="ce390-161">Będziesz chciał dodać **MyFormsCore.csproj** projekt **MyApps.sln** za pomocą programu Visual Studio lub platformy .NET Core interfejsu wiersza polecenia z **SolutionFolder** katalogu:</span><span class="sxs-lookup"><span data-stu-id="ce390-161">You'll want to add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="ce390-162">Generowanie informacji zestawu poprawki</span><span class="sxs-lookup"><span data-stu-id="ce390-162">Fix assembly info generation</span></span>

<span data-ttu-id="ce390-163">Obejmują projekty Windows Forms, które zostały utworzone za pomocą .NET Framework `AssemblyInfo.cs` pliku, który zawiera zestaw atrybutów, takich jak wersja zestawu do wygenerowania.</span><span class="sxs-lookup"><span data-stu-id="ce390-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="ce390-164">Projektów w stylu zestaw SDK automatycznie generować te informacje w oparciu o plik projektu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="ce390-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="ce390-165">Posiadanie oba rodzaje "informacje o zestawie" spowoduje konflikt.</span><span class="sxs-lookup"><span data-stu-id="ce390-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="ce390-166">Rozwiązać ten problem, wyłączając automatyczne generowanie, co zmusza projekt, aby używać istniejącej `AssemblyInfo.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="ce390-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="ce390-167">Dostępne są trzy ustawienia, aby dodać do głównego `<PropertyGroup>` węzła.</span><span class="sxs-lookup"><span data-stu-id="ce390-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="ce390-168">**GenerateAssemblyInfo**\\</span><span class="sxs-lookup"><span data-stu-id="ce390-168">**GenerateAssemblyInfo**\\</span></span>
<span data-ttu-id="ce390-169">Po ustawieniu wartości tej właściwości na `false`, nie będzie ona Generowanie atrybutów zestawu.</span><span class="sxs-lookup"><span data-stu-id="ce390-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="ce390-170">Pozwala to uniknąć konfliktu z istniejącym `AssemblyInfo.cs` pliku z projektem .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce390-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="ce390-171">**AssemblyName**\\</span><span class="sxs-lookup"><span data-stu-id="ce390-171">**AssemblyName**\\</span></span>
<span data-ttu-id="ce390-172">Wartość tej właściwości jest wynikowy plik binarny utworzony podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="ce390-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="ce390-173">Nazwa nie musi rozszerzenie dodawanych do niego.</span><span class="sxs-lookup"><span data-stu-id="ce390-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="ce390-174">Na przykład za pomocą `MyCoreApp` tworzy `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="ce390-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="ce390-175">**RootNamespace**\\</span><span class="sxs-lookup"><span data-stu-id="ce390-175">**RootNamespace**\\</span></span>
<span data-ttu-id="ce390-176">Domyślna przestrzeń nazw używaną w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ce390-176">The default namespace used by your project.</span></span> <span data-ttu-id="ce390-177">Powinien on odpowiadać domyślny obszar nazw projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce390-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="ce390-178">Te trzy elementy, aby dodać `<PropertyGroup>` w węźle `MyFormsCore.csproj` pliku:</span><span class="sxs-lookup"><span data-stu-id="ce390-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="ce390-179">Dodawanie kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="ce390-179">Add source code</span></span>

<span data-ttu-id="ce390-180">Od razu **MyFormsCore.csproj** projektu nie skompilować jakiegokolwiek kodu.</span><span class="sxs-lookup"><span data-stu-id="ce390-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="ce390-181">Domyślnie projekty .NET Core automatycznie uwzględnia całego kodu źródłowego w bieżącym katalogu i katalogi podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="ce390-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="ce390-182">Należy skonfigurować projekt, aby dołączyć kod z projektu .NET Framework za pomocą ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="ce390-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="ce390-183">Jeśli używany projekt .NET Framework **resx** pliki ikon i zasoby dotyczące formularzy, należy włączyć te zbyt.</span><span class="sxs-lookup"><span data-stu-id="ce390-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span> 

<span data-ttu-id="ce390-184">Dodaj następujący kod `<ItemGroup>` węzła do projektu.</span><span class="sxs-lookup"><span data-stu-id="ce390-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="ce390-185">Każda instrukcja zawiera wzorzec glob pliku, która obejmuje katalogach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="ce390-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="ce390-186">Alternatywnie można utworzyć `<Compile>` lub `<EmbeddedResource>` wpis dla każdego pliku w projekcie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce390-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="ce390-187">Dodawanie pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="ce390-187">Add NuGet packages</span></span>

<span data-ttu-id="ce390-188">Dodaj pakiet NuGet, każdy przywoływanego przez projekt programu .NET Framework do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce390-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="ce390-189">Prawdopodobnie ma aplikacji .NET Framework Windows Forms **packages.config** pliku, który zawiera listę wszystkich pakietów NuGet, które są przywoływane przez projekt.</span><span class="sxs-lookup"><span data-stu-id="ce390-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="ce390-190">Zapoznanie się z tą listą, aby określić, które pakiety NuGet, aby dodać do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce390-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="ce390-191">Na przykład, jeśli projekt programu .NET Framework wywoływane `MetroFramework`, `MetroFramework.Design`, i `MetroFramework.Fonts` pakietów NuGet, Dodaj do projektu przy użyciu programu Visual Studio lub platformy .NET Core interfejsu wiersza polecenia z **SolutionFolder** katalogu :</span><span class="sxs-lookup"><span data-stu-id="ce390-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="ce390-192">Poprzednie polecenia dodać następujące odwołania NuGet do **MyFormsCore.csproj** projektu:</span><span class="sxs-lookup"><span data-stu-id="ce390-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="ce390-193">Port bibliotek kontrolek</span><span class="sxs-lookup"><span data-stu-id="ce390-193">Port control libraries</span></span>

<span data-ttu-id="ce390-194">Jeśli masz Projekt Biblioteka kontrolek formularzy Windows Forms do portu podane są takie same jak eksportowanie projektu aplikacji platformy .NET Framework Windows Forms, z wyjątkiem kilku ustawień.</span><span class="sxs-lookup"><span data-stu-id="ce390-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="ce390-195">I zamiast kompilacji do pliku wykonywalnego, skompiluj bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="ce390-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="ce390-196">Różnica między projekt wykonywalny i projekt biblioteki, oprócz ścieżki dla pliku elementy globalne, które zawierają kod źródłowy, jest minimalny.</span><span class="sxs-lookup"><span data-stu-id="ce390-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="ce390-197">Przy użyciu przykładu w poprzednim kroku, informuje o tym, jakie projektów i plików pracujemy nad.</span><span class="sxs-lookup"><span data-stu-id="ce390-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="ce390-198">Plik</span><span class="sxs-lookup"><span data-stu-id="ce390-198">File</span></span> | <span data-ttu-id="ce390-199">Opis</span><span class="sxs-lookup"><span data-stu-id="ce390-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="ce390-200">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="ce390-200">**MyApps.sln**</span></span> | <span data-ttu-id="ce390-201">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ce390-201">The name of the solution file.</span></span> |
| <span data-ttu-id="ce390-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="ce390-202">**MyControls.csproj**</span></span> | <span data-ttu-id="ce390-203">Nazwa projektu formantów formularzy Windows Framework .NET do portu.</span><span class="sxs-lookup"><span data-stu-id="ce390-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="ce390-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="ce390-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="ce390-205">Nazwa nowego projektu platformy .NET Core w bibliotece tworzenia.</span><span class="sxs-lookup"><span data-stu-id="ce390-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="ce390-206">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="ce390-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="ce390-207">Biblioteka formantów formularzy programu .NET Core Windows.</span><span class="sxs-lookup"><span data-stu-id="ce390-207">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="ce390-208">Należy wziąć pod uwagę różnice między `MyControlsCore.csproj` projektu oraz utworzoną wcześniej `MyFormsCore.csproj` projektu.</span><span class="sxs-lookup"><span data-stu-id="ce390-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="ce390-209">Oto przykład jak będzie wyglądać plik projektu Biblioteka formantów formularzy programu .NET Core Windows:</span><span class="sxs-lookup"><span data-stu-id="ce390-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="ce390-210">Jak widać, `<OutputType>` węzeł został usunięty, które domyślnie używa kompilator generuje bibliotekę zamiast pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="ce390-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="ce390-211">`<AssemblyName>` i `<RootNamespace>` zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="ce390-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="ce390-212">W szczególności `<RootNamespace>` powinien być zgodny z przestrzeni nazw są przenoszenie biblioteki kontrolek formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ce390-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="ce390-213">I wreszcie `<Compile>` i `<EmbeddedResource>` węzły zostały dostosowane by wskazywał folder Biblioteka kontrolek formularzy Windows Forms, to przenoszenie.</span><span class="sxs-lookup"><span data-stu-id="ce390-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="ce390-214">Następnie na główne platformy .NET Core **MyFormsCore.csproj** projektu Dodaj odwołanie do nowej biblioteki .NET Core Windows Forms kontroli.</span><span class="sxs-lookup"><span data-stu-id="ce390-214">Next, in the main .NET Core **MyFormsCore.csproj** project add reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="ce390-215">Dodaj odwołanie za pomocą programu Visual Studio lub platformy .NET Core interfejsu wiersza polecenia z **SolutionFolder** katalogu:</span><span class="sxs-lookup"><span data-stu-id="ce390-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="ce390-216">Poprzednie polecenie dodaje następujące polecenie, aby **MyFormsCore.csproj** projektu:</span><span class="sxs-lookup"><span data-stu-id="ce390-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="ce390-217">Problemy z kompilacji</span><span class="sxs-lookup"><span data-stu-id="ce390-217">Problems compiling</span></span>

<span data-ttu-id="ce390-218">Jeśli masz problemy z kompilowanie projektów, może być używany niektóre Windows — tylko do interfejsów API, które są dostępne w programie .NET Framework, ale nie jest dostępna w .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce390-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="ce390-219">Możesz spróbować dodać [systemie Windows Compatibility Pack] [ compat-pack] pakiet NuGet do projektu.</span><span class="sxs-lookup"><span data-stu-id="ce390-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="ce390-220">Ten pakiet tylko działa na Windows i dodaje około 20 000 Windows interfejsów API do projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ce390-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="ce390-221">Poprzednie polecenie dodaje następujące polecenie, aby **MyFormsCore.csproj** projektu:</span><span class="sxs-lookup"><span data-stu-id="ce390-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="ce390-222">Projektant Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce390-222">Windows Forms Designer</span></span>

<span data-ttu-id="ce390-223">Zgodnie z opisem w tym artykule Visual Studio 2019 obsługuje Projektant formularzy czy tylko w projektach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce390-223">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="ce390-224">Tworząc projekt .NET Core side-by-side, można przetestować projektu na platformie .NET Core, podczas korzystania z projektu .NET Framework do projektowania formularzy.</span><span class="sxs-lookup"><span data-stu-id="ce390-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="ce390-225">Plik rozwiązania zawiera projekty .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce390-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="ce390-226">Dodaj projekt formularzy i kontrolek w projekcie .NET Framework i wzorce glob pliku dodaliśmy do projektów .NET Core i wszelkich nowych lub zmienionych plików zostaną automatycznie uwzględnione w projektach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce390-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="ce390-227">Po 2019 usługi Visual Studio obsługuje Windows Forms Designer, możesz skopiować lub wkleić zawartość pliku projektu .NET Core do pliku projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce390-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="ce390-228">Następnie usuń wzorce glob plików, które są dodawane przy użyciu `<Source>` i `<EmbeddedResource>` elementów.</span><span class="sxs-lookup"><span data-stu-id="ce390-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="ce390-229">Napraw ścieżki do dowolnego odwołania projektu do używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="ce390-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="ce390-230">Projekt programu .NET Framework to skutecznie uaktualniania do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce390-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="ce390-231">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ce390-231">Next steps</span></span>

* <span data-ttu-id="ce390-232">Przeczytaj więcej na temat [systemie Windows Compatibility Pack][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="ce390-232">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
* <span data-ttu-id="ce390-233">Obejrzyj [wideo na przenoszenie](https://www.youtube.com/watch?v=upVQEUc_KwU) projekt formularzy Windows programu .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce390-233">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
