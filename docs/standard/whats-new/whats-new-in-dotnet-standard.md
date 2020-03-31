---
title: Co nowego w umyka . NET Standard
description: W tym artykule podsumowano nowe funkcje i ulepszenia znalezione w każdej nowej wersji programu .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 28d6a3546e08bbc3a7d4a26f08ba9cc5e16a901b
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438202"
---
# <a name="whats-new-in-net-standard"></a><span data-ttu-id="bd228-103">Co nowego w umyka . NET Standard</span><span class="sxs-lookup"><span data-stu-id="bd228-103">What's new in .NET Standard</span></span>

<span data-ttu-id="bd228-104">.NET Standard to formalna specyfikacja, która definiuje wersjonatowany zestaw interfejsów API, które muszą być dostępne w implementacjach platformy .NET zgodnych z tą wersją standardu.</span><span class="sxs-lookup"><span data-stu-id="bd228-104">.NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="bd228-105">Program .NET Standard jest przeznaczony dla deweloperów bibliotek.</span><span class="sxs-lookup"><span data-stu-id="bd228-105">.NET Standard is targeted at library developers.</span></span> <span data-ttu-id="bd228-106">Biblioteka przeznaczona dla wersji .NET Standard może być używana w dowolnej implementacji platformy .NET Framework, .NET Core lub Xamarin, która obsługuje tę wersję standardu.</span><span class="sxs-lookup"><span data-stu-id="bd228-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="bd228-107">Program .NET Standard jest dołączony do rdzenia SDK .NET, a także z programem Visual Studio po wybraniu obciążenia .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd228-107">.NET Standard is included with the .NET Core SDK, as well as with Visual Studio when you select the .NET Core workload.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="bd228-108">Obsługiwane implementacje platformy .NET</span><span class="sxs-lookup"><span data-stu-id="bd228-108">Supported .NET implementations</span></span>

<span data-ttu-id="bd228-109">.NET Standard 2.0 jest obsługiwany przez następujące implementacje .NET:</span><span class="sxs-lookup"><span data-stu-id="bd228-109">.NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="bd228-110">.NET Core 2.0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="bd228-110">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="bd228-111">.NET Framework 4.6.1 lub nowsze</span><span class="sxs-lookup"><span data-stu-id="bd228-111">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="bd228-112">Mono 5.4 lub nowsze</span><span class="sxs-lookup"><span data-stu-id="bd228-112">Mono 5.4 or later</span></span>
- <span data-ttu-id="bd228-113">Xamarin.iOS 10.14 lub nowsze</span><span class="sxs-lookup"><span data-stu-id="bd228-113">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="bd228-114">Xamarin.Mac 3.8 lub nowsze</span><span class="sxs-lookup"><span data-stu-id="bd228-114">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="bd228-115">Xamarin.Android 8.0 lub nowsze</span><span class="sxs-lookup"><span data-stu-id="bd228-115">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="bd228-116">Uniwersalna platforma systemu Windows 10.0.16299 lub nowsza</span><span class="sxs-lookup"><span data-stu-id="bd228-116">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-net-standard-20"></a><span data-ttu-id="bd228-117">Co nowego w .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="bd228-117">What's new in .NET Standard 2.0</span></span>

<span data-ttu-id="bd228-118">Program .NET Standard 2.0 zawiera następujące nowe funkcje:</span><span class="sxs-lookup"><span data-stu-id="bd228-118">.NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="bd228-119">Znacznie rozszerzony zestaw interfejsów API</span><span class="sxs-lookup"><span data-stu-id="bd228-119">A vastly expanded set of APIs</span></span>

<span data-ttu-id="bd228-120">W wersji 1.6 program .NET Standard zawierał stosunkowo mały podzbiór interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="bd228-120">Through version 1.6, .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="bd228-121">Wśród wykluczonych było wiele interfejsów API, które były powszechnie używane w .NET Framework lub platformy Xamarin.</span><span class="sxs-lookup"><span data-stu-id="bd228-121">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="bd228-122">To komplikuje rozwój, ponieważ wymaga, aby deweloperzy znaleźć odpowiednie zamienniki dla znanych interfejsów API podczas tworzenia aplikacji i bibliotek, które są przeznaczone dla wielu implementacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="bd228-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="bd228-123">Program .NET Standard 2.0 rozwiązuje to ograniczenie, dodając ponad 20 000 więcej interfejsów API niż w standardzie .NET Standard 1.6, poprzedniej wersji standardu.</span><span class="sxs-lookup"><span data-stu-id="bd228-123">.NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="bd228-124">Aby uzyskać listę interfejsów API, które zostały dodane do programu .NET Standard 2.0, zobacz [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="bd228-124">For a list of the APIs that have been added to .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="bd228-125">Niektóre dodatki do obszaru <xref:System> nazw w .NET Standard 2.0 obejmują:</span><span class="sxs-lookup"><span data-stu-id="bd228-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="bd228-126">Wsparcie dla <xref:System.AppDomain> klasy.</span><span class="sxs-lookup"><span data-stu-id="bd228-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="bd228-127">Lepsza obsługa pracy z tablicami od <xref:System.Array> dodatkowych członków w klasie.</span><span class="sxs-lookup"><span data-stu-id="bd228-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="bd228-128">Lepsza obsługa pracy z atrybutami <xref:System.Attribute> od dodatkowych członków w klasie.</span><span class="sxs-lookup"><span data-stu-id="bd228-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="bd228-129">Lepsza obsługa kalendarza i <xref:System.DateTime> dodatkowe opcje formatowania wartości.</span><span class="sxs-lookup"><span data-stu-id="bd228-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="bd228-130">Dodatkowa <xref:System.Decimal> funkcja zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="bd228-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="bd228-131">Dodatkowe funkcje <xref:System.Environment> w klasie.</span><span class="sxs-lookup"><span data-stu-id="bd228-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="bd228-132">Zwiększona kontrola nad modułem <xref:System.GC> zbierającym elementy bezużyteczne za pośrednictwem klasy.</span><span class="sxs-lookup"><span data-stu-id="bd228-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="bd228-133">Ulepszona obsługa porównywania ciągów, wyliczania <xref:System.String> i normalizacji w klasie.</span><span class="sxs-lookup"><span data-stu-id="bd228-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="bd228-134">Obsługa regulacji czasu letniego i <xref:System.TimeZoneInfo.AdjustmentRule> czasów <xref:System.TimeZoneInfo.TransitionTime> przejścia w klasach i.</span><span class="sxs-lookup"><span data-stu-id="bd228-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="bd228-135">Znacznie zwiększona funkcjonalność w <xref:System.Type> klasie.</span><span class="sxs-lookup"><span data-stu-id="bd228-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="bd228-136">Lepsza obsługa deserializacji obiektów wyjątków przez dodanie <xref:System.Runtime.Serialization.SerializationInfo> <xref:System.Runtime.Serialization.StreamingContext> konstruktora wyjątków z i parametrów.</span><span class="sxs-lookup"><span data-stu-id="bd228-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="bd228-137">Obsługa bibliotek programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bd228-137">Support for .NET Framework libraries</span></span>

<span data-ttu-id="bd228-138">Przeważająca większość bibliotek docelowych .NET Framework, a nie .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="bd228-138">The overwhelming majority of libraries target .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="bd228-139">Jednak większość wywołań w tych bibliotekach są interfejsy API, które są zawarte w .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="bd228-139">However, most of the calls in those libraries are to APIs that are included in .NET Standard 2.0.</span></span> <span data-ttu-id="bd228-140">Począwszy od platformy .NET Standard 2.0, można uzyskać dostęp do bibliotek programu .NET Framework z biblioteki .NET Standard przy użyciu [podkładki zgodności](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="bd228-140">Starting with .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="bd228-141">Ta warstwa zgodności jest przezroczysta dla deweloperów; nie musisz nic robić, aby korzystać z bibliotek .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bd228-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="bd228-142">Jednym wymaganiem jest, że interfejsy API wywoływane przez bibliotekę klas .NET Framework muszą być uwzględnione w .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="bd228-142">The single requirement is that the APIs called by the .NET Framework class library must be included in .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="bd228-143">Obsługa języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd228-143">Support for Visual Basic</span></span>

<span data-ttu-id="bd228-144">Teraz można tworzyć biblioteki .NET Standard w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bd228-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="bd228-145">Visual Studio 2019 i Visual Studio 2017 w wersji 15.3 lub nowszej z zainstalowanym obciążeniem .NET Core zawierają szablon biblioteki klas standardowych platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="bd228-145">Visual Studio 2019 and Visual Studio 2017 version 15.3 or later with the .NET Core workload installed include a .NET Standard Class Library template.</span></span> <span data-ttu-id="bd228-146">W przypadku deweloperów języka Visual Basic, którzy używają innych narzędzi i środowisk programistycznych, można użyć nowego polecenia [dotnet](../../core/tools/dotnet-new.md) do utworzenia projektu biblioteki standardowej platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="bd228-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="bd228-147">Aby uzyskać więcej informacji, zobacz [obsługę narzędzi dla bibliotek .NET Standard](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="bd228-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="bd228-148">Obsługa narzędzi dla bibliotek standardowych platformy .NET</span><span class="sxs-lookup"><span data-stu-id="bd228-148">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="bd228-149">Wraz z wydaniem platformy .NET Core 2.0 i .NET Standard 2.0 zarówno program Visual Studio 2017, jak i [.NET Core CLI](../../core/tools/index.md) obejmują obsługę narzędzi do tworzenia bibliotek .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="bd228-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="bd228-150">W przypadku instalowania programu Visual Studio z **wieloplatformowym** obciążeniem programowym .NET Core można utworzyć projekt biblioteki .NET Standard 2.0 przy użyciu szablonu projektu, jak pokazano na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="bd228-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="bd228-151">C #</span><span class="sxs-lookup"><span data-stu-id="bd228-151">C#</span></span>](#tab/csharp)

![Dodawanie nowego projektu biblioteki standardu .NET](./media/std-project-cs.png)

<span data-ttu-id="bd228-153">Jeśli używasz interfejsu wiersza polecenia .NET Core, następujące polecenie [dotnet new](../../core/tools/dotnet-new.md) tworzy projekt biblioteki klas, który jest przeznaczony dla platformy .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="bd228-153">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="bd228-154">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bd228-154">Visual Basic</span></span>](#tab/vb)

![Dodawanie nowego projektu biblioteki standardu .NET](./media/std-project-vb.png)

<span data-ttu-id="bd228-156">Jeśli używasz interfejsu wiersza polecenia .NET Core, następujące polecenie [dotnet new](../../core/tools/dotnet-new.md) tworzy projekt biblioteki klas, który jest przeznaczony dla platformy .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="bd228-156">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="bd228-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd228-157">See also</span></span>

- [<span data-ttu-id="bd228-158">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="bd228-158">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="bd228-159">Przedstawiamy standard .NET</span><span class="sxs-lookup"><span data-stu-id="bd228-159">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
