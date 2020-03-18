---
title: Co nowego w programie .NET Standard
description: W tym artykule podsumowano nowe funkcje i ulepszenia dostępne w każdej nowej wersji programu .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: a90df0360211c3b02f4f2d8697890180099c5807
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76921060"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="4b924-103">Co nowego w programie .NET Standard</span><span class="sxs-lookup"><span data-stu-id="4b924-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="4b924-104">Standard .NET jest formalną specyfikacją, która definiuje wersjonowany zestaw interfejsów API, które muszą być dostępne w implementacjach .NET, które są zgodne z tą wersją standardu.</span><span class="sxs-lookup"><span data-stu-id="4b924-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="4b924-105">Standard .NET jest przeznaczony dla deweloperów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="4b924-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="4b924-106">Biblioteka przeznaczona dla wersji .NET Standard może być używana w dowolnej implementacji .NET Framework, .NET Core lub Xamarin, która obsługuje tę wersję standardu.</span><span class="sxs-lookup"><span data-stu-id="4b924-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="4b924-107">Najnowsza wersja standardu .NET to 2.0.</span><span class="sxs-lookup"><span data-stu-id="4b924-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="4b924-108">Jest on dołączony do .NET Core 2.0 SDK, a także do programu Visual Studio 2017 w wersji 15.3 z zainstalowanym obciążeniem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b924-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="4b924-109">Obsługiwane implementacje .NET</span><span class="sxs-lookup"><span data-stu-id="4b924-109">Supported .NET implementations</span></span>

<span data-ttu-id="4b924-110">Standard .NET 2.0 jest obsługiwany przez następujące implementacje .NET:</span><span class="sxs-lookup"><span data-stu-id="4b924-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="4b924-111">.NET Core 2.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="4b924-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="4b924-112">.NET Framework 4.6.1 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="4b924-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="4b924-113">Mono 5.4 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="4b924-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="4b924-114">Xamarin.iOS 10.14 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="4b924-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="4b924-115">Xamarin.Mac 3.8 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="4b924-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="4b924-116">Xamarin.Android 8.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="4b924-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="4b924-117">Uniwersalna platforma systemu Windows 10.0.16299 lub nowsza</span><span class="sxs-lookup"><span data-stu-id="4b924-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="4b924-118">Co nowego w standardzie .NET 2.0</span><span class="sxs-lookup"><span data-stu-id="4b924-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="4b924-119">.NET Standard 2.0 zawiera następujące nowe funkcje:</span><span class="sxs-lookup"><span data-stu-id="4b924-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="4b924-120">Znacznie rozszerzony zestaw interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4b924-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="4b924-121">W wersji 1.6 standard .NET zawierał stosunkowo mały podzbiór interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="4b924-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="4b924-122">Wśród wykluczonych było wiele interfejsów API, które były powszechnie używane w .NET Framework lub Xamarin.</span><span class="sxs-lookup"><span data-stu-id="4b924-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="4b924-123">Komplikuje to rozwój, ponieważ wymaga, aby deweloperzy znaleźć odpowiednie zamienniki dla znanych interfejsów API podczas tworzenia aplikacji i bibliotek, które są przeznaczone dla wielu implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="4b924-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="4b924-124">.NET Standard 2.0 rozwiązuje to ograniczenie, dodając ponad 20 000 więcej interfejsów API niż były dostępne w .NET Standard 1.6, poprzedniej wersji standardu.</span><span class="sxs-lookup"><span data-stu-id="4b924-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="4b924-125">Aby uzyskać listę interfejsów API dodanych do standardu .NET Standard 2.0, zobacz [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="4b924-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="4b924-126">Niektóre dodatki do <xref:System> obszaru nazw w .NET Standard 2.0 obejmują:</span><span class="sxs-lookup"><span data-stu-id="4b924-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="4b924-127">Wsparcie dla <xref:System.AppDomain> klasy.</span><span class="sxs-lookup"><span data-stu-id="4b924-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="4b924-128">Lepsza obsługa pracy z tablicami z <xref:System.Array> dodatkowych elementów członkowskich w klasie.</span><span class="sxs-lookup"><span data-stu-id="4b924-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="4b924-129">Lepsza obsługa pracy z atrybutami z <xref:System.Attribute> dodatkowych członków w klasie.</span><span class="sxs-lookup"><span data-stu-id="4b924-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="4b924-130">Lepsza obsługa kalendarza i dodatkowe <xref:System.DateTime> opcje formatowania wartości.</span><span class="sxs-lookup"><span data-stu-id="4b924-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="4b924-131">Dodatkowa <xref:System.Decimal> funkcja zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="4b924-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="4b924-132">Dodatkowe funkcje w <xref:System.Environment> klasie.</span><span class="sxs-lookup"><span data-stu-id="4b924-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="4b924-133">Zwiększona kontrola nad modułodśmie pamięci za pośrednictwem <xref:System.GC> klasy.</span><span class="sxs-lookup"><span data-stu-id="4b924-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="4b924-134">Zwiększona obsługa porównywania ciągów, wyliczania i normalizacji w <xref:System.String> klasie.</span><span class="sxs-lookup"><span data-stu-id="4b924-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="4b924-135">Obsługa regulacji czasu letniego i czasów <xref:System.TimeZoneInfo.AdjustmentRule> przejścia <xref:System.TimeZoneInfo.TransitionTime> w klasach i.</span><span class="sxs-lookup"><span data-stu-id="4b924-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="4b924-136">Znacznie ulepszona <xref:System.Type> funkcjonalność w klasie.</span><span class="sxs-lookup"><span data-stu-id="4b924-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="4b924-137">Lepsza obsługa deserializacji obiektów wyjątków przez dodanie <xref:System.Runtime.Serialization.SerializationInfo> <xref:System.Runtime.Serialization.StreamingContext> konstruktora wyjątku z parametrami i parametrami.</span><span class="sxs-lookup"><span data-stu-id="4b924-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="4b924-138">Obsługa bibliotek programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4b924-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="4b924-139">Zdecydowana większość bibliotek jest docelowa dla .NET Framework zamiast .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4b924-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="4b924-140">Jednak większość wywołań w tych bibliotekach są do interfejsów API, które są zawarte w .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="4b924-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="4b924-141">Począwszy od .NET Standard 2.0, można uzyskać dostęp do bibliotek .NET Framework z biblioteki .NET Standard przy użyciu [podkładki zgodności](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="4b924-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="4b924-142">Ta warstwa zgodności jest niewidoczna dla deweloperów; nie trzeba nic robić, aby skorzystać z bibliotek .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b924-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="4b924-143">Pojedyncze wymaganie polega na tym, że interfejsy API wywoływane przez bibliotekę klas .NET Framework muszą być uwzględnione w standardzie .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="4b924-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="4b924-144">Obsługa języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b924-144">Support for Visual Basic</span></span>

<span data-ttu-id="4b924-145">Teraz można tworzyć biblioteki standardów .NET w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4b924-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="4b924-146">W przypadku deweloperów języka Visual Basic korzystających z programu Visual Studio 2017 w wersji 15.3 lub nowszej z zainstalowanym obciążeniem .NET Core program Visual Studio zawiera teraz szablon standardowej biblioteki klas .NET.</span><span class="sxs-lookup"><span data-stu-id="4b924-146">For Visual Basic developers using Visual Studio 2017 version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="4b924-147">Dla deweloperów języka Visual Basic, którzy używają innych narzędzi programistycznych i środowisk, można użyć [polecenia dotnet new](../../core/tools/dotnet-new.md) do utworzenia projektu biblioteki standardowej .NET.</span><span class="sxs-lookup"><span data-stu-id="4b924-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="4b924-148">Aby uzyskać więcej informacji, zobacz [obsługę narzędzi dla bibliotek standardów .NET](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="4b924-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="4b924-149">Obsługa narzędzi dla bibliotek standardów .NET</span><span class="sxs-lookup"><span data-stu-id="4b924-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="4b924-150">Wraz z wydaniem .NET Core 2.0 i .NET Standard 2.0 zarówno visual studio 2017, jak i [procesor cli .NET Core](../../core/tools/index.md) obsługują tworzenie bibliotek .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4b924-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="4b924-151">W przypadku instalowania programu Visual Studio z wieloplatformowym obciążeniem **programistycznym .NET Core** można utworzyć projekt biblioteki .NET Standard 2.0 przy użyciu szablonu projektu, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="4b924-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="4b924-152">C #</span><span class="sxs-lookup"><span data-stu-id="4b924-152">C#</span></span>](#tab/csharp)

![Dodawanie nowego projektu biblioteki standardu .NET](./media/std-project-cs.png)

<span data-ttu-id="4b924-154">Jeśli używasz polecenia cli .NET Core, następujące [polecenie dotnet tworzy](../../core/tools/dotnet-new.md) projekt biblioteki klas, który jest przeznaczony dla .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="4b924-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="4b924-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b924-155">Visual Basic</span></span>](#tab/vb)

![Dodawanie nowego projektu biblioteki standardu .NET](./media/std-project-vb.png)

<span data-ttu-id="4b924-157">Jeśli używasz polecenia cli .NET Core, następujące [polecenie dotnet tworzy](../../core/tools/dotnet-new.md) projekt biblioteki klas, który jest przeznaczony dla .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="4b924-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="4b924-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b924-158">See also</span></span>

- [<span data-ttu-id="4b924-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="4b924-159">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="4b924-160">Wprowadzenie do standardu .NET</span><span class="sxs-lookup"><span data-stu-id="4b924-160">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
