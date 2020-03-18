---
title: Uruchamianie selektywnych testów jednostkowych
description: Jak używać wyrażenia filtru do uruchamiania testów jednostek selektywnych za pomocą polecenia testu dotnet w .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: b9156300587215e68c01c609e298dbc1a2c53d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543511"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="2490c-103">Uruchamianie selektywnych testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="2490c-103">Running selective unit tests</span></span>

<span data-ttu-id="2490c-104">Za `dotnet test` pomocą polecenia w .NET Core można użyć wyrażenia filtru do uruchamiania testów selektywnych.</span><span class="sxs-lookup"><span data-stu-id="2490c-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="2490c-105">W tym artykule pokazano, jak filtrować, które testy są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="2490c-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="2490c-106">W poniższych `dotnet test`przykładach używa się .</span><span class="sxs-lookup"><span data-stu-id="2490c-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="2490c-107">Jeśli używasz `vstest.console.exe`, zamień `--filter` na `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="2490c-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

> [!NOTE]
> <span data-ttu-id="2490c-108">Korzystanie z filtrów, które zawierają `*nix` wykrzyknik (!) na wymaga ucieczki, ponieważ `!` jest zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="2490c-108">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="2490c-109">Na przykład ten filtr pomija wszystkie testy, jeśli `dotnet test --filter FullyQualifiedName\!~IntegrationTests`obszar nazw zawiera IntegrationTests: .</span><span class="sxs-lookup"><span data-stu-id="2490c-109">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
> <span data-ttu-id="2490c-110">Zwróć uwagę na ukośnik odwrotny, który poprzedza wykrzyknik.</span><span class="sxs-lookup"><span data-stu-id="2490c-110">Note the backslash that precedes the exclamation mark.</span></span>

## <a name="mstest"></a><span data-ttu-id="2490c-111">MSTest</span><span class="sxs-lookup"><span data-stu-id="2490c-111">MSTest</span></span>

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

| <span data-ttu-id="2490c-112">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="2490c-112">Expression</span></span> | <span data-ttu-id="2490c-113">Wynik</span><span class="sxs-lookup"><span data-stu-id="2490c-113">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="2490c-114">Uruchamia testy, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="2490c-114">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="2490c-115">Dostępne `vstest 15.1+`w .</span><span class="sxs-lookup"><span data-stu-id="2490c-115">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="2490c-116">Uruchamia testy, `TestMethod1`których nazwa zawiera .</span><span class="sxs-lookup"><span data-stu-id="2490c-116">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="2490c-117">Uruchamia testy, które `MSTestNamespace.UnitTest1`są w klasie .</span><span class="sxs-lookup"><span data-stu-id="2490c-117">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="2490c-118">**Uwaga:** Wartość `ClassName` powinna mieć obszar nazw, więc `ClassName=UnitTest1` nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="2490c-118">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="2490c-119">Uruchamia wszystkie `MSTestNamespace.UnitTest1.TestMethod1`testy z wyjątkiem .</span><span class="sxs-lookup"><span data-stu-id="2490c-119">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="2490c-120">Uruchamia testy, które są `[TestCategory("CategoryA")]`z adnotatorem .</span><span class="sxs-lookup"><span data-stu-id="2490c-120">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="2490c-121">Uruchamia testy, które są `[Priority(2)]`z adnotatorem .</span><span class="sxs-lookup"><span data-stu-id="2490c-121">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="2490c-122">**Korzystanie z operatorów warunkowych | I&amp;**</span><span class="sxs-lookup"><span data-stu-id="2490c-122">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="2490c-123">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="2490c-123">Expression</span></span> | <span data-ttu-id="2490c-124">Wynik</span><span class="sxs-lookup"><span data-stu-id="2490c-124">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="2490c-125">Uruchamia testy, `UnitTest1` `FullyQualifiedName` które `CategoryA`mają **lub** `TestCategory` są .</span><span class="sxs-lookup"><span data-stu-id="2490c-125">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="2490c-126">Uruchamia testy, `UnitTest1` `FullyQualifiedName` które `CategoryA`mają **i** `TestCategory` jest .</span><span class="sxs-lookup"><span data-stu-id="2490c-126">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="2490c-127">Uruchamia testy, `FullyQualifiedName` które `UnitTest1` zawierają `CategoryA` **i** `TestCategory` jest **lub** `Priority` jest 1.</span><span class="sxs-lookup"><span data-stu-id="2490c-127">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="2490c-128">Xunit</span><span class="sxs-lookup"><span data-stu-id="2490c-128">xUnit</span></span>

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

| <span data-ttu-id="2490c-129">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="2490c-129">Expression</span></span> | <span data-ttu-id="2490c-130">Wynik</span><span class="sxs-lookup"><span data-stu-id="2490c-130">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="2490c-131">Uruchamia tylko jeden `XUnitNamespace.TestClass1.Test1`test, .</span><span class="sxs-lookup"><span data-stu-id="2490c-131">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="2490c-132">Uruchamia wszystkie `XUnitNamespace.TestClass1.Test1`testy z wyjątkiem .</span><span class="sxs-lookup"><span data-stu-id="2490c-132">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="2490c-133">Uruchamia testy, których `TestClass1`nazwa wyświetlana zawiera .</span><span class="sxs-lookup"><span data-stu-id="2490c-133">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="2490c-134">W przykładzie kodu zdefiniowane cechy z `Category` `Priority` kluczami i mogą być używane do filtrowania.</span><span class="sxs-lookup"><span data-stu-id="2490c-134">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="2490c-135">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="2490c-135">Expression</span></span> | <span data-ttu-id="2490c-136">Wynik</span><span class="sxs-lookup"><span data-stu-id="2490c-136">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="2490c-137">Uruchamia testy, których `FullyQualifiedName` zawiera `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="2490c-137">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="2490c-138">Dostępne `vstest 15.1+`w .</span><span class="sxs-lookup"><span data-stu-id="2490c-138">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="2490c-139">Uruchamia testy, `[Trait("Category", "CategoryA")]`które mają .</span><span class="sxs-lookup"><span data-stu-id="2490c-139">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="2490c-140">**Korzystanie z operatorów warunkowych | I&amp;**</span><span class="sxs-lookup"><span data-stu-id="2490c-140">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="2490c-141">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="2490c-141">Expression</span></span> | <span data-ttu-id="2490c-142">Wynik</span><span class="sxs-lookup"><span data-stu-id="2490c-142">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="2490c-143">Uruchamia testy, `TestClass1` `FullyQualifiedName` które `CategoryA`mają **lub** `Category` są .</span><span class="sxs-lookup"><span data-stu-id="2490c-143">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="2490c-144">Uruchamia testy, `TestClass1` `FullyQualifiedName` które `CategoryA`ma **i** `Category` jest .</span><span class="sxs-lookup"><span data-stu-id="2490c-144">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="2490c-145">Uruchamia testy, `FullyQualifiedName` które `TestClass1` zawierają `CategoryA` **i** `Category` jest **lub** `Priority` jest 1.</span><span class="sxs-lookup"><span data-stu-id="2490c-145">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="2490c-146">Nunit</span><span class="sxs-lookup"><span data-stu-id="2490c-146">NUnit</span></span>

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

| <span data-ttu-id="2490c-147">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="2490c-147">Expression</span></span> | <span data-ttu-id="2490c-148">Wynik</span><span class="sxs-lookup"><span data-stu-id="2490c-148">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="2490c-149">Uruchamia testy, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="2490c-149">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="2490c-150">Dostępne `vstest 15.1+`w .</span><span class="sxs-lookup"><span data-stu-id="2490c-150">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="2490c-151">Uruchamia testy, `TestMethod1`których nazwa zawiera .</span><span class="sxs-lookup"><span data-stu-id="2490c-151">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="2490c-152">Uruchamia testy, które `NUnitNamespace.UnitTest1`są w klasie .</span><span class="sxs-lookup"><span data-stu-id="2490c-152">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="2490c-153">Uruchamia wszystkie `NUnitNamespace.UnitTest1.TestMethod1`testy z wyjątkiem .</span><span class="sxs-lookup"><span data-stu-id="2490c-153">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="2490c-154">Uruchamia testy, które są `[Category("CategoryA")]`z adnotatorem .</span><span class="sxs-lookup"><span data-stu-id="2490c-154">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="2490c-155">Uruchamia testy, które są `[Priority(2)]`z adnotatorem .</span><span class="sxs-lookup"><span data-stu-id="2490c-155">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="2490c-156">**Korzystanie z operatorów warunkowych | I&amp;**</span><span class="sxs-lookup"><span data-stu-id="2490c-156">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="2490c-157">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="2490c-157">Expression</span></span> | <span data-ttu-id="2490c-158">Wynik</span><span class="sxs-lookup"><span data-stu-id="2490c-158">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="2490c-159">Uruchamia testy, `UnitTest1` `FullyQualifiedName` które `CategoryA`mają **lub** `TestCategory` są .</span><span class="sxs-lookup"><span data-stu-id="2490c-159">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="2490c-160">Uruchamia testy, `UnitTest1` `FullyQualifiedName` które `CategoryA`mają **i** `TestCategory` jest .</span><span class="sxs-lookup"><span data-stu-id="2490c-160">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="2490c-161">Uruchamia testy, `FullyQualifiedName` które `UnitTest1` zawierają `CategoryA` **i** `TestCategory` jest **lub** `Priority` jest 1.</span><span class="sxs-lookup"><span data-stu-id="2490c-161">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
