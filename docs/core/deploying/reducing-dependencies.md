---
title: Zmniejszanie zależności pakietów za pomocą projektu.json
description: Zmniejsz zależności pakietów podczas tworzenia bibliotek opartych na programie project.json.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740829"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="c4c92-103">Zmniejszanie zależności pakietów za pomocą projektu.json</span><span class="sxs-lookup"><span data-stu-id="c4c92-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="c4c92-104">W tym artykule omówiono, co należy wiedzieć o `project.json` zmniejszaniu zależności pakietu podczas tworzenia bibliotek.</span><span class="sxs-lookup"><span data-stu-id="c4c92-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="c4c92-105">Na końcu tego artykułu dowiesz się, jak skomponować biblioteki w taki sposób, że używa tylko zależności, których potrzebuje.</span><span class="sxs-lookup"><span data-stu-id="c4c92-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span>

## <a name="why-its-important"></a><span data-ttu-id="c4c92-106">Dlaczego jest to ważne</span><span class="sxs-lookup"><span data-stu-id="c4c92-106">Why it's Important</span></span>

<span data-ttu-id="c4c92-107">.NET Core to produkt złożony z pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="c4c92-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="c4c92-108">Podstawowym pakietem jest [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), który jest pakietem NuGet składającym się z innych pakietów.</span><span class="sxs-lookup"><span data-stu-id="c4c92-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span> <span data-ttu-id="c4c92-109">Zapewnia zestaw pakietów, które są gwarantowane do pracy na wiele implementacji .NET, takich jak .NET Framework, .NET Core i Xamarin/Mono.</span><span class="sxs-lookup"><span data-stu-id="c4c92-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core, and Xamarin/Mono.</span></span>

<span data-ttu-id="c4c92-110">Istnieje jednak duża szansa, że biblioteka nie będzie używać każdego pakietu, który zawiera.</span><span class="sxs-lookup"><span data-stu-id="c4c92-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="c4c92-111">Podczas tworzenia biblioteki i dystrybucji go za pomocą NuGet, jest najlepszym rozwiązaniem do "przyciąć" zależności w dół tylko pakiety, które faktycznie używasz.</span><span class="sxs-lookup"><span data-stu-id="c4c92-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="c4c92-112">Powoduje to mniejszy ogólny rozmiar dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="c4c92-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="c4c92-113">Jak to zrobić</span><span class="sxs-lookup"><span data-stu-id="c4c92-113">How to do it</span></span>

<span data-ttu-id="c4c92-114">Obecnie nie ma `dotnet` oficjalnego polecenia, które przycina odwołania do pakietu.</span><span class="sxs-lookup"><span data-stu-id="c4c92-114">Currently, there is no official `dotnet` command that trims package references.</span></span>  <span data-ttu-id="c4c92-115">Zamiast tego musisz to zrobić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="c4c92-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="c4c92-116">Ogólny proces wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="c4c92-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="c4c92-117">Wersja `NETStandard.Library` `1.6.0` referencyjna `dependencies` w `project.json`sekcji pliku .</span><span class="sxs-lookup"><span data-stu-id="c4c92-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="c4c92-118">Przywracanie `dotnet restore` pakietów z[(patrz uwaga)](#dotnet-restore-note)z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c4c92-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="c4c92-119">Sprawdź `project.lock.json` plik i `NETStandard.Library` znajdź sekcję.</span><span class="sxs-lookup"><span data-stu-id="c4c92-119">Inspect the `project.lock.json` file and find the `NETStandard.Library` section.</span></span>  <span data-ttu-id="c4c92-120">Znajduje się na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="c4c92-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="c4c92-121">Skopiuj wszystkie `dependencies`wymienione pakiety w obszarze .</span><span class="sxs-lookup"><span data-stu-id="c4c92-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="c4c92-122">Usuń `.NETStandard.Library` odwołanie i zastąp je skopiowanymi pakietami.</span><span class="sxs-lookup"><span data-stu-id="c4c92-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="c4c92-123">Usuń odwołania do pakietów, których nie potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="c4c92-123">Remove references to packages you don't need.</span></span>

<span data-ttu-id="c4c92-124">Możesz dowiedzieć się, których pakietów nie potrzebujesz, jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="c4c92-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="c4c92-125">Próby i błędy.</span><span class="sxs-lookup"><span data-stu-id="c4c92-125">Trial and error.</span></span> <span data-ttu-id="c4c92-126">Wiąże się to usunięcie pakietu, przywrócenie, sprawdzanie, czy biblioteka nadal kompiluje i powtarzanie tego procesu.</span><span class="sxs-lookup"><span data-stu-id="c4c92-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="c4c92-127">Za pomocą narzędzia, takich jak [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) lub [.NET Reflektor,](https://www.red-gate.com/products/dotnet-development/reflector) aby zerknąć na odwołania, aby zobaczyć, co kod jest faktycznie przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="c4c92-127">Using a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span> <span data-ttu-id="c4c92-128">Następnie można usunąć pakiety, które nie odpowiadają typom, których używasz.</span><span class="sxs-lookup"><span data-stu-id="c4c92-128">You can then remove packages that don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="c4c92-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4c92-129">Example</span></span>

<span data-ttu-id="c4c92-130">Wyobraź sobie, że napisałeś bibliotekę, która dostarczyła dodatkowe funkcje dla typów kolekcji ogólnych.</span><span class="sxs-lookup"><span data-stu-id="c4c92-130">Imagine that you wrote a library that provided additional functionality to generic collection types.</span></span> <span data-ttu-id="c4c92-131">Taka biblioteka musiałaby zależeć od `System.Collections`pakietów takich jak , ale `System.Net.Http`może wcale nie zależeć od pakietów takich jak .</span><span class="sxs-lookup"><span data-stu-id="c4c92-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span> <span data-ttu-id="c4c92-132">W związku z tym dobrze byłoby przyciąć zależności pakietów do tego, czego wymaga ta biblioteka!</span><span class="sxs-lookup"><span data-stu-id="c4c92-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="c4c92-133">Aby przyciąć tę bibliotekę, należy rozpocząć od `project.json` pliku i dodać odwołanie do `NETStandard.Library` wersji `1.6.0`.</span><span class="sxs-lookup"><span data-stu-id="c4c92-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="c4c92-134">Następnie przywracasz `dotnet restore` pakiety za pomocą `project.lock.json` [(patrz uwaga),](#dotnet-restore-note)sprawdź plik `NETStandard.Library`i znajdź wszystkie pakiety przywrócone dla .</span><span class="sxs-lookup"><span data-stu-id="c4c92-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETStandard.Library`.</span></span>

<span data-ttu-id="c4c92-135">Oto jak wygląda odpowiednia `project.lock.json` sekcja w `netstandard1.0`pliku podczas kierowania:</span><span class="sxs-lookup"><span data-stu-id="c4c92-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

<span data-ttu-id="c4c92-136">Następnie skopiuj odniesienia `dependencies` do pakietu do `project.json` sekcji pliku `NETStandard.Library` biblioteki, zastępując odwołanie:</span><span class="sxs-lookup"><span data-stu-id="c4c92-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

<span data-ttu-id="c4c92-137">To dość dużo pakietów, z których wiele z pewnością nie jest niezbędnych do rozszerzenia typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c4c92-137">That's quite a lot of packages, many of which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="c4c92-138">Pakiety można usunąć ręcznie lub użyć narzędzia, takiego jak [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) lub [.NET Reflector,](https://www.red-gate.com/products/dotnet-development/reflector/) aby określić, które pakiety faktycznie używa kodu.</span><span class="sxs-lookup"><span data-stu-id="c4c92-138">You can either remove packages manually or use a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="c4c92-139">Oto, jak może wyglądać przycięty pakiet:</span><span class="sxs-lookup"><span data-stu-id="c4c92-139">Here's what a trimmed package could look like:</span></span>

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="c4c92-140">Teraz ma mniejszy ślad niż gdyby zależał od `NETStandard.Library` metapakietu.</span><span class="sxs-lookup"><span data-stu-id="c4c92-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
