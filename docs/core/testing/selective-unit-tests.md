---
title: Uruchamianie selektywnych testów jednostkowych
description: Jak używać wyrażenia filtru do uruchamiania selektywnych testów jednostkowych za pomocą polecenia Test dotnet w programie .NET Core.
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: 50642126f3b470180ddd303ed4a2d2d90bfa5b8f
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728183"
---
# <a name="run-selective-unit-tests"></a><span data-ttu-id="dea5c-103">Uruchamianie selektywnych testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="dea5c-103">Run selective unit tests</span></span>

<span data-ttu-id="dea5c-104">Za pomocą `dotnet test` polecenia w programie .NET Core można używać wyrażenia filtru do uruchamiania selektywnych testów.</span><span class="sxs-lookup"><span data-stu-id="dea5c-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="dea5c-105">W tym artykule przedstawiono sposób filtrowania, które testy są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="dea5c-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="dea5c-106">W poniższych przykładach `dotnet test`użyto.</span><span class="sxs-lookup"><span data-stu-id="dea5c-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="dea5c-107">Jeśli używasz programu `vstest.console.exe`, Zamień `--filter` na. `--testcasefilter:`</span><span class="sxs-lookup"><span data-stu-id="dea5c-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="dea5c-108">Znak ucieczki</span><span class="sxs-lookup"><span data-stu-id="dea5c-108">Character escaping</span></span>

<span data-ttu-id="dea5c-109">Użycie filtrów, które zawierają znak wykrzyknika (! `*nix` ), wymaga ucieczki, ponieważ `!` jest zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="dea5c-109">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="dea5c-110">Na przykład ten filtr pomija wszystkie testy, jeśli przestrzeń nazw zawiera IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span><span class="sxs-lookup"><span data-stu-id="dea5c-110">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
<span data-ttu-id="dea5c-111">Zwróć uwagę na ukośnik odwrotny poprzedzający wykrzyknik.</span><span class="sxs-lookup"><span data-stu-id="dea5c-111">Note the backslash that precedes the exclamation mark.</span></span>

<span data-ttu-id="dea5c-112">Dla `FullyQualifiedName` wartości, które zawierają przecinek dla parametrów typu generycznego, wpisz przecinek `%2C`.</span><span class="sxs-lookup"><span data-stu-id="dea5c-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="dea5c-113">Przykład:</span><span class="sxs-lookup"><span data-stu-id="dea5c-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

## <a name="mstest"></a><span data-ttu-id="dea5c-114">MSTest</span><span class="sxs-lookup"><span data-stu-id="dea5c-114">MSTest</span></span>

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestCategory("CategoryA")]
        [Priority(1)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [Priority(2)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="dea5c-115">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="dea5c-115">Expression</span></span> | <span data-ttu-id="dea5c-116">Wynik</span><span class="sxs-lookup"><span data-stu-id="dea5c-116">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="dea5c-117">Uruchamia testy, `FullyQualifiedName` których `Method`zawiera.</span><span class="sxs-lookup"><span data-stu-id="dea5c-117">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="dea5c-118">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="dea5c-118">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="dea5c-119">Uruchamia testy, których nazwa `TestMethod1`zawiera.</span><span class="sxs-lookup"><span data-stu-id="dea5c-119">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="dea5c-120">Uruchamia testy, które znajdują `MSTestNamespace.UnitTest1`się w klasie.</span><span class="sxs-lookup"><span data-stu-id="dea5c-120">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="dea5c-121">**Uwaga:** `ClassName` Wartość powinna mieć przestrzeń nazw, dlatego `ClassName=UnitTest1` nie będzie działała.</span><span class="sxs-lookup"><span data-stu-id="dea5c-121">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="dea5c-122">Uruchamia wszystkie testy z `MSTestNamespace.UnitTest1.TestMethod1`wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="dea5c-122">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="dea5c-123">Uruchamia testy, które są opatrzone `[TestCategory("CategoryA")]`adnotacją.</span><span class="sxs-lookup"><span data-stu-id="dea5c-123">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="dea5c-124">Uruchamia testy, które są opatrzone `[Priority(2)]`adnotacją.</span><span class="sxs-lookup"><span data-stu-id="dea5c-124">Runs tests that are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="dea5c-125">**Używanie operatorów warunkowych | lub&amp;**</span><span class="sxs-lookup"><span data-stu-id="dea5c-125">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="dea5c-126">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="dea5c-126">Expression</span></span> | <span data-ttu-id="dea5c-127">Wynik</span><span class="sxs-lookup"><span data-stu-id="dea5c-127">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="dea5c-128">Uruchamia testy, które `UnitTest1` mają `FullyQualifiedName` w **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="dea5c-128">Runs tests that have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="dea5c-129">Uruchamia testy, które `UnitTest1` mają `FullyQualifiedName` w **i** `TestCategory` to `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="dea5c-129">Runs tests that have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="dea5c-130">Uruchamia testy z parametrami `FullyQualifiedName` zawierającymi `UnitTest1` **i** `TestCategory` is `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="dea5c-130">Runs tests that have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="dea5c-131">xUnit</span><span class="sxs-lookup"><span data-stu-id="dea5c-131">xUnit</span></span>

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "CategoryA")]
        [Trait("Priority", "1")]
        [Fact]
        public void Test1()
        {
        }

        [Trait("Priority", "2")]
        [Fact]
        public void Test2()
        {
        }
    }
}
```

| <span data-ttu-id="dea5c-132">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="dea5c-132">Expression</span></span> | <span data-ttu-id="dea5c-133">Wynik</span><span class="sxs-lookup"><span data-stu-id="dea5c-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="dea5c-134">Uruchamia tylko jeden test, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="dea5c-134">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="dea5c-135">Uruchamia wszystkie testy z `XUnitNamespace.TestClass1.Test1`wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="dea5c-135">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="dea5c-136">Uruchamia testy, których nazwa wyświetlana `TestClass1`zawiera.</span><span class="sxs-lookup"><span data-stu-id="dea5c-136">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="dea5c-137">W przykładzie kodu, zdefiniowane cechy z kluczami `Category` i `Priority` mogą być używane do filtrowania.</span><span class="sxs-lookup"><span data-stu-id="dea5c-137">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="dea5c-138">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="dea5c-138">Expression</span></span> | <span data-ttu-id="dea5c-139">Wynik</span><span class="sxs-lookup"><span data-stu-id="dea5c-139">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="dea5c-140">Uruchamia testy, `FullyQualifiedName` których `XUnit`zawiera.</span><span class="sxs-lookup"><span data-stu-id="dea5c-140">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="dea5c-141">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="dea5c-141">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="dea5c-142">Uruchamia testy, które `[Trait("Category", "CategoryA")]`mają.</span><span class="sxs-lookup"><span data-stu-id="dea5c-142">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="dea5c-143">**Używanie operatorów warunkowych | lub&amp;**</span><span class="sxs-lookup"><span data-stu-id="dea5c-143">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="dea5c-144">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="dea5c-144">Expression</span></span> | <span data-ttu-id="dea5c-145">Wynik</span><span class="sxs-lookup"><span data-stu-id="dea5c-145">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="dea5c-146">Uruchamia testy, które `TestClass1` mają `FullyQualifiedName` w **lub** `Category` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="dea5c-146">Runs tests that have `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="dea5c-147">Uruchamia testy, które `TestClass1` mają `FullyQualifiedName` w **i** `Category` to `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="dea5c-147">Runs tests that have `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="dea5c-148">Uruchamia testy z parametrami `FullyQualifiedName` zawierającymi `TestClass1` **i** `Category` is `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="dea5c-148">Runs tests that have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="dea5c-149">NUnit</span><span class="sxs-lookup"><span data-stu-id="dea5c-149">NUnit</span></span>

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Category("CategoryA")]
        [Property("Priority", 1)]
        [Test]
        public void TestMethod1()
        {
        }

        [Property("Priority", 2)]
        [Test]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="dea5c-150">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="dea5c-150">Expression</span></span> | <span data-ttu-id="dea5c-151">Wynik</span><span class="sxs-lookup"><span data-stu-id="dea5c-151">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="dea5c-152">Uruchamia testy, `FullyQualifiedName` których `Method`zawiera.</span><span class="sxs-lookup"><span data-stu-id="dea5c-152">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="dea5c-153">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="dea5c-153">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="dea5c-154">Uruchamia testy, których nazwa `TestMethod1`zawiera.</span><span class="sxs-lookup"><span data-stu-id="dea5c-154">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="dea5c-155">Uruchamia testy, które znajdują `NUnitNamespace.UnitTest1`się w klasie.</span><span class="sxs-lookup"><span data-stu-id="dea5c-155">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="dea5c-156">Uruchamia wszystkie testy z `NUnitNamespace.UnitTest1.TestMethod1`wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="dea5c-156">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="dea5c-157">Uruchamia testy, które są opatrzone `[Category("CategoryA")]`adnotacją.</span><span class="sxs-lookup"><span data-stu-id="dea5c-157">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="dea5c-158">Uruchamia testy, które są opatrzone `[Priority(2)]`adnotacją.</span><span class="sxs-lookup"><span data-stu-id="dea5c-158">Runs tests that are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="dea5c-159">**Używanie operatorów warunkowych | lub&amp;**</span><span class="sxs-lookup"><span data-stu-id="dea5c-159">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="dea5c-160">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="dea5c-160">Expression</span></span> | <span data-ttu-id="dea5c-161">Wynik</span><span class="sxs-lookup"><span data-stu-id="dea5c-161">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="dea5c-162">Uruchamia testy, które `UnitTest1` mają `FullyQualifiedName` w **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="dea5c-162">Runs tests that have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="dea5c-163">Uruchamia testy, które `UnitTest1` mają `FullyQualifiedName` w **i** `TestCategory` to `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="dea5c-163">Runs tests that have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="dea5c-164">Uruchamia testy z parametrami `FullyQualifiedName` zawierającymi `UnitTest1` **i** `TestCategory` is `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="dea5c-164">Runs tests that have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

<span data-ttu-id="dea5c-165">Aby uzyskać więcej informacji, zobacz [przypadku testowego Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="dea5c-165">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>
