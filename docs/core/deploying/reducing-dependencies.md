---
title: Zmniejszanie zależności pakietu przy użyciu pliku Project. JSON
description: Zmniejszenie zależności pakietu podczas tworzenia bibliotek opartych na pliku Project. JSON.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740829"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="3b6bb-103">Zmniejszanie zależności pakietu przy użyciu pliku Project. JSON</span><span class="sxs-lookup"><span data-stu-id="3b6bb-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="3b6bb-104">W tym artykule opisano, co należy wiedzieć o zmniejszeniu zależności pakietu podczas tworzenia bibliotek `project.json`.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="3b6bb-105">Na końcu tego artykułu dowiesz się, jak utworzyć bibliotekę w taki sposób, aby korzystała tylko z potrzeb.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span>

## <a name="why-its-important"></a><span data-ttu-id="3b6bb-106">Dlaczego jest ważne</span><span class="sxs-lookup"><span data-stu-id="3b6bb-106">Why it's Important</span></span>

<span data-ttu-id="3b6bb-107">.NET Core to produkt składający się z pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="3b6bb-108">Istotnym pakietem jest [. Pakiet servicepackage. Library](https://www.nuget.org/packages/NETStandard.Library), który jest pakietem NuGet składającym się z innych pakietów.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span> <span data-ttu-id="3b6bb-109">Zawiera zestaw pakietów, które są gwarantowane do pracy w wielu implementacjach platformy .NET, takich jak .NET Framework, .NET Core i Xamarin/mono.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core, and Xamarin/Mono.</span></span>

<span data-ttu-id="3b6bb-110">Istnieje jednak dobry szansa, że biblioteka nie będzie używać każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="3b6bb-111">W przypadku tworzenia biblioteki i dystrybucji jej za pośrednictwem programu NuGet najlepszym rozwiązaniem jest "przycinanie" zależności do tylko pakietów, których faktycznie używasz.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="3b6bb-112">Powoduje to mniejsze ogólne rozmiary pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="3b6bb-113">Jak to zrobić</span><span class="sxs-lookup"><span data-stu-id="3b6bb-113">How to do it</span></span>

<span data-ttu-id="3b6bb-114">Obecnie nie istnieje oficjalne polecenie `dotnet`, które przycina odwołania do pakietów.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-114">Currently, there is no official `dotnet` command that trims package references.</span></span>  <span data-ttu-id="3b6bb-115">Zamiast tego należy to zrobić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="3b6bb-116">Ogólny proces wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="3b6bb-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="3b6bb-117">Informacje o wersji `NETStandard.Library` `1.6.0` w sekcji `dependencies` `project.json`.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="3b6bb-118">Przywróć pakiety z `dotnet restore` ([Zobacz Uwaga](#dotnet-restore-note)) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="3b6bb-119">Sprawdź plik `project.lock.json` i Znajdź sekcję `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-119">Inspect the `project.lock.json` file and find the `NETStandard.Library` section.</span></span>  <span data-ttu-id="3b6bb-120">Znajduje się blisko początku pliku.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="3b6bb-121">Skopiuj wszystkie pakiety z listy w obszarze `dependencies`.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="3b6bb-122">Usuń odwołanie `.NETStandard.Library` i zastąp je skopiowanymi pakietami.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="3b6bb-123">Usuń odwołania do pakietów, które nie są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-123">Remove references to packages you don't need.</span></span>

<span data-ttu-id="3b6bb-124">Możesz dowiedzieć się, które pakiety nie są potrzebne, wykonując jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="3b6bb-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="3b6bb-125">Wersja próbna i błąd.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-125">Trial and error.</span></span> <span data-ttu-id="3b6bb-126">Obejmuje to usuwanie pakietu, przywracanie, wyświetlanie, czy biblioteka jest nadal skompilowana, i powtarzanie tego procesu.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="3b6bb-127">Za pomocą narzędzia, takiego jak [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) lub [reflektor .NET](https://www.red-gate.com/products/dotnet-development/reflector) , można uzyskać wgląd w odwołania, aby zobaczyć, do czego służy Twój kod.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-127">Using a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span> <span data-ttu-id="3b6bb-128">Następnie można usunąć pakiety, które nie odpowiadają typom, z którego korzystasz.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-128">You can then remove packages that don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="3b6bb-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b6bb-129">Example</span></span>

<span data-ttu-id="3b6bb-130">Załóżmy, że Zapisano bibliotekę, która udostępnia dodatkowe funkcje dla typów kolekcji rodzajowych.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-130">Imagine that you wrote a library that provided additional functionality to generic collection types.</span></span> <span data-ttu-id="3b6bb-131">Taka Biblioteka musi zależeć od pakietów, takich jak `System.Collections`, ale może nie zależeć od pakietów, takich jak `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span> <span data-ttu-id="3b6bb-132">W związku z tym dobrym sposobem jest przycinanie zależności pakietów do tylko potrzeb tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="3b6bb-133">Aby przyciąć tę bibliotekę, Zacznij od pliku `project.json` i Dodaj odwołanie do `NETStandard.Library` wersji `1.6.0`.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

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

<span data-ttu-id="3b6bb-134">Następnie Przywróć pakiety z `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)), sprawdź plik `project.lock.json` i Znajdź wszystkie pakiety przywrócone dla `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETStandard.Library`.</span></span>

<span data-ttu-id="3b6bb-135">Poniżej przedstawiono informacje o tym, co znajduje się w odpowiedniej sekcji w pliku `project.lock.json` podczas określania celu `netstandard1.0`:</span><span class="sxs-lookup"><span data-stu-id="3b6bb-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

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

<span data-ttu-id="3b6bb-136">Następnie skopiuj odwołania do pakietu do sekcji `dependencies` pliku `project.json` biblioteki, zastępując `NETStandard.Library` odwołanie:</span><span class="sxs-lookup"><span data-stu-id="3b6bb-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

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

<span data-ttu-id="3b6bb-137">Jest to dość wiele pakietów, z których wiele nie jest koniecznych do rozszerzania typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-137">That's quite a lot of packages, many of which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="3b6bb-138">Pakiety można usuwać ręcznie lub za pomocą narzędzia, takiego jak [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) lub [reflektor .NET](https://www.red-gate.com/products/dotnet-development/reflector/) , aby identyfikować, które pakiety rzeczywiście są używane w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-138">You can either remove packages manually or use a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="3b6bb-139">Oto, jak może wyglądać przycięty pakiet:</span><span class="sxs-lookup"><span data-stu-id="3b6bb-139">Here's what a trimmed package could look like:</span></span>

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

<span data-ttu-id="3b6bb-140">Teraz ma mniejsze rozmiary niż w przypadku, gdy zależą od pakietu `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="3b6bb-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
