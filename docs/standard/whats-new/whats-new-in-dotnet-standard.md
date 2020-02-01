---
title: Co nowego w programie .NET Standard
description: Ten artykuł zawiera podsumowanie nowych funkcji i ulepszeń znalezionych w każdej nowej wersji .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: a90df0360211c3b02f4f2d8697890180099c5807
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921060"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="1e059-103">Co nowego w programie .NET Standard</span><span class="sxs-lookup"><span data-stu-id="1e059-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="1e059-104">.NET Standard to formalna Specyfikacja, która definiuje zestaw interfejsów API, które muszą być dostępne w implementacjach platformy .NET, które są zgodne z tą wersją Standard.</span><span class="sxs-lookup"><span data-stu-id="1e059-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="1e059-105">.NET Standard jest przeznaczona dla deweloperów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="1e059-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="1e059-106">Biblioteka, która jest przeznaczona dla wersji .NET Standard, może być używana w ramach implementacji .NET Framework, .NET Core lub Xamarin, która obsługuje tę wersję Standard.</span><span class="sxs-lookup"><span data-stu-id="1e059-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="1e059-107">Najnowsza wersja .NET Standard to 2,0.</span><span class="sxs-lookup"><span data-stu-id="1e059-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="1e059-108">Jest on zawarty w zestawie SDK platformy .NET Core 2,0, a także z programem Visual Studio 2017 w wersji 15,3 z zainstalowanym obciążeniem programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1e059-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="1e059-109">Obsługiwane implementacje platformy .NET</span><span class="sxs-lookup"><span data-stu-id="1e059-109">Supported .NET implementations</span></span>

<span data-ttu-id="1e059-110">.NET Standard 2,0 jest obsługiwana przez następujące implementacje .NET:</span><span class="sxs-lookup"><span data-stu-id="1e059-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="1e059-111">.NET Core 2,0 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="1e059-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="1e059-112">.NET Framework 4.6.1 lub nowsze</span><span class="sxs-lookup"><span data-stu-id="1e059-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="1e059-113">Mono 5,4 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="1e059-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="1e059-114">Platforma Xamarin. iOS 10,14 lub nowsza</span><span class="sxs-lookup"><span data-stu-id="1e059-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="1e059-115">Platforma Xamarin. Mac 3,8 lub nowsza</span><span class="sxs-lookup"><span data-stu-id="1e059-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="1e059-116">Platforma Xamarin. Android 8,0 lub nowsza</span><span class="sxs-lookup"><span data-stu-id="1e059-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="1e059-117">Platforma uniwersalna systemu Windows 10.0.16299 lub nowszy</span><span class="sxs-lookup"><span data-stu-id="1e059-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="1e059-118">Co nowego w .NET Standard 2,0</span><span class="sxs-lookup"><span data-stu-id="1e059-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="1e059-119">.NET Standard 2,0 zawiera następujące nowe funkcje:</span><span class="sxs-lookup"><span data-stu-id="1e059-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="1e059-120">Zestaw interfejsów API o szerokim rozszerzeniu</span><span class="sxs-lookup"><span data-stu-id="1e059-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="1e059-121">W wersji 1,6, .NET Standard obejmowały niewielki podzbiór interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="1e059-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="1e059-122">Wśród tych wykluczonych było wiele interfejsów API, które były często używane w .NET Framework lub Xamarin.</span><span class="sxs-lookup"><span data-stu-id="1e059-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="1e059-123">To komplikuje programowanie, ponieważ wymaga, aby deweloperzy znalazły odpowiednie zamienniki dla znanych interfejsów API podczas opracowywania aplikacji i bibliotek przeznaczonych dla wielu implementacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="1e059-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="1e059-124">.NET Standard 2,0 dotyczy tego ograniczenia przez dodanie ponad 20 000 więcej interfejsów API niż w .NET Standard 1,6, poprzedniej wersji Standard.</span><span class="sxs-lookup"><span data-stu-id="1e059-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="1e059-125">Aby uzyskać listę interfejsów API, które zostały dodane do .NET Standard 2,0, zobacz [.NET Standard 2,0 vs 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="1e059-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="1e059-126">Niektóre dodatki do przestrzeni nazw <xref:System> w .NET Standard 2,0 obejmują:</span><span class="sxs-lookup"><span data-stu-id="1e059-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="1e059-127">Obsługa klasy <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1e059-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="1e059-128">Lepsza obsługa pracy z tablicami z dodatkowych elementów członkowskich w klasie <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="1e059-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="1e059-129">Lepsza obsługa pracy z atrybutami z dodatkowych elementów członkowskich w klasie <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="1e059-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="1e059-130">Lepsza obsługa kalendarza i dodatkowe opcje formatowania dla wartości <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="1e059-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="1e059-131">Dodatkowe funkcje zaokrąglania <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="1e059-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="1e059-132">Dodatkowa funkcjonalność klasy <xref:System.Environment>.</span><span class="sxs-lookup"><span data-stu-id="1e059-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="1e059-133">Rozszerzona kontrola nad modułem wyrzucania elementów bezużytecznych za pośrednictwem klasy <xref:System.GC>.</span><span class="sxs-lookup"><span data-stu-id="1e059-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="1e059-134">Ulepszona obsługa porównywania ciągów, wyliczania i normalizacji w klasie <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="1e059-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="1e059-135">Obsługa zmian czasu letnich i czasów przejścia w klasach <xref:System.TimeZoneInfo.AdjustmentRule> i <xref:System.TimeZoneInfo.TransitionTime>.</span><span class="sxs-lookup"><span data-stu-id="1e059-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="1e059-136">Znacznie rozszerzona funkcjonalność klasy <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="1e059-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="1e059-137">Lepsza obsługa deserializacji obiektów wyjątków przez dodanie konstruktora wyjątków z parametrami <xref:System.Runtime.Serialization.SerializationInfo> i <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="1e059-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="1e059-138">Obsługa bibliotek .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1e059-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="1e059-139">Przeciążanie większości bibliotek celem .NET Framework, a nie .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1e059-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="1e059-140">Większość wywołań w tych bibliotekach obejmuje jednak interfejsy API, które znajdują się w .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="1e059-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="1e059-141">Począwszy od .NET Standard 2,0, można uzyskać dostęp do bibliotek .NET Framework z biblioteki .NET Standard za pomocą [podkładki zgodności](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="1e059-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="1e059-142">Ta warstwa zgodności jest niewidoczna dla deweloperów; nie trzeba wykonywać żadnych czynności, aby korzystać z bibliotek .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1e059-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="1e059-143">Jedynym wymaganiem jest, że interfejsy API wywoływane przez bibliotekę klas .NET Framework muszą być dołączone do .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="1e059-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="1e059-144">Obsługa Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e059-144">Support for Visual Basic</span></span>

<span data-ttu-id="1e059-145">Teraz można opracowywać biblioteki .NET Standard w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1e059-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="1e059-146">W przypadku Visual Basic deweloperów korzystających z programu Visual Studio 2017 w wersji 15,3 lub nowszej z zainstalowanym obciążeniem programu .NET Core program Visual Studio zawiera teraz szablon biblioteki klas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1e059-146">For Visual Basic developers using Visual Studio 2017 version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="1e059-147">Dla Visual Basic deweloperów, którzy korzystają z innych narzędzi programistycznych i środowisk, można użyć polecenia [dotnet New](../../core/tools/dotnet-new.md) , aby utworzyć projekt biblioteki .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1e059-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="1e059-148">Aby uzyskać więcej informacji, zobacz [Obsługa narzędzi dla bibliotek .NET Standard](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="1e059-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="1e059-149">Obsługa narzędzi dla bibliotek .NET Standard</span><span class="sxs-lookup"><span data-stu-id="1e059-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="1e059-150">W przypadku wersji programu .NET Core 2,0 i .NET Standard 2,0 zarówno program Visual Studio 2017, jak i [interfejs wiersza polecenia platformy .NET Core](../../core/tools/index.md) obejmują narzędzia obsługujące tworzenie bibliotek .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1e059-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="1e059-151">W przypadku instalowania programu Visual Studio z użyciem obciążenia **międzyplatformowego platformy .NET Core** można utworzyć projekt biblioteki .NET Standard 2,0 przy użyciu szablonu projektu, tak jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="1e059-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="1e059-152">C#</span><span class="sxs-lookup"><span data-stu-id="1e059-152">C#</span></span>](#tab/csharp)

![Dodaj nowy projekt biblioteki .NET Standard](./media/std-project-cs.png)

<span data-ttu-id="1e059-154">Jeśli używasz interfejs wiersza polecenia platformy .NET Core, następujące polecenie [dotnet New](../../core/tools/dotnet-new.md) powoduje utworzenie projektu biblioteki klas, który jest przeznaczony dla .NET Standard 2,0:</span><span class="sxs-lookup"><span data-stu-id="1e059-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="1e059-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e059-155">Visual Basic</span></span>](#tab/vb)

![Dodaj nowy projekt biblioteki .NET Standard](./media/std-project-vb.png)

<span data-ttu-id="1e059-157">Jeśli używasz interfejs wiersza polecenia platformy .NET Core, następujące polecenie [dotnet New](../../core/tools/dotnet-new.md) powoduje utworzenie projektu biblioteki klas, który jest przeznaczony dla .NET Standard 2,0:</span><span class="sxs-lookup"><span data-stu-id="1e059-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="1e059-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e059-158">See also</span></span>

- [<span data-ttu-id="1e059-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="1e059-159">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="1e059-160">Wprowadzenie .NET Standard</span><span class="sxs-lookup"><span data-stu-id="1e059-160">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
