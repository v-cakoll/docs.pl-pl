---
title: What's new in .NET Standard
description: Ten artykuł zawiera podsumowanie nowych funkcji i ulepszeń w każda nowa wersja programu .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c99f59478b61bd382d6bf9529d2921407cc70bc
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133055"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="9c242-103">What's new in .NET Standard</span><span class="sxs-lookup"><span data-stu-id="9c242-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="9c242-104">.NET Standard to formalną specyfikację, definiujący określonej wersji zestawu interfejsów API, które muszą być dostępne w implementacji .NET, które są zgodne z wersji standard.</span><span class="sxs-lookup"><span data-stu-id="9c242-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="9c242-105">.NET Standard jest przeznaczona dla deweloperów bibliotek.</span><span class="sxs-lookup"><span data-stu-id="9c242-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="9c242-106">Biblioteka, która jest przeznaczona dla wersji .NET Standard może służyć w .NET Framework, .NET Core i Xamarin implementacji, który obsługuje daną wersję standard.</span><span class="sxs-lookup"><span data-stu-id="9c242-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="9c242-107">Najnowszą wersję programu .NET Standard jest w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="9c242-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="9c242-108">Znajduje się za pomocą zestawu .NET Core 2.0 SDK, a także za pomocą programu Visual Studio 2017 w wersji 15.3 z zainstalowanym obciążeniem platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c242-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="9c242-109">Obsługiwane implementacje platformy .NET</span><span class="sxs-lookup"><span data-stu-id="9c242-109">Supported .NET implementations</span></span>

<span data-ttu-id="9c242-110">.NET Standard 2.0 jest obsługiwany przez następujące implementacje platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="9c242-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="9c242-111">.NET core 2.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="9c242-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="9c242-112">Program .NET framework 4.6.1 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="9c242-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="9c242-113">Narzędzie mono 5.4 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="9c242-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="9c242-114">Xamarin.iOS 10.14 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="9c242-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="9c242-115">Platforma Xamarin.Mac 3,8 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="9c242-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="9c242-116">Platforma Xamarin.Android w wersji 8.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="9c242-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="9c242-117">Universal Windows Platform 10.0.16299 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="9c242-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="9c242-118">What's new in .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="9c242-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="9c242-119">.NET Standard 2.0 obejmuje następujące nowe funkcje:</span><span class="sxs-lookup"><span data-stu-id="9c242-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="9c242-120">Znacznie rozwinięty zestaw interfejsów API</span><span class="sxs-lookup"><span data-stu-id="9c242-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="9c242-121">Za pomocą wersji 1.6 .NET Standard uwzględnione stosunkowo małego podzbioru interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="9c242-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="9c242-122">Wśród tych wykluczonych były wiele interfejsów API, które często używane w programie .NET Framework lub Xamarin.</span><span class="sxs-lookup"><span data-stu-id="9c242-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="9c242-123">Ten komplikuje rozwoju, ponieważ wymaga ona, czy deweloperów Znajdź odpowiednie elementy zastępcze dobrze znanych interfejsów API, podczas ich tworzenia aplikacji i bibliotek przeznaczonych do wielu implementacjach systemu .NET.</span><span class="sxs-lookup"><span data-stu-id="9c242-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="9c242-124">.NET Standard 2.0 dotyczy to ograniczenie, dodając ponad 20 000 więcej interfejsów API nie były dostępne w .NET Standard w wersji 1.6, poprzednią wersję standard.</span><span class="sxs-lookup"><span data-stu-id="9c242-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="9c242-125">Aby uzyskać listę interfejsów API, które zostały dodane do platformy .NET Standard 2.0, zobacz [vs .NET Standard 2.0 w wersji 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="9c242-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="9c242-126">Niektóre dodatki do <xref:System> przestrzeni nazw w programie .NET Standard 2.0 obejmują:</span><span class="sxs-lookup"><span data-stu-id="9c242-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="9c242-127">Obsługa <xref:System.AppDomain> klasy.</span><span class="sxs-lookup"><span data-stu-id="9c242-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="9c242-128">Lepsza obsługa pracy z tablicami z dodatkowe elementy członkowskie w <xref:System.Array> klasy.</span><span class="sxs-lookup"><span data-stu-id="9c242-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="9c242-129">Lepsza obsługa pracy z atrybutami dodatkowe elementy członkowskie w <xref:System.Attribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="9c242-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="9c242-130">Lepiej kalendarza pomocy technicznej i dodatkowe opcje formatowania dla <xref:System.DateTime> wartości.</span><span class="sxs-lookup"><span data-stu-id="9c242-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="9c242-131">Dodatkowe <xref:System.Decimal> zaokrąglania funkcji.</span><span class="sxs-lookup"><span data-stu-id="9c242-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="9c242-132">Dodatkowe funkcje w <xref:System.Environment> klasy.</span><span class="sxs-lookup"><span data-stu-id="9c242-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="9c242-133">Rozszerzony kontrolę nad moduł odśmiecania pamięci, za pośrednictwem <xref:System.GC> klasy.</span><span class="sxs-lookup"><span data-stu-id="9c242-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="9c242-134">Rozszerzoną obsługę porównania ciągów, wyliczenia i normalizacji w <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="9c242-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="9c242-135">Obsługa Uwzględniaj dostosowań i czasów przejścia w <xref:System.TimeZoneInfo.AdjustmentRule> i <xref:System.TimeZoneInfo.TransitionTime> klasy.</span><span class="sxs-lookup"><span data-stu-id="9c242-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="9c242-136">Znacznie rozszerzone funkcje w <xref:System.Type> klasy.</span><span class="sxs-lookup"><span data-stu-id="9c242-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="9c242-137">Lepsza obsługa deserializacji obiektów wyjątków przez dodanie konstruktora wyjątków z <xref:System.Runtime.Serialization.SerializationInfo> i <xref:System.Runtime.Serialization.StreamingContext> parametrów.</span><span class="sxs-lookup"><span data-stu-id="9c242-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="9c242-138">Obsługa bibliotek .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9c242-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="9c242-139">Przeważająca większość bibliotek docelowe z .NET Framework, a nie .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9c242-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="9c242-140">Jednak większość wywołań w tych bibliotek są do interfejsów API, które stanowią część pakietu .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="9c242-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="9c242-141">Począwszy od .NET Standard 2.0, dostępne biblioteki .NET Framework z biblioteki .NET Standard za pomocą [podkładki zgodności](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-20/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="9c242-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="9c242-142">Ta warstwa zgodności jest niewidoczne dla deweloperów; nie trzeba wykonywać żadnych czynności, aby móc korzystać z biblioteki .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9c242-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="9c242-143">Jednym wymaganiem jest o tym, czy interfejsy API o nazwie w bibliotece klas programu .NET Framework, muszą być zawarte w .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="9c242-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="9c242-144">Obsługa języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c242-144">Support for Visual Basic</span></span>

<span data-ttu-id="9c242-145">Możesz teraz tworzyć biblioteki .NET Standard w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9c242-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="9c242-146">Dla deweloperów programu Visual Basic, za pomocą programu Visual Studio 2017 w wersji 15.3 lub nowszym z zainstalowanym obciążeniem platformy .NET Core Visual Studio zawiera obecnie szablon Biblioteka klas programu .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9c242-146">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="9c242-147">Dla deweloperów języka Visual Basic, którzy korzystają z innych narzędzi programistycznych i środowisk, możesz użyć [dotnet nowe](../../core/tools/dotnet-new.md) polecenie, aby utworzyć projekt Biblioteka .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9c242-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="9c242-148">Aby uzyskać więcej informacji, zobacz [narzędzia obsługujące biblioteki .NET Standard](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="9c242-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="9c242-149">Obsługę narzędzi dla biblioteki .NET Standard</span><span class="sxs-lookup"><span data-stu-id="9c242-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="9c242-150">Wersja programu .NET Core 2.0 i .NET Standard 2.0, zarówno program Visual Studio 2017 i [.NET Core interfejsu wiersza polecenia (CLI)](../../core/tools/index.md) obejmują narzędzia do obsługi do tworzenia biblioteki .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9c242-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="9c242-151">Po zainstalowaniu programu Visual Studio z **programowanie dla wielu platform .NET Core** obciążenia, można utworzyć projekt biblioteki .NET Standard 2.0 przy użyciu szablonu projektu, jak przedstawiono na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="9c242-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="9c242-152">C#</span><span class="sxs-lookup"><span data-stu-id="9c242-152">C#</span></span>](#tab/csharp)

![Dodaj projekt biblioteki nowe .NET Standard](./media/std-project-cs.png)

<span data-ttu-id="9c242-154">Jeśli używasz platformy .NET Core interfejsu wiersza polecenia, następujące [dotnet nowe](../../core/tools/dotnet-new.md) polecenie tworzy projekt biblioteki klas, który jest przeznaczony dla .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="9c242-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="9c242-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c242-155">Visual Basic</span></span>](#tab/vb)

![Dodaj projekt biblioteki nowe .NET Standard](./media/std-project-vb.png)

<span data-ttu-id="9c242-157">Jeśli używasz platformy .NET Core interfejsu wiersza polecenia, następujące [dotnet nowe](../../core/tools/dotnet-new.md) polecenie tworzy projekt biblioteki klas, który jest przeznaczony dla .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="9c242-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="9c242-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c242-158">See also</span></span>

- [<span data-ttu-id="9c242-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="9c242-159">.NET Standard</span></span>](../net-standard.md)  
- [<span data-ttu-id="9c242-160">Wprowadzenie do platformy .NET Standard</span><span class="sxs-lookup"><span data-stu-id="9c242-160">Introducing .NET Standard</span></span>](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
