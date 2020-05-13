---
title: Port aplikacji Windows Forms do programu .NET Core
description: Naucz się, w jaki sposób portować .NET Framework aplikację Windows Forms do programu .NET Core dla systemu Windows.
author: Thraka
ms.author: adegeo
ms.date: 01/24/2020
ms.openlocfilehash: efa73428c816eddc00c62c2275d3457c92284388
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206131"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="3f500-103">Jak przenieść aplikację klasyczną Windows Forms na platformę .NET Core</span><span class="sxs-lookup"><span data-stu-id="3f500-103">How to port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="3f500-104">W tym artykule opisano sposób przenoszenia aplikacji klasycznej opartej na Windows Forms z .NET Framework do programu .NET Core 3,0 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="3f500-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0 or later.</span></span> <span data-ttu-id="3f500-105">Zestaw .NET Core 3,0 SDK obejmuje obsługę aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3f500-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="3f500-106">Windows Forms nadal jest strukturą tylko dla systemu Windows i działa tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="3f500-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="3f500-107">W tym przykładzie jest używany interfejs wiersza polecenia zestaw .NET Core SDK do tworzenia projektu i zarządzania nim.</span><span class="sxs-lookup"><span data-stu-id="3f500-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="3f500-108">W tym artykule różne nazwy są używane do identyfikowania typów plików używanych do migracji.</span><span class="sxs-lookup"><span data-stu-id="3f500-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="3f500-109">Podczas migrowania projektu pliki będą wyglądać inaczej, dlatego można je dopasować do nich w sposób psychiczny do wymienionych poniżej:</span><span class="sxs-lookup"><span data-stu-id="3f500-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="3f500-110">Plik</span><span class="sxs-lookup"><span data-stu-id="3f500-110">File</span></span> | <span data-ttu-id="3f500-111">Opis</span><span class="sxs-lookup"><span data-stu-id="3f500-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="3f500-112">**Moje Apps. sln**</span><span class="sxs-lookup"><span data-stu-id="3f500-112">**MyApps.sln**</span></span> | <span data-ttu-id="3f500-113">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="3f500-113">The name of the solution file.</span></span> |
| <span data-ttu-id="3f500-114">**Moje formy. csproj**</span><span class="sxs-lookup"><span data-stu-id="3f500-114">**MyForms.csproj**</span></span> | <span data-ttu-id="3f500-115">Nazwa .NET Framework Windows Forms projektu do portów.</span><span class="sxs-lookup"><span data-stu-id="3f500-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="3f500-116">**MyFormsCore. csproj**</span><span class="sxs-lookup"><span data-stu-id="3f500-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="3f500-117">Nazwa nowego projektu .NET Core, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="3f500-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="3f500-118">**MyAppCore. exe**</span><span class="sxs-lookup"><span data-stu-id="3f500-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="3f500-119">Plik wykonywalny aplikacji .NET Core Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3f500-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="3f500-120">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="3f500-120">Prerequisites</span></span>

- <span data-ttu-id="3f500-121">[Visual Studio 2019 16,5 (wersja zapoznawcza 1](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&ch=pre&rel=16) lub nowsza) dla dowolnej pracy projektanta, który chcesz wykonać.</span><span class="sxs-lookup"><span data-stu-id="3f500-121">[Visual Studio 2019 16.5 Preview 1](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&ch=pre&rel=16) or later for any designer work you want to do.</span></span> <span data-ttu-id="3f500-122">Zalecamy aktualizację do najnowszej [wersji zapoznawczej programu Visual Studio](https://visualstudio.microsoft.com/vs/preview/).</span><span class="sxs-lookup"><span data-stu-id="3f500-122">We recommend to update to the latest [Preview version of Visual Studio](https://visualstudio.microsoft.com/vs/preview/).</span></span>

  <span data-ttu-id="3f500-123">Zainstaluj następujące obciążenia programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="3f500-123">Install the following Visual Studio workloads:</span></span>
  
  - <span data-ttu-id="3f500-124">Programowanie aplikacji klasycznych dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="3f500-124">.NET desktop development</span></span>
  - <span data-ttu-id="3f500-125">Tworzenie aplikacji dla wielu platform w środowisku .NET Core</span><span class="sxs-lookup"><span data-stu-id="3f500-125">.NET Core cross-platform development</span></span>

- <span data-ttu-id="3f500-126">Projekt działającego Windows Forms w rozwiązaniu, które kompiluje i uruchamia bez problemu.</span><span class="sxs-lookup"><span data-stu-id="3f500-126">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="3f500-127">Projekt kodowany w języku C#.</span><span class="sxs-lookup"><span data-stu-id="3f500-127">A project coded in C#.</span></span>

> [!NOTE]
> <span data-ttu-id="3f500-128">Projekty .NET Core 3,0 są obsługiwane tylko w programie **Visual Studio 2019** lub jego nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="3f500-128">.NET Core 3.0 projects are only supported in **Visual Studio 2019** or a later version.</span></span> <span data-ttu-id="3f500-129">Począwszy od **programu Visual Studio 2019 w wersji 16,5 (wersja zapoznawcza 1**) jest również obsługiwany program .net Core Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="3f500-129">Starting with **Visual Studio 2019 version 16.5 Preview 1**, the .NET Core Windows Forms designer is also supported.</span></span>
>
> <span data-ttu-id="3f500-130">Aby włączyć projektanta, przejdź do opcji **Narzędzia**  >  **Opcje**  >  **środowisko**  >  w**wersji zapoznawczej** i wybierz opcję **Użyj podglądu Windows Forms projektanta dla aplikacji .NET Core** .</span><span class="sxs-lookup"><span data-stu-id="3f500-130">To enable the designer, go to **Tools** > **Options** > **Environment** > **Preview Features** and select the **Use the preview Windows Forms designer for .NET Core apps** option.</span></span>

### <a name="consider"></a><span data-ttu-id="3f500-131">Pod</span><span class="sxs-lookup"><span data-stu-id="3f500-131">Consider</span></span>

<span data-ttu-id="3f500-132">Podczas przenoszenia aplikacji Windows Forms .NET Framework należy wziąć pod uwagę kilka rzeczy.</span><span class="sxs-lookup"><span data-stu-id="3f500-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="3f500-133">Sprawdź, czy aplikacja jest dobrym kandydatem do migracji.</span><span class="sxs-lookup"><span data-stu-id="3f500-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="3f500-134">Użyj [analizatora przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md) , aby określić, czy projekt zostanie zmigrowany do programu .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="3f500-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="3f500-135">Jeśli projekt zawiera problemy z platformą .NET Core 3,0, Analizator pomaga zidentyfikować te problemy.</span><span class="sxs-lookup"><span data-stu-id="3f500-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="3f500-136">Używasz innej wersji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3f500-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="3f500-137">Po wydaniu programu .NET Core 3,0 w wersji zapoznawczej 1 Windows Forms mógł zostać otwartym źródłem w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="3f500-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open source on GitHub.</span></span> <span data-ttu-id="3f500-138">Kod dla Windows Forms .NET Core jest rozwidleniem bazy kodu .NET Framework Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3f500-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms codebase.</span></span> <span data-ttu-id="3f500-139">Istnieją pewne różnice, które nie są dostępne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f500-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="3f500-140">[Pakiet zgodności systemu Windows][compat-pack] może pomóc w migracji.</span><span class="sxs-lookup"><span data-stu-id="3f500-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="3f500-141">Niektóre interfejsy API, które są dostępne w .NET Framework nie są dostępne w programie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="3f500-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="3f500-142">[Pakiet zgodności systemu Windows][compat-pack] dodaje wiele z tych interfejsów API i może pomóc aplikacji Windows Forms być zgodny z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f500-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="3f500-143">Zaktualizuj pakiety NuGet używane przez Twój projekt.</span><span class="sxs-lookup"><span data-stu-id="3f500-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="3f500-144">Zawsze dobrym sposobem jest użycie najnowszych wersji pakietów NuGet przed migracją.</span><span class="sxs-lookup"><span data-stu-id="3f500-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="3f500-145">Jeśli aplikacja odwołuje się do wszystkich pakietów NuGet, zaktualizuj je do najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="3f500-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="3f500-146">Upewnij się, że aplikacja została pomyślnie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="3f500-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="3f500-147">Po uaktualnieniu, jeśli występują jakiekolwiek błędy pakietów, można obniżyć pakiet do najnowszej wersji, która nie powoduje przerwania kodu.</span><span class="sxs-lookup"><span data-stu-id="3f500-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="3f500-148">Utwórz nowy projekt zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="3f500-148">Create a new SDK project</span></span>

<span data-ttu-id="3f500-149">Nowy projekt platformy .NET Core 3,0, który tworzysz, musi znajdować się w innym katalogu niż projekt .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f500-149">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="3f500-150">Jeśli oba te elementy znajdują się w tym samym katalogu, może wystąpić konflikt z plikami, które są generowane w katalogu **obj** .</span><span class="sxs-lookup"><span data-stu-id="3f500-150">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="3f500-151">W tym przykładzie utworzymy katalog o nazwie **MyFormsAppCore** w katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="3f500-151">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="3f500-152">Następnie należy utworzyć projekt **MyFormsCore. csproj** w katalogu **MyFormsAppCore** .</span><span class="sxs-lookup"><span data-stu-id="3f500-152">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="3f500-153">Ten plik można utworzyć ręcznie przy użyciu edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="3f500-153">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="3f500-154">Wklej następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="3f500-154">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="3f500-155">Jeśli nie chcesz tworzyć pliku projektu ręcznie, możesz użyć programu Visual Studio lub zestaw .NET Core SDK do wygenerowania projektu.</span><span class="sxs-lookup"><span data-stu-id="3f500-155">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="3f500-156">Należy jednak usunąć wszystkie inne pliki wygenerowane przez szablon projektu, z wyjątkiem pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="3f500-156">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="3f500-157">Aby użyć zestawu SDK, uruchom następujące polecenie w katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="3f500-157">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="3f500-158">Po utworzeniu **MyFormsCore. csproj**struktura katalogów powinna wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="3f500-158">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="3f500-159">Dodaj projekt **MyFormsCore. csproj** do elementu **webapps. sln** z programem Visual Studio lub interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="3f500-159">Add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="3f500-160">Napraw generowanie informacji o zestawie</span><span class="sxs-lookup"><span data-stu-id="3f500-160">Fix assembly info generation</span></span>

<span data-ttu-id="3f500-161">Windows Forms projekty, które zostały utworzone za pomocą .NET Framework obejmują `AssemblyInfo.cs` plik, który zawiera atrybuty zestawu, takie jak wersja zestawu do wygenerowania.</span><span class="sxs-lookup"><span data-stu-id="3f500-161">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="3f500-162">Projekty w stylu zestawu SDK automatycznie generują te informacje na podstawie pliku projektu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="3f500-162">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="3f500-163">W przypadku obu typów "informacje o zestawie" powstaje konflikt.</span><span class="sxs-lookup"><span data-stu-id="3f500-163">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="3f500-164">Rozwiąż ten problem, wyłączając automatyczne generowanie, co wymusza, aby projekt korzystał z istniejącego `AssemblyInfo.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="3f500-164">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="3f500-165">Istnieją trzy ustawienia do dodania do `<PropertyGroup>` węzła głównego.</span><span class="sxs-lookup"><span data-stu-id="3f500-165">There are three settings to add to the main `<PropertyGroup>` node.</span></span>

- <span data-ttu-id="3f500-166">**GenerateAssemblyInfo**</span><span class="sxs-lookup"><span data-stu-id="3f500-166">**GenerateAssemblyInfo**</span></span>\
<span data-ttu-id="3f500-167">Ustawienie tej właściwości na `false` , nie spowoduje wygenerowanie atrybutów zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f500-167">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="3f500-168">Pozwala to uniknąć konfliktu z istniejącym `AssemblyInfo.cs` plikiem z projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f500-168">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="3f500-169">**AssemblyName**</span><span class="sxs-lookup"><span data-stu-id="3f500-169">**AssemblyName**</span></span>\
<span data-ttu-id="3f500-170">Wartością tej właściwości jest wyjściowy plik binarny tworzony podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="3f500-170">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="3f500-171">Nazwa nie wymaga dodanego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="3f500-171">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="3f500-172">Na przykład przy użyciu polecenia `MyCoreApp` Generuj `MyCoreApp.exe` .</span><span class="sxs-lookup"><span data-stu-id="3f500-172">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="3f500-173">**RootNamespace**</span><span class="sxs-lookup"><span data-stu-id="3f500-173">**RootNamespace**</span></span>\
<span data-ttu-id="3f500-174">Domyślna przestrzeń nazw używana przez projekt.</span><span class="sxs-lookup"><span data-stu-id="3f500-174">The default namespace used by your project.</span></span> <span data-ttu-id="3f500-175">Powinna być zgodna z domyślną przestrzenią nazw projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f500-175">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="3f500-176">Dodaj te trzy elementy do `<PropertyGroup>` węzła w `MyFormsCore.csproj` pliku:</span><span class="sxs-lookup"><span data-stu-id="3f500-176">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

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

## <a name="add-source-code"></a><span data-ttu-id="3f500-177">Dodaj kod źródłowy</span><span class="sxs-lookup"><span data-stu-id="3f500-177">Add source code</span></span>

<span data-ttu-id="3f500-178">Teraz projekt **MyFormsCore. csproj** nie kompiluje żadnego kodu.</span><span class="sxs-lookup"><span data-stu-id="3f500-178">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="3f500-179">Domyślnie projekty platformy .NET Core automatycznie uwzględniają cały kod źródłowy w bieżącym katalogu i wszystkich katalogach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="3f500-179">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="3f500-180">Należy skonfigurować projekt do dołączania kodu z projektu .NET Framework przy użyciu ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="3f500-180">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="3f500-181">Jeśli projekt .NET Framework używał plików **resx** dla ikon i zasobów formularzy, należy uwzględnić te pliki.</span><span class="sxs-lookup"><span data-stu-id="3f500-181">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span>

<span data-ttu-id="3f500-182">Dodaj następujący `<ItemGroup>` węzeł do projektu.</span><span class="sxs-lookup"><span data-stu-id="3f500-182">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="3f500-183">Każda instrukcja zawiera wzorzec globalizowania pliku, który zawiera katalogi podrzędne.</span><span class="sxs-lookup"><span data-stu-id="3f500-183">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="3f500-184">Alternatywnie można utworzyć `<Compile>` `<EmbeddedResource>` wpis lub dla każdego pliku w projekcie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f500-184">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="3f500-185">Dodawanie pakietów NuGet</span><span class="sxs-lookup"><span data-stu-id="3f500-185">Add NuGet packages</span></span>

<span data-ttu-id="3f500-186">Dodaj każdy pakiet NuGet, do którego odwołuje się projekt .NET Framework, do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f500-186">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span>

<span data-ttu-id="3f500-187">Prawdopodobnie aplikacja Windows Forms .NET Framework ma plik **Packages. config** zawierający listę wszystkich pakietów NuGet, do których odwołuje się projekt.</span><span class="sxs-lookup"><span data-stu-id="3f500-187">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="3f500-188">Możesz zapoznać się z tą listą, aby określić, które pakiety NuGet dodać do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f500-188">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="3f500-189">Na przykład jeśli projekt .NET Framework, do którego odwołuje się `MetroFramework` `MetroFramework.Design` pakiety, i `MetroFramework.Fonts` NuGet, należy dodać każdy do projektu z Visual Studio lub interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="3f500-189">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="3f500-190">Poprzednie polecenia spowodują dodanie następujących odwołań NuGet do projektu **MyFormsCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="3f500-190">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="3f500-191">Biblioteki kontrolek portu</span><span class="sxs-lookup"><span data-stu-id="3f500-191">Port control libraries</span></span>

<span data-ttu-id="3f500-192">Jeśli masz projekt biblioteki formantów Windows Forms do portu, kierunki są takie same jak w przypadku portów .NET Framework projektu aplikacji Windows Forms, z wyjątkiem kilku ustawień.</span><span class="sxs-lookup"><span data-stu-id="3f500-192">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="3f500-193">I zamiast kompilowania do pliku wykonywalnego, należy skompilować do biblioteki.</span><span class="sxs-lookup"><span data-stu-id="3f500-193">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="3f500-194">Różnica między projektem wykonywalnym i projektem biblioteki, oprócz ścieżki dla pliku elementy globalne, który zawiera kod źródłowy, jest minimalna.</span><span class="sxs-lookup"><span data-stu-id="3f500-194">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="3f500-195">Korzystając z przykładu poprzedniego kroku, program umożliwia rozwinięcie projektów i plików, z którymi pracujemy.</span><span class="sxs-lookup"><span data-stu-id="3f500-195">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="3f500-196">Plik</span><span class="sxs-lookup"><span data-stu-id="3f500-196">File</span></span> | <span data-ttu-id="3f500-197">Opis</span><span class="sxs-lookup"><span data-stu-id="3f500-197">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="3f500-198">**Moje Apps. sln**</span><span class="sxs-lookup"><span data-stu-id="3f500-198">**MyApps.sln**</span></span> | <span data-ttu-id="3f500-199">Nazwa pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="3f500-199">The name of the solution file.</span></span> |
| <span data-ttu-id="3f500-200">**Kontrolki. csproj**</span><span class="sxs-lookup"><span data-stu-id="3f500-200">**MyControls.csproj**</span></span> | <span data-ttu-id="3f500-201">Nazwa .NET Framework Windows Forms kontroluje projekt do portu.</span><span class="sxs-lookup"><span data-stu-id="3f500-201">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="3f500-202">**MyControlsCore. csproj**</span><span class="sxs-lookup"><span data-stu-id="3f500-202">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="3f500-203">Nazwa nowego projektu biblioteki .NET Core, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="3f500-203">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="3f500-204">**MyCoreControls. dll**</span><span class="sxs-lookup"><span data-stu-id="3f500-204">**MyCoreControls.dll**</span></span> | <span data-ttu-id="3f500-205">Biblioteka formantów Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f500-205">The .NET Core Windows Forms Controls library.</span></span> |

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

<span data-ttu-id="3f500-206">Uwzględnij różnice między `MyControlsCore.csproj` projektem i wcześniej utworzonym `MyFormsCore.csproj` projektem.</span><span class="sxs-lookup"><span data-stu-id="3f500-206">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

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

<span data-ttu-id="3f500-207">Poniżej znajduje się przykład pliku projektu biblioteki formantów Windows Forms .NET Core:</span><span class="sxs-lookup"><span data-stu-id="3f500-207">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

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

<span data-ttu-id="3f500-208">Jak widać, `<OutputType>` węzeł został usunięty, który domyślnie kompilator tworzy bibliotekę zamiast pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="3f500-208">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="3f500-209">`<AssemblyName>`I `<RootNamespace>` zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="3f500-209">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="3f500-210">W `<RootNamespace>` odróżnieniu od przestrzeni nazw biblioteki formantów Windows Forms, która jest przeprojektowana.</span><span class="sxs-lookup"><span data-stu-id="3f500-210">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="3f500-211">A wreszcie `<Compile>` `<EmbeddedResource>` węzły i zostały dostosowane tak, aby wskazywały folder bibliotek formantów Windows Forms, które są przełączone.</span><span class="sxs-lookup"><span data-stu-id="3f500-211">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="3f500-212">Następnie w głównym projekcie programu .NET Core **MyFormsCore. csproj** Dodaj odwołanie do nowej biblioteki formantów Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f500-212">Next, in the main .NET Core **MyFormsCore.csproj** project, add a reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="3f500-213">Dodaj odwołanie z programu Visual Studio lub interfejs wiersza polecenia platformy .NET Core z katalogu **SolutionFolder** :</span><span class="sxs-lookup"><span data-stu-id="3f500-213">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCore.csproj
```

<span data-ttu-id="3f500-214">Poprzednie polecenie dodaje następujący do projektu **MyFormsCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="3f500-214">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCore.csproj" />
  </ItemGroup>
```

## <a name="compilation-problems"></a><span data-ttu-id="3f500-215">Problemy z kompilacją</span><span class="sxs-lookup"><span data-stu-id="3f500-215">Compilation problems</span></span>

<span data-ttu-id="3f500-216">Jeśli masz problemy z kompilowaniem projektów, możesz używać niektórych interfejsów API tylko dla systemu Windows, które są dostępne w .NET Framework ale nie są dostępne w środowisku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f500-216">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="3f500-217">Możesz spróbować dodać pakiet NuGet pakietu [zgodności systemu Windows][compat-pack] do projektu.</span><span class="sxs-lookup"><span data-stu-id="3f500-217">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="3f500-218">Ten pakiet działa tylko w systemie Windows i dodaje około 20 000 interfejsów API systemu Windows do projektów .NET Core i .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3f500-218">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```dotnetcli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="3f500-219">Poprzednie polecenie dodaje następujący do projektu **MyFormsCore. csproj** :</span><span class="sxs-lookup"><span data-stu-id="3f500-219">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="3.1.0" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="3f500-220">Projektant Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3f500-220">Windows Forms Designer</span></span>

<span data-ttu-id="3f500-221">Zgodnie z opisem w tym artykule program Visual Studio 2019 obsługuje tylko projektanta formularzy w projektach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f500-221">As detailed in this article, Visual Studio 2019 only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="3f500-222">Tworząc równoległy projekt platformy .NET Core, można testować projekt przy użyciu platformy .NET Core podczas projektowania formularzy przy użyciu projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f500-222">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="3f500-223">Plik rozwiązania zawiera zarówno projekty .NET Framework, jak i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f500-223">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="3f500-224">Dodawanie i projektowanie formularzy i kontrolek w projekcie .NET Framework i opartych na wzorcach globalizowania plików dodanych do projektów .NET Core, wszystkie nowe lub zmienione pliki zostaną automatycznie uwzględnione w projektach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f500-224">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="3f500-225">Gdy program Visual Studio 2019 obsługuje Projektant formularzy systemu Windows, można skopiować/wkleić zawartość pliku projektu .NET Core do pliku projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3f500-225">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="3f500-226">Następnie usuń pliki wzorców globalizowania dodane z `<Source>` `<EmbeddedResource>` elementami i.</span><span class="sxs-lookup"><span data-stu-id="3f500-226">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="3f500-227">Popraw ścieżki do dowolnych odwołań do projektu używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="3f500-227">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="3f500-228">Efektywnie uaktualnia projekt .NET Framework do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f500-228">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3f500-229">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="3f500-229">Next steps</span></span>

- <span data-ttu-id="3f500-230">Informacje o istotnych [zmianach z .NET Framework na platformę .NET Core](../compatibility/fx-core.md).</span><span class="sxs-lookup"><span data-stu-id="3f500-230">Learn about [breaking changes from .NET Framework to .NET Core](../compatibility/fx-core.md).</span></span>
- <span data-ttu-id="3f500-231">Przeczytaj więcej na temat [pakietu zgodności systemu Windows][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="3f500-231">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
- <span data-ttu-id="3f500-232">Obejrzyj [film wideo podczas przenoszenia](https://www.youtube.com/watch?v=upVQEUc_KwU) projektu Windows Forms .NET Framework do programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3f500-232">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md
