---
title: Uruchamianie selektywnych testów jednostkowych
description: Jak używać wyrażenia filtru do uruchamiania selektywnych testów jednostkowych za pomocą polecenia Test dotnet w programie .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: b9156300587215e68c01c609e298dbc1a2c53d11
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543511"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="7cff6-103">Uruchamianie selektywnych testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="7cff6-103">Running selective unit tests</span></span>

<span data-ttu-id="7cff6-104">Za pomocą polecenia `dotnet test` w programie .NET Core można użyć wyrażenia filtru, aby uruchomić testy selektywne.</span><span class="sxs-lookup"><span data-stu-id="7cff6-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="7cff6-105">W tym artykule pokazano, jak odfiltrować, który test jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="7cff6-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="7cff6-106">W poniższych przykładach użyto `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="7cff6-107">Jeśli używasz `vstest.console.exe`, Zastąp `--filter` `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

> [!NOTE]
> <span data-ttu-id="7cff6-108">Użycie filtrów, które zawierają znak wykrzyknika (!) na `*nix` wymaga ucieczki, ponieważ `!` jest zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="7cff6-108">Using filters that include exclamation mark (!) on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="7cff6-109">Na przykład ten filtr pomija wszystkie testy, jeśli przestrzeń nazw zawiera IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-109">For example, this filter skips all tests if the namespace contains IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.</span></span>
> <span data-ttu-id="7cff6-110">Zwróć uwagę na ukośnik odwrotny poprzedzający wykrzyknik.</span><span class="sxs-lookup"><span data-stu-id="7cff6-110">Note the backslash that precedes the exclamation mark.</span></span>

## <a name="mstest"></a><span data-ttu-id="7cff6-111">MSTest</span><span class="sxs-lookup"><span data-stu-id="7cff6-111">MSTest</span></span>

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

| <span data-ttu-id="7cff6-112">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="7cff6-112">Expression</span></span> | <span data-ttu-id="7cff6-113">Wynik</span><span class="sxs-lookup"><span data-stu-id="7cff6-113">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="7cff6-114">Uruchamia testy, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-114">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="7cff6-115">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-115">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="7cff6-116">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-116">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="7cff6-117">Uruchamia testy, które znajdują się w klasie `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-117">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="7cff6-118">**Uwaga:** Wartość `ClassName` powinna mieć przestrzeń nazw, dlatego `ClassName=UnitTest1` nie będzie działała.</span><span class="sxs-lookup"><span data-stu-id="7cff6-118">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="7cff6-119">Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-119">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="7cff6-120">Uruchamia testy, które są opatrzone adnotacją `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-120">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="7cff6-121">Uruchamia testy, które są opatrzone adnotacją `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-121">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="7cff6-122">**Używanie operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="7cff6-122">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="7cff6-123">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="7cff6-123">Expression</span></span> | <span data-ttu-id="7cff6-124">Wynik</span><span class="sxs-lookup"><span data-stu-id="7cff6-124">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="7cff6-125">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-125">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="7cff6-126">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-126">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="7cff6-127">Uruchamia testy, które mają `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` to 1.</span><span class="sxs-lookup"><span data-stu-id="7cff6-127">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="7cff6-128">xUnit</span><span class="sxs-lookup"><span data-stu-id="7cff6-128">xUnit</span></span>

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

| <span data-ttu-id="7cff6-129">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="7cff6-129">Expression</span></span> | <span data-ttu-id="7cff6-130">Wynik</span><span class="sxs-lookup"><span data-stu-id="7cff6-130">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="7cff6-131">Uruchamia tylko jeden test, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-131">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="7cff6-132">Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-132">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="7cff6-133">Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-133">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="7cff6-134">W przykładzie kodu zdefiniowane cechy z kluczami `Category` i `Priority` mogą służyć do filtrowania.</span><span class="sxs-lookup"><span data-stu-id="7cff6-134">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="7cff6-135">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="7cff6-135">Expression</span></span> | <span data-ttu-id="7cff6-136">Wynik</span><span class="sxs-lookup"><span data-stu-id="7cff6-136">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="7cff6-137">Uruchamia testy, których `FullyQualifiedName` zawiera `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-137">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="7cff6-138">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-138">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="7cff6-139">Uruchamia testy, które mają `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-139">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="7cff6-140">**Używanie operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="7cff6-140">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="7cff6-141">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="7cff6-141">Expression</span></span> | <span data-ttu-id="7cff6-142">Wynik</span><span class="sxs-lookup"><span data-stu-id="7cff6-142">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="7cff6-143">Uruchamia testy, które mają `TestClass1` w `FullyQualifiedName` **lub** `Category` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-143">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="7cff6-144">Uruchamia testy, które mają `TestClass1` w `FullyQualifiedName` **i** `Category` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-144">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="7cff6-145">Uruchamia testy, które mają `FullyQualifiedName` zawierający `TestClass1` **i** `Category` jest `CategoryA` **lub** `Priority` to 1.</span><span class="sxs-lookup"><span data-stu-id="7cff6-145">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="7cff6-146">Rozszerzenie NUnit</span><span class="sxs-lookup"><span data-stu-id="7cff6-146">NUnit</span></span>

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

| <span data-ttu-id="7cff6-147">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="7cff6-147">Expression</span></span> | <span data-ttu-id="7cff6-148">Wynik</span><span class="sxs-lookup"><span data-stu-id="7cff6-148">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="7cff6-149">Uruchamia testy, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-149">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="7cff6-150">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-150">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="7cff6-151">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-151">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="7cff6-152">Uruchamia testy, które znajdują się w klasie `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-152">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="7cff6-153">Uruchamia wszystkie testy z wyjątkiem `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-153">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="7cff6-154">Uruchamia testy, które są opatrzone adnotacją `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-154">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="7cff6-155">Uruchamia testy, które są opatrzone adnotacją `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-155">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="7cff6-156">**Używanie operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="7cff6-156">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="7cff6-157">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="7cff6-157">Expression</span></span> | <span data-ttu-id="7cff6-158">Wynik</span><span class="sxs-lookup"><span data-stu-id="7cff6-158">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="7cff6-159">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-159">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="7cff6-160">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="7cff6-160">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="7cff6-161">Uruchamia testy, które mają `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` to 1.</span><span class="sxs-lookup"><span data-stu-id="7cff6-161">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
