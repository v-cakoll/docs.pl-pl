---
title: Uruchamianie selektywnych testów jednostkowych
description: Dowiesz się, jak uruchamianie selektywnych testów jednostkowych za pomocą polecenia dotnet test za pomocą wyrażenia filtru.
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.openlocfilehash: 428e31014f5d8d487deb7c4b4317ebcef13c294d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517223"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="588d3-103">Uruchamianie selektywnych testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="588d3-103">Running selective unit tests</span></span>

<span data-ttu-id="588d3-104">W poniższych przykładach używane `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="588d3-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="588d3-105">Jeśli używasz `vstest.console.exe`, Zastąp `--filter ` z `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="588d3-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="588d3-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="588d3-106">MSTest</span></span>

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

| <span data-ttu-id="588d3-107">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="588d3-107">Expression</span></span> | <span data-ttu-id="588d3-108">Wynik</span><span class="sxs-lookup"><span data-stu-id="588d3-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="588d3-109">Przebiegi testów, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="588d3-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="588d3-110">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="588d3-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="588d3-111">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="588d3-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="588d3-112">Uruchamia testy, które są w klasie `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="588d3-112">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="588d3-113">**Uwaga:** `ClassName` wartości powinny mieć obszaru nazw, więc `ClassName=UnitTest1` nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="588d3-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="588d3-114">Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="588d3-114">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="588d3-115">Uruchamia testy, które są przypisane przy użyciu `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="588d3-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="588d3-116">Uruchamia testy, które są przypisane przy użyciu `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="588d3-116">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="588d3-117">**Za pomocą operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="588d3-117">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="588d3-118">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="588d3-118">Expression</span></span> | <span data-ttu-id="588d3-119">Wynik</span><span class="sxs-lookup"><span data-stu-id="588d3-119">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="588d3-120">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="588d3-120">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="588d3-121">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="588d3-121">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="588d3-122">Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="588d3-122">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="588d3-123">xUnit</span><span class="sxs-lookup"><span data-stu-id="588d3-123">xUnit</span></span>

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

| <span data-ttu-id="588d3-124">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="588d3-124">Expression</span></span> | <span data-ttu-id="588d3-125">Wynik</span><span class="sxs-lookup"><span data-stu-id="588d3-125">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="588d3-126">Uruchamia tylko jeden test `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="588d3-126">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="588d3-127">Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="588d3-127">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="588d3-128">Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="588d3-128">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="588d3-129">W przykładzie kodu zdefiniowanych cech przy użyciu kluczy `Category` i `Priority` może służyć do filtrowania.</span><span class="sxs-lookup"><span data-stu-id="588d3-129">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="588d3-130">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="588d3-130">Expression</span></span> | <span data-ttu-id="588d3-131">Wynik</span><span class="sxs-lookup"><span data-stu-id="588d3-131">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="588d3-132">Przebiegi testów, których `FullyQualifiedName` zawiera `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="588d3-132">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="588d3-133">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="588d3-133">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="588d3-134">Uruchamia testy, które mają `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="588d3-134">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="588d3-135">**Za pomocą operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="588d3-135">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="588d3-136">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="588d3-136">Expression</span></span> | <span data-ttu-id="588d3-137">Wynik</span><span class="sxs-lookup"><span data-stu-id="588d3-137">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="588d3-138">Przebiegów testów, które ma `TestClass1` w `FullyQualifiedName` **lub** `Category` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="588d3-138">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="588d3-139">Przebiegów testów, które ma `TestClass1` w `FullyQualifiedName` **i** `Category` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="588d3-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="588d3-140">Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `TestClass1` **i** `Category` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="588d3-140">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="588d3-141">Rozszerzenie NUnit</span><span class="sxs-lookup"><span data-stu-id="588d3-141">NUnit</span></span>

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

| <span data-ttu-id="588d3-142">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="588d3-142">Expression</span></span> | <span data-ttu-id="588d3-143">Wynik</span><span class="sxs-lookup"><span data-stu-id="588d3-143">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="588d3-144">Przebiegi testów, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="588d3-144">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="588d3-145">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="588d3-145">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="588d3-146">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="588d3-146">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="588d3-147">Uruchamia testy, które są w klasie `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="588d3-147">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="588d3-148">Uruchamia wszystkie testy z wyjątkiem `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="588d3-148">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="588d3-149">Uruchamia testy, które są przypisane przy użyciu `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="588d3-149">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="588d3-150">Uruchamia testy, które są przypisane przy użyciu `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="588d3-150">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="588d3-151">**Za pomocą operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="588d3-151">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="588d3-152">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="588d3-152">Expression</span></span> | <span data-ttu-id="588d3-153">Wynik</span><span class="sxs-lookup"><span data-stu-id="588d3-153">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="588d3-154">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="588d3-154">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="588d3-155">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="588d3-155">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="588d3-156">Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="588d3-156">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
