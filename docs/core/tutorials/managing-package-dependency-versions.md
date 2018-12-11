---
title: Jak zarządzać wersjami zależności pakietu dla platformy .NET Core 1.0
description: Dowiedz się o zarządzanie wersjami zależności pakietu dla aplikacji i bibliotek platformy .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 7d7133ddb8717db1b830e531955454925c31a728
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168614"
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a><span data-ttu-id="f09c2-103">Jak zarządzać wersjami zależności pakietu dla platformy .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f09c2-103">How to Manage Package Dependency Versions for .NET Core 1.0</span></span>

<span data-ttu-id="f09c2-104">W tym artykule opisano, co musisz wiedzieć o wersji pakietu dla aplikacji i bibliotek platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f09c2-104">This article covers what you need to know about package versions for your .NET Core libraries and apps.</span></span>

## <a name="glossary"></a><span data-ttu-id="f09c2-105">Słownik</span><span class="sxs-lookup"><span data-stu-id="f09c2-105">Glossary</span></span>

<span data-ttu-id="f09c2-106">**Napraw** — naprawianie zależności oznacza, że używasz tej samej "rodziny" pakietów wydanych dla narzędzia NuGet dla platformy .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="f09c2-106">**Fix** - Fixing dependencies means you are using the same "family" of packages released on NuGet for .NET Core 1.0.</span></span>

<span data-ttu-id="f09c2-107">**Meta Microsoft.aspnetcore.all** — pakiet NuGet, który reprezentuje zestaw pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="f09c2-107">**Metapackage** - A NuGet package that represents a set of NuGet packages.</span></span>

<span data-ttu-id="f09c2-108">**Przycinanie** -oznacza usunięcie pakietów nie zależą od meta Microsoft.aspnetcore.all.</span><span class="sxs-lookup"><span data-stu-id="f09c2-108">**Trimming** - The act of removing the packages you do not depend on from a metapackage.</span></span>  <span data-ttu-id="f09c2-109">Jest to coś, co jest istotne dla autorów pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="f09c2-109">This is something relevant for NuGet package authors.</span></span>  <span data-ttu-id="f09c2-110">Zobacz [zmniejszenia zależności pakietów przy użyciu pliku project.json](../deploying/reducing-dependencies.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f09c2-110">See [Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md) for more information.</span></span> 

## <a name="fix-your-dependencies-to-net-core-10"></a><span data-ttu-id="f09c2-111">Naprawianie zależności do platformy .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="f09c2-111">Fix your dependencies to .NET Core 1.0</span></span>

<span data-ttu-id="f09c2-112">Niezawodne przywrócenia pakietów i pisanie niezawodnego kodu, ważne jest rozwiązaniu zależności do wersji pakietów wysyłania wraz z platformy .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="f09c2-112">To reliably restore packages and write reliable code, it's important that you fix your dependencies to the versions of packages shipping alongside .NET Core 1.0.</span></span>  <span data-ttu-id="f09c2-113">Oznacza to, że każdego pakietu, powinien mieć tylko jedną jego wersję z nie dodatkowych kwalifikatorach.</span><span class="sxs-lookup"><span data-stu-id="f09c2-113">This means every package should have a single version with no additional qualifiers.</span></span>

<span data-ttu-id="f09c2-114">**Przykłady pakietów stałą 1.0**</span><span class="sxs-lookup"><span data-stu-id="f09c2-114">**Examples of packages fixed to 1.0**</span></span>

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

<span data-ttu-id="f09c2-115">**Przykładowe pakiety, które nie zostały usunięte ze 1.0**</span><span class="sxs-lookup"><span data-stu-id="f09c2-115">**Examples of packages that are NOT fixed to 1.0**</span></span>

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a><span data-ttu-id="f09c2-116">Dlaczego jest to istotne?</span><span class="sxs-lookup"><span data-stu-id="f09c2-116">Why does this matter?</span></span>

<span data-ttu-id="f09c2-117">Firma Microsoft gwarantuje, że jeśli możesz rozwiązać zależności do jakich dostarczany wraz z platformy .NET Core 1.0, te pakiety będą współpracują ze sobą.</span><span class="sxs-lookup"><span data-stu-id="f09c2-117">We guarantee that if you fix your dependencies to what ships alongside .NET Core 1.0, those packages will all work together.</span></span> <span data-ttu-id="f09c2-118">Nie ma takich gwarancji Jeśli korzystanie z pakietów, które nie są ustalone w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="f09c2-118">There is no such guarantee if you use packages which aren't fixed in this way.</span></span>

### <a name="scenarios"></a><span data-ttu-id="f09c2-119">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="f09c2-119">Scenarios</span></span>

<span data-ttu-id="f09c2-120">Mimo że znajduje się lista big wszystkie pakiety i ich wersji wydanej z platformy .NET Core 1.0, nie masz do wyszukiwania przez nią, jeśli Twój kod znajduje się w niektórych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="f09c2-120">Although there is a big list of all packages and their versions released with .NET Core 1.0, you may not have to look through it if your code falls under certain scenarios.</span></span>

<span data-ttu-id="f09c2-121">**Czy zależności tylko w systemach** `NETStandard.Library` **?**</span><span class="sxs-lookup"><span data-stu-id="f09c2-121">**Are you depending only on** `NETStandard.Library`**?**</span></span>

<span data-ttu-id="f09c2-122">Jeśli tak, którą powinieneś naprawić swoje `NETStandard.Library` pakietu do wersji `1.6`.</span><span class="sxs-lookup"><span data-stu-id="f09c2-122">If so, you should fix your `NETStandard.Library` package to version `1.6`.</span></span>  <span data-ttu-id="f09c2-123">Ponieważ wyselekcjonowanych meta Microsoft.aspnetcore.all jego zamknięcia pakietu również zostanie usunięty z wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="f09c2-123">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="f09c2-124">**Czy zależności tylko w systemach** `Microsoft.NETCore.App` **?**</span><span class="sxs-lookup"><span data-stu-id="f09c2-124">**Are you depending only on** `Microsoft.NETCore.App`**?**</span></span>

<span data-ttu-id="f09c2-125">Jeśli tak, którą powinieneś naprawić swoje `Microsoft.NETCore.App` pakietu do wersji `1.0.0`.</span><span class="sxs-lookup"><span data-stu-id="f09c2-125">If so, you should fix your `Microsoft.NETCore.App` package to version `1.0.0`.</span></span>  <span data-ttu-id="f09c2-126">Ponieważ wyselekcjonowanych meta Microsoft.aspnetcore.all jego zamknięcia pakietu również zostanie usunięty z wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="f09c2-126">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="f09c2-127">**Czy [przycinania](../deploying/reducing-dependencies.md) swoje** `NETStandard.Library` **lub** `Microsoft.NETCore.App` **zależności meta Microsoft.aspnetcore.all?**</span><span class="sxs-lookup"><span data-stu-id="f09c2-127">**Are you [trimming](../deploying/reducing-dependencies.md) your** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackage dependencies?**</span></span>

<span data-ttu-id="f09c2-128">Jeśli tak, należy upewnić się, że meta Microsoft.aspnetcore.all, który jest uruchamiany, za pomocą zostanie usunięty z wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="f09c2-128">If so, you should ensure that the metapackage you start with is fixed to 1.0.</span></span>  <span data-ttu-id="f09c2-129">Indywidualne pakiety, które są zależne od po przycięciu również są stałe do 1,0.</span><span class="sxs-lookup"><span data-stu-id="f09c2-129">The individual packages you depend on after trimming are also fixed to 1.0.</span></span>

<span data-ttu-id="f09c2-130">**Czy w zależności od pakietów poza** `NETStandard.Library` **lub** `Microsoft.NETCore.App` **metapakiety?**</span><span class="sxs-lookup"><span data-stu-id="f09c2-130">**Are you depending on packages outside the** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackages?**</span></span>

<span data-ttu-id="f09c2-131">Jeśli tak, należy naprawianie zależności do 1,0.</span><span class="sxs-lookup"><span data-stu-id="f09c2-131">If so, you need to fix your other dependencies to 1.0.</span></span>  <span data-ttu-id="f09c2-132">Zobacz wersje poprawny pakiet i numery na końcu tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="f09c2-132">See the correct package versions and build numbers at the end of this article.</span></span>

### <a name="a-note-on-using-a-splat-string--when-versioning"></a><span data-ttu-id="f09c2-133">Uwaga dotycząca przy użyciu ciągu splat (\*) podczas przechowywania wersji</span><span class="sxs-lookup"><span data-stu-id="f09c2-133">A note on using a splat string (\*) when versioning</span></span>

<span data-ttu-id="f09c2-134">Przyjęła wzorzec przechowywania wersji, który używa splat (\*) ciąg następująco: `"System.Collections":"4.0.11-*"`.</span><span class="sxs-lookup"><span data-stu-id="f09c2-134">You may have adopted a versioning pattern which uses a splat (\*) string like this: `"System.Collections":"4.0.11-*"`.</span></span>

<span data-ttu-id="f09c2-135">**Nie należy tego robić**.</span><span class="sxs-lookup"><span data-stu-id="f09c2-135">**You should not do this**.</span></span>  <span data-ttu-id="f09c2-136">Przy użyciu ciągu splat może spowodować Trwa przywracanie pakietów z różnych kompilacji, z których część może być dalej w tym samym niż platformy .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="f09c2-136">Using the splat string could result in restoring packages from different builds, some of which may be further along than .NET Core 1.0.</span></span>  <span data-ttu-id="f09c2-137">Następnie może to spowodować niektóre pakiety są niezgodne.</span><span class="sxs-lookup"><span data-stu-id="f09c2-137">This could then result in some packages being incompatible.</span></span>

## <a name="packages-and-version-numbers-organized-by-metapackage"></a><span data-ttu-id="f09c2-138">Pakiety i numery wersji uporządkowane według meta Microsoft.aspnetcore.all</span><span class="sxs-lookup"><span data-stu-id="f09c2-138">Packages and Version Numbers organized by Metapackage</span></span>

<span data-ttu-id="f09c2-139">[Lista wszystkich pakietów .NET Standard i ich wersji 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="f09c2-139">[List of all .NET Standard packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span></span>

<span data-ttu-id="f09c2-140">[Lista wszystkich pakietów środowiska uruchomieniowego i ich wersji 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="f09c2-140">[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span></span>

<span data-ttu-id="f09c2-141">[Lista wszystkich pakietów aplikacji .NET Core i ich wersji 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span><span class="sxs-lookup"><span data-stu-id="f09c2-141">[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span></span>
