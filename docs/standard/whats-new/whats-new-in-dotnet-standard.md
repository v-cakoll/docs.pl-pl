---
title: Co to jest nowa w programie .NET Standard
description: W tym artykule przedstawiono nowe funkcje i ulepszenia znajdujące się w każdej nowej wersji programu .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e422e6ff65439d105020a6305b66a8192586a8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="2a148-103">Co to jest nowa w programie .NET Standard</span><span class="sxs-lookup"><span data-stu-id="2a148-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="2a148-104">.NET Standard jest formalną specyfikację, który definiuje wersjonowany zestaw interfejsów API, które muszą być dostępne na implementacje .NET, które są zgodne z tą wersją standardowego.</span><span class="sxs-lookup"><span data-stu-id="2a148-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="2a148-105">.NET Standard jest przeznaczona dla deweloperów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="2a148-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="2a148-106">Biblioteka, przeznaczonego dla wersji platformy .NET Standard może służyć wykonania dowolnego .NET Framework .NET Core i Xamarin obsługuje tej wersji standard.</span><span class="sxs-lookup"><span data-stu-id="2a148-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="2a148-107">Najnowszą wersję programu .NET Standard jest wersja 2.0.</span><span class="sxs-lookup"><span data-stu-id="2a148-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="2a148-108">Jest dostępna przy użyciu zestawu SDK programu .NET Core 2.0, a także z programu Visual Studio 2017 wersji 15 ustęp 3 z obciążeniem .NET Core zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="2a148-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="2a148-109">Obsługiwane implementacje .NET</span><span class="sxs-lookup"><span data-stu-id="2a148-109">Supported .NET implementations</span></span>

<span data-ttu-id="2a148-110">.NET 2.0 standardowe jest obsługiwany przez następujące implementacje .NET:</span><span class="sxs-lookup"><span data-stu-id="2a148-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="2a148-111">Oprogramowanie .NET core 2.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="2a148-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="2a148-112">.NET framework 4.6.1 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="2a148-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="2a148-113">Mono 5.4 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="2a148-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="2a148-114">Xamarin.iOS 10.14 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="2a148-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="2a148-115">Xamarin.Mac 3.8 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="2a148-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="2a148-116">Xamarin.Android 8.0 lub nowszej</span><span class="sxs-lookup"><span data-stu-id="2a148-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="2a148-117">Platforma uniwersalna systemu Windows 10.0.16299 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="2a148-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="2a148-118">Co to jest nowa w programie .NET 2.0 standardowe</span><span class="sxs-lookup"><span data-stu-id="2a148-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="2a148-119">Standardowa .NET 2.0 obejmuje następujące nowe funkcje:</span><span class="sxs-lookup"><span data-stu-id="2a148-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="2a148-120">Znacząco rozwinięte zestaw interfejsów API</span><span class="sxs-lookup"><span data-stu-id="2a148-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="2a148-121">Za pomocą wersji 1.6 .NET Standard uwzględnione stosunkowo mały podzbiór interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="2a148-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="2a148-122">Między tymi wyłączone zostały wiele interfejsów API, które często używane w programie .NET Framework lub Xamarin.</span><span class="sxs-lookup"><span data-stu-id="2a148-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="2a148-123">Komplikuje rozwoju, ponieważ wymaga ona, że deweloperzy znaleźć odpowiednie elementy zastępcze znanych interfejsów API podczas opracowywania aplikacji i bibliotek przeznaczonych do wiele implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="2a148-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="2a148-124">.NET 2.0 standardowe usuwa to ograniczenie, dodając ponad 20 000 API więcej niż były dostępne w .NET Standard 1.6 poprzedniej wersji standard.</span><span class="sxs-lookup"><span data-stu-id="2a148-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="2a148-125">Listę interfejsów API, które zostały dodane do programu .NET 2.0 standardowego, zobacz [.NET 2.0 standardowe vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="2a148-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="2a148-126">Niektóre dodatki do <xref:System> przestrzeni nazw w .NET Standard 2.0 obejmują:</span><span class="sxs-lookup"><span data-stu-id="2a148-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="2a148-127">Obsługa <xref:System.AppDomain> klasy.</span><span class="sxs-lookup"><span data-stu-id="2a148-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="2a148-128">Lepszą obsługę pracy z tablicami z dodatkowych członków w <xref:System.Array> klasy.</span><span class="sxs-lookup"><span data-stu-id="2a148-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="2a148-129">Lepszą obsługę pracy z atrybutów z dodatkowych członków w <xref:System.Attribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="2a148-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="2a148-130">Lepiej kalendarza pomocy technicznej i dodatkowe opcje formatowania <xref:System.DateTime> wartości.</span><span class="sxs-lookup"><span data-stu-id="2a148-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="2a148-131">Dodatkowe <xref:System.Decimal> funkcji zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="2a148-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="2a148-132">Dodatkowe funkcje w <xref:System.Environment> klasy.</span><span class="sxs-lookup"><span data-stu-id="2a148-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="2a148-133">Ulepszone kontrolę nad modułu zbierającego elementy bezużyteczne za pośrednictwem <xref:System.GC> klasy.</span><span class="sxs-lookup"><span data-stu-id="2a148-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="2a148-134">Rozszerzona obsługa porównania ciągów, wyliczenia i normalizacji w <xref:System.String> klasy.</span><span class="sxs-lookup"><span data-stu-id="2a148-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="2a148-135">Obsługa Uwzględniaj dostosowań i czasy przejścia w <xref:System.TimeZoneInfo.AdjustmentRule> i <xref:System.TimeZoneInfo.TransitionTime> klasy.</span><span class="sxs-lookup"><span data-stu-id="2a148-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="2a148-136">Znacznie rozszerzoną funkcjonalność w <xref:System.Type> klasy.</span><span class="sxs-lookup"><span data-stu-id="2a148-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="2a148-137">Lepszą obsługę deserializacji obiektów wyjątku przez dodanie wyjątku konstruktora z <xref:System.Runtime.Serialization.SerializationInfo> i <xref:System.Runtime.Serialization.StreamingContext> parametrów.</span><span class="sxs-lookup"><span data-stu-id="2a148-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="2a148-138">Obsługa bibliotek .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2a148-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="2a148-139">Przeważająca większość bibliotek docelowy .NET Framework, a nie .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2a148-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="2a148-140">Do interfejsów API, które znajdują się w .NET 2.0 standardowe są jednak większość wywołań w tych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="2a148-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="2a148-141">Począwszy od programu .NET 2.0 standardowe dostępnych bibliotek .NET Framework z biblioteki .NET Standard za pomocą [podkładki zgodności](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="2a148-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="2a148-142">Ta warstwa zgodności jest niewidoczny dla deweloperów; nie trzeba wykonywać żadnych czynności, aby móc korzystać z biblioteki .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2a148-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="2a148-143">Pojedynczy wymagane jest, że interfejsy API o nazwie w bibliotece klas programu .NET Framework muszą być zawarte w standardowe .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="2a148-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="2a148-144">Obsługa języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2a148-144">Support for Visual Basic</span></span>

<span data-ttu-id="2a148-145">Można teraz tworzyć .NET standardowych bibliotek języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2a148-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="2a148-146">Dla deweloperów języka Visual Basic, za pomocą programu Visual Studio 2017 wersji 15 ustęp 3 lub nowszym z obciążenia .NET Core zainstalowane Visual Studio teraz obejmuje szablonu standardowa biblioteka klas programu .NET.</span><span class="sxs-lookup"><span data-stu-id="2a148-146">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="2a148-147">Dla deweloperów języka Visual Basic, korzystających z innych narzędzi do tworzenia i środowisk, można użyć [dotnet nowe](../../core/tools/dotnet-new.md) polecenie, aby utworzyć projekt biblioteki standardowej .NET.</span><span class="sxs-lookup"><span data-stu-id="2a148-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="2a148-148">Aby uzyskać więcej informacji, zobacz [Obsługa narzędzi dla platformy .NET standardowych bibliotek](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="2a148-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="2a148-149">Obsługa narzędzi dla platformy .NET standardowych bibliotek</span><span class="sxs-lookup"><span data-stu-id="2a148-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="2a148-150">Wraz z wydaniem programu .NET Core 2.0 i .NET 2.0 standardowe, zarówno programu Visual Studio 2017 i [.NET Core interfejsu wiersza polecenia (CLI)](../../core/tools/index.md) obejmują narzędzia pomocy technicznej do tworzenia bibliotek .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2a148-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="2a148-151">Jeśli zainstalujesz program Visual Studio z **aplikacji dla wielu platform .NET Core** obciążenie, można utworzyć projektu biblioteki .NET 2.0 standardowe za pomocą szablonu projektu, jak przedstawiono na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="2a148-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="2a148-152">C#</span><span class="sxs-lookup"><span data-stu-id="2a148-152">C#</span></span>](#tab/csharp)

![Dodaj nowy .NET Standard projektu biblioteki](./media/std-project-cs.png)

<span data-ttu-id="2a148-154">W przypadku korzystania z platformy .NET Core interfejsu wiersza polecenia, następujące [dotnet nowe](../../core/tools/dotnet-new.md) polecenie tworzy projektu biblioteki klas, przeznaczonego dla programu .NET 2.0 standardowe:</span><span class="sxs-lookup"><span data-stu-id="2a148-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="2a148-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2a148-155">Visual Basic</span></span>](#tab/vb)

![Dodaj nowy .NET Standard projektu biblioteki](./media/std-project-vb.png)

<span data-ttu-id="2a148-157">W przypadku korzystania z platformy .NET Core interfejsu wiersza polecenia, następujące [dotnet nowe](../../core/tools/dotnet-new.md) polecenie tworzy projektu biblioteki klas, przeznaczonego dla programu .NET 2.0 standardowe:</span><span class="sxs-lookup"><span data-stu-id="2a148-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="2a148-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a148-158">See also</span></span>

[<span data-ttu-id="2a148-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="2a148-159">.NET Standard</span></span>](../net-standard.md)  
[<span data-ttu-id="2a148-160">Wprowadzenie do platformy .NET Standard</span><span class="sxs-lookup"><span data-stu-id="2a148-160">Introducing .NET Standard</span></span>](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
