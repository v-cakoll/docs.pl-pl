---
title: Zmniejszenie zależności pakietu z pliku project.json
description: Zmniejszenie zależności pakietu, podczas tworzenia biblioteki na podstawie pliku project.json.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: ae314800f789cee363728def8347b5e6990acb0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211787"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="b805c-103">Zmniejszenie zależności pakietu z pliku project.json</span><span class="sxs-lookup"><span data-stu-id="b805c-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="b805c-104">W tym artykule opisano, co należy wiedzieć o zmniejszeniu zależności pakietu, podczas tworzenia `project.json` biblioteki.</span><span class="sxs-lookup"><span data-stu-id="b805c-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="b805c-105">Na koniec tego artykułu dowiesz się, jak utworzenie biblioteki w taki sposób, że używa tylko zależności, które są niezbędne.</span><span class="sxs-lookup"><span data-stu-id="b805c-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span> 

## <a name="why-its-important"></a><span data-ttu-id="b805c-106">Dlaczego jest ważne</span><span class="sxs-lookup"><span data-stu-id="b805c-106">Why it's Important</span></span>

<span data-ttu-id="b805c-107">Oprogramowanie .NET core to produkt składają się z pakietami NuGet.</span><span class="sxs-lookup"><span data-stu-id="b805c-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="b805c-108">Pakiet niezbędne jest [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), która pakietu NuGet składa się z innymi pakietami.</span><span class="sxs-lookup"><span data-stu-id="b805c-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span>  <span data-ttu-id="b805c-109">Umożliwia zestaw pakietów, które mogą działać na wiele implementacji .NET, takich jak .NET Framework, .NET Core i Xamarin/Mono.</span><span class="sxs-lookup"><span data-stu-id="b805c-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core and Xamarin/Mono.</span></span>

<span data-ttu-id="b805c-110">Jednakże istnieje szansa, że biblioteki nie będą korzystać co jeden pakiet, który zawiera.</span><span class="sxs-lookup"><span data-stu-id="b805c-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="b805c-111">Podczas tworzenia biblioteki i jej dystrybucji za pośrednictwem NuGet, jest najlepszym rozwiązaniem "Przycinanie" zależności dół tylko pakiety rzeczywiście używane.</span><span class="sxs-lookup"><span data-stu-id="b805c-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="b805c-112">Powoduje mniejsze zużycie ogólną pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="b805c-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="b805c-113">Jak to zrobić</span><span class="sxs-lookup"><span data-stu-id="b805c-113">How to do it</span></span>

<span data-ttu-id="b805c-114">Obecnie nie są nie oficjalne `dotnet` polecenia, które usuwa odwołania do pakietu.</span><span class="sxs-lookup"><span data-stu-id="b805c-114">Currently, there is no official `dotnet` command which trims package references.</span></span>  <span data-ttu-id="b805c-115">Zamiast tego należy to zrobić ręcznie.</span><span class="sxs-lookup"><span data-stu-id="b805c-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="b805c-116">Ogólny proces wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="b805c-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="b805c-117">Odwołanie `NETStandard.Library` wersji `1.6.0` w `dependencies` części Twojego `project.json`.</span><span class="sxs-lookup"><span data-stu-id="b805c-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="b805c-118">Przywracanie pakietów z `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b805c-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="b805c-119">Sprawdź `project.lock.json` plików i Znajdź `NETSTandard.Library` sekcji.</span><span class="sxs-lookup"><span data-stu-id="b805c-119">Inspect the `project.lock.json` file and find the `NETSTandard.Library` section.</span></span>  <span data-ttu-id="b805c-120">Jest na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="b805c-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="b805c-121">Skopiuj wszystkie pakiety wymienione w obszarze `dependencies`.</span><span class="sxs-lookup"><span data-stu-id="b805c-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="b805c-122">Usuń `.NETStandard.Library` odwołania i zastąp go skopiowanych pakietów.</span><span class="sxs-lookup"><span data-stu-id="b805c-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="b805c-123">Usuń odwołania do pakietów, które nie są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="b805c-123">Remove references to packages you don't need.</span></span>


<span data-ttu-id="b805c-124">Można znaleźć pakiety, których nie ma potrzeby przez jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="b805c-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="b805c-125">Prób i błędów.</span><span class="sxs-lookup"><span data-stu-id="b805c-125">Trial and error.</span></span>  <span data-ttu-id="b805c-126">Obejmuje to usunięcie pakietu, przywracanie wyświetlany, jeśli biblioteka nadal kompiluje i powtórzyć ten proces.</span><span class="sxs-lookup"><span data-stu-id="b805c-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="b805c-127">Przy użyciu narzędzia, takie jak [ILSpy](http://ilspy.net) lub [reflektora .NET](http://www.red-gate.com/products/dotnet-development/reflector) wglądu odwołania, aby zobaczyć, co kod jest rzeczywiście przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="b805c-127">Using a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span>  <span data-ttu-id="b805c-128">Następnie można usunąć pakietów, które nie odnoszą się do typów, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="b805c-128">You can then remove packages which don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="b805c-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="b805c-129">Example</span></span> 

<span data-ttu-id="b805c-130">Załóżmy, że zapisano bibliotekę, która podano dodatkowe funkcje typy kolekcji ogólnych.</span><span class="sxs-lookup"><span data-stu-id="b805c-130">Imagine that you wrote a library which provided additional functionality to generic collection types.</span></span>  <span data-ttu-id="b805c-131">Takie biblioteki musi być zależne od pakietów, takie jak `System.Collections`, ale może być w ogóle zależne od pakietów takich jak `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="b805c-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span>  <span data-ttu-id="b805c-132">Tak byłoby dobrej przyciąć zależności pakietu do co ta biblioteka wymagane tylko!</span><span class="sxs-lookup"><span data-stu-id="b805c-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="b805c-133">Aby przyciąć tej biblioteki, należy uruchomić z `project.json` i Dodaj odwołanie do `NETStandard.Library` wersji `1.6.0`.</span><span class="sxs-lookup"><span data-stu-id="b805c-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

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

<span data-ttu-id="b805c-134">Następnie należy przywrócić pakiety z `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)), sprawdzić `project.lock.json` plików i Znajdź wszystkie pakiety przywrócone dla `NETSTandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="b805c-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETSTandard.Library`.</span></span>

<span data-ttu-id="b805c-135">Oto jakie odpowiedniej sekcji `project.lock.json` pliku wygląda podobnie, jeśli celem `netstandard1.0`:</span><span class="sxs-lookup"><span data-stu-id="b805c-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

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

<span data-ttu-id="b805c-136">Następnie skopiuj za pośrednictwem odwołania do pakietu do `dependencies` części biblioteki `project.json` pliku, zastępując `NETStandard.Library` odwołania:</span><span class="sxs-lookup"><span data-stu-id="b805c-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

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

<span data-ttu-id="b805c-137">Bardzo dużo pakietów, duża liczba które które na pewno nie są niezbędne do rozszerzania typy kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b805c-137">That's quite a lot of packages, many of which which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="b805c-138">Można ręcznie usunąć pakietów lub za pomocą narzędzia, takie jak [ILSpy](http://ilspy.net) lub [reflektora .NET](http://www.red-gate.com/products/dotnet-development/reflector) do identyfikowania, która faktycznie pakiety kodu używa.</span><span class="sxs-lookup"><span data-stu-id="b805c-138">You can either remove packages manually or use a tool such as [ILSpy](http://ilspy.net) or [.NET Reflector](http://www.red-gate.com/products/dotnet-development/reflector) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="b805c-139">Oto, jak może wyglądać przycięte pakietu:</span><span class="sxs-lookup"><span data-stu-id="b805c-139">Here's what a trimmed package could look like:</span></span>

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

<span data-ttu-id="b805c-140">Teraz, ma mniejszy wyświetlacz niż jeśli ma ono zależy na `NETStandard.Library` metapackage.</span><span class="sxs-lookup"><span data-stu-id="b805c-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]