---
title: Uruchamianie selektywnych testów jednostkowych
description: Jak używać wyrażenia filtru do uruchamiania selektywnych testów jednostkowych za pomocą polecenia Test dotnet w programie .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: 57428dad2de6c2507ca2cdc42e3df9e83a1edd69
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715461"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="10b49-103">Uruchamianie selektywnych testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="10b49-103">Running selective unit tests</span></span>

<span data-ttu-id="10b49-104">Za pomocą polecenia `dotnet test` w programie .NET Core można użyć wyrażenia filtru, aby uruchomić testy selektywne.</span><span class="sxs-lookup"><span data-stu-id="10b49-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="10b49-105">W tym artykule pokazano, jak odfiltrować, który test jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="10b49-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="10b49-106">W poniższych przykładach użyto `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="10b49-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="10b49-107">Jeśli używasz `vstest.console.exe`, Zastąp `--filter` `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="10b49-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="10b49-108">MSTest</span><span class="sxs-lookup"><span data-stu-id="10b49-108">MSTest</span></span>

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

| <span data-ttu-id="10b49-109">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="10b49-109">Expression</span></span> | <span data-ttu-id="10b49-110">Wynik</span><span class="sxs-lookup"><span data-stu-id="10b49-110">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="10b49-111">Uruchamia testy, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="10b49-111">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="10b49-112">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="10b49-112">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="10b49-113">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="10b49-113">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="10b49-114">Uruchamia testy, które znajdują się w klasie `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="10b49-114">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="10b49-115">**Uwaga:** Wartość `ClassName` powinna mieć przestrzeń nazw, dlatego `ClassName=UnitTest1` nie będzie działała.</span><span class="sxs-lookup"><span data-stu-id="10b49-115">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="10b49-116">Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="10b49-116">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="10b49-117">Uruchamia testy, które są opatrzone adnotacją `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="10b49-117">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="10b49-118">Uruchamia testy, które są opatrzone adnotacją `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="10b49-118">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="10b49-119">**Używanie operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="10b49-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="10b49-120">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="10b49-120">Expression</span></span> | <span data-ttu-id="10b49-121">Wynik</span><span class="sxs-lookup"><span data-stu-id="10b49-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="10b49-122">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="10b49-122">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="10b49-123">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="10b49-123">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="10b49-124">Uruchamia testy, które mają `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` to 1.</span><span class="sxs-lookup"><span data-stu-id="10b49-124">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="10b49-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="10b49-125">xUnit</span></span>

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

| <span data-ttu-id="10b49-126">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="10b49-126">Expression</span></span> | <span data-ttu-id="10b49-127">Wynik</span><span class="sxs-lookup"><span data-stu-id="10b49-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="10b49-128">Uruchamia tylko jeden test, `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="10b49-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="10b49-129">Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="10b49-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="10b49-130">Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="10b49-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="10b49-131">W przykładzie kodu zdefiniowane cechy z kluczami `Category` i `Priority` mogą służyć do filtrowania.</span><span class="sxs-lookup"><span data-stu-id="10b49-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="10b49-132">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="10b49-132">Expression</span></span> | <span data-ttu-id="10b49-133">Wynik</span><span class="sxs-lookup"><span data-stu-id="10b49-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="10b49-134">Uruchamia testy, których `FullyQualifiedName` zawiera `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="10b49-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="10b49-135">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="10b49-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="10b49-136">Uruchamia testy, które mają `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="10b49-136">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="10b49-137">**Używanie operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="10b49-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="10b49-138">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="10b49-138">Expression</span></span> | <span data-ttu-id="10b49-139">Wynik</span><span class="sxs-lookup"><span data-stu-id="10b49-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="10b49-140">Uruchamia testy, które mają `TestClass1` w `FullyQualifiedName` **lub** `Category` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="10b49-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="10b49-141">Uruchamia testy, które mają `TestClass1` w `FullyQualifiedName` **i** `Category` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="10b49-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="10b49-142">Uruchamia testy, które mają `FullyQualifiedName` zawierający `TestClass1` **i** `Category` jest `CategoryA` **lub** `Priority` to 1.</span><span class="sxs-lookup"><span data-stu-id="10b49-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="10b49-143">Rozszerzenie NUnit</span><span class="sxs-lookup"><span data-stu-id="10b49-143">NUnit</span></span>

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

| <span data-ttu-id="10b49-144">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="10b49-144">Expression</span></span> | <span data-ttu-id="10b49-145">Wynik</span><span class="sxs-lookup"><span data-stu-id="10b49-145">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="10b49-146">Uruchamia testy, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="10b49-146">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="10b49-147">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="10b49-147">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="10b49-148">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="10b49-148">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="10b49-149">Uruchamia testy, które znajdują się w klasie `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="10b49-149">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="10b49-150">Uruchamia wszystkie testy z wyjątkiem `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="10b49-150">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="10b49-151">Uruchamia testy, które są opatrzone adnotacją `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="10b49-151">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="10b49-152">Uruchamia testy, które są opatrzone adnotacją `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="10b49-152">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="10b49-153">**Używanie operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="10b49-153">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="10b49-154">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="10b49-154">Expression</span></span> | <span data-ttu-id="10b49-155">Wynik</span><span class="sxs-lookup"><span data-stu-id="10b49-155">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="10b49-156">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="10b49-156">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="10b49-157">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="10b49-157">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="10b49-158">Uruchamia testy, które mają `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` to 1.</span><span class="sxs-lookup"><span data-stu-id="10b49-158">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
