---
title: Uruchamianie selektywnych testów jednostkowych
description: Jak używać wyrażenia filtru uruchamianie selektywnych testów jednostkowych za pomocą polecenia dotnet testu w programie .NET Core.
author: smadala
ms.date: 03/22/2017
ms.custom: seodec18
ms.openlocfilehash: 1a90438e3b0b2eb095124208010bbe9558424d91
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170206"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="0fedd-103">Uruchamianie selektywnych testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="0fedd-103">Running selective unit tests</span></span>

<span data-ttu-id="0fedd-104">W poniższych przykładach używane `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="0fedd-105">Jeśli używasz `vstest.console.exe`, Zastąp `--filter ` z `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="0fedd-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="0fedd-106">MSTest</span></span>

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

| <span data-ttu-id="0fedd-107">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="0fedd-107">Expression</span></span> | <span data-ttu-id="0fedd-108">Wynik</span><span class="sxs-lookup"><span data-stu-id="0fedd-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="0fedd-109">Przebiegi testów, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="0fedd-110">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="0fedd-111">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="0fedd-112">Uruchamia testy, które są w klasie `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-112">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="0fedd-113">**Uwaga:** `ClassName` Wartości powinny mieć obszaru nazw, więc `ClassName=UnitTest1` nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="0fedd-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="0fedd-114">Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-114">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="0fedd-115">Uruchamia testy, które są przypisane przy użyciu `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="0fedd-116">Uruchamia testy, które są przypisane przy użyciu `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-116">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="0fedd-117">**Za pomocą operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="0fedd-117">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="0fedd-118">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="0fedd-118">Expression</span></span> | <span data-ttu-id="0fedd-119">Wynik</span><span class="sxs-lookup"><span data-stu-id="0fedd-119">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="0fedd-120">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-120">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="0fedd-121">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-121">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="0fedd-122">Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="0fedd-122">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="0fedd-123">xUnit</span><span class="sxs-lookup"><span data-stu-id="0fedd-123">xUnit</span></span>

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

| <span data-ttu-id="0fedd-124">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="0fedd-124">Expression</span></span> | <span data-ttu-id="0fedd-125">Wynik</span><span class="sxs-lookup"><span data-stu-id="0fedd-125">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="0fedd-126">Uruchamia tylko jeden test `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-126">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="0fedd-127">Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-127">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="0fedd-128">Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-128">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="0fedd-129">W przykładzie kodu zdefiniowanych cech przy użyciu kluczy `Category` i `Priority` może służyć do filtrowania.</span><span class="sxs-lookup"><span data-stu-id="0fedd-129">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="0fedd-130">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="0fedd-130">Expression</span></span> | <span data-ttu-id="0fedd-131">Wynik</span><span class="sxs-lookup"><span data-stu-id="0fedd-131">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="0fedd-132">Przebiegi testów, których `FullyQualifiedName` zawiera `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-132">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="0fedd-133">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-133">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="0fedd-134">Uruchamia testy, które mają `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-134">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="0fedd-135">**Za pomocą operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="0fedd-135">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="0fedd-136">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="0fedd-136">Expression</span></span> | <span data-ttu-id="0fedd-137">Wynik</span><span class="sxs-lookup"><span data-stu-id="0fedd-137">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="0fedd-138">Przebiegów testów, które ma `TestClass1` w `FullyQualifiedName` **lub** `Category` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-138">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="0fedd-139">Przebiegów testów, które ma `TestClass1` w `FullyQualifiedName` **i** `Category` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="0fedd-140">Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `TestClass1` **i** `Category` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="0fedd-140">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="0fedd-141">Rozszerzenie NUnit</span><span class="sxs-lookup"><span data-stu-id="0fedd-141">NUnit</span></span>

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

| <span data-ttu-id="0fedd-142">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="0fedd-142">Expression</span></span> | <span data-ttu-id="0fedd-143">Wynik</span><span class="sxs-lookup"><span data-stu-id="0fedd-143">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="0fedd-144">Przebiegi testów, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-144">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="0fedd-145">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-145">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="0fedd-146">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-146">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="0fedd-147">Uruchamia testy, które są w klasie `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-147">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="0fedd-148">Uruchamia wszystkie testy z wyjątkiem `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-148">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="0fedd-149">Uruchamia testy, które są przypisane przy użyciu `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-149">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="0fedd-150">Uruchamia testy, które są przypisane przy użyciu `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-150">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="0fedd-151">**Za pomocą operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="0fedd-151">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="0fedd-152">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="0fedd-152">Expression</span></span> | <span data-ttu-id="0fedd-153">Wynik</span><span class="sxs-lookup"><span data-stu-id="0fedd-153">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="0fedd-154">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-154">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="0fedd-155">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="0fedd-155">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="0fedd-156">Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="0fedd-156">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
