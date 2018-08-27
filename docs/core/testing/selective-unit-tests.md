---
title: Uruchamianie selektywnych testów jednostkowych
description: Dowiesz się, jak uruchamianie selektywnych testów jednostkowych za pomocą polecenia dotnet test za pomocą wyrażenia filtru.
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.openlocfilehash: 428e31014f5d8d487deb7c4b4317ebcef13c294d
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935183"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="4450f-103">Uruchamianie selektywnych testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="4450f-103">Running selective unit tests</span></span>

<span data-ttu-id="4450f-104">W poniższych przykładach używane `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="4450f-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="4450f-105">Jeśli używasz `vstest.console.exe`, Zastąp `--filter ` z `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="4450f-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="4450f-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="4450f-106">MSTest</span></span>

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

| <span data-ttu-id="4450f-107">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="4450f-107">Expression</span></span> | <span data-ttu-id="4450f-108">Wynik</span><span class="sxs-lookup"><span data-stu-id="4450f-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="4450f-109">Przebiegi testów, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="4450f-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="4450f-110">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="4450f-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="4450f-111">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="4450f-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="4450f-112">Uruchamia testy, które są w klasie `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="4450f-112">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="4450f-113">**Uwaga:** `ClassName` wartości powinny mieć obszaru nazw, więc `ClassName=UnitTest1` nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="4450f-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="4450f-114">Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="4450f-114">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="4450f-115">Uruchamia testy, które są przypisane przy użyciu `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="4450f-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="4450f-116">Uruchamia testy, które są przypisane przy użyciu `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="4450f-116">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="4450f-117">**Za pomocą operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="4450f-117">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="4450f-118">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="4450f-118">Expression</span></span> | <span data-ttu-id="4450f-119">Wynik</span><span class="sxs-lookup"><span data-stu-id="4450f-119">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="4450f-120">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="4450f-120">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="4450f-121">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="4450f-121">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="4450f-122">Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="4450f-122">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="4450f-123">xUnit</span><span class="sxs-lookup"><span data-stu-id="4450f-123">xUnit</span></span>

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

| <span data-ttu-id="4450f-124">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="4450f-124">Expression</span></span> | <span data-ttu-id="4450f-125">Wynik</span><span class="sxs-lookup"><span data-stu-id="4450f-125">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="4450f-126">Uruchamia tylko jeden test `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="4450f-126">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="4450f-127">Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="4450f-127">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="4450f-128">Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="4450f-128">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="4450f-129">W przykładzie kodu zdefiniowanych cech przy użyciu kluczy `Category` i `Priority` może służyć do filtrowania.</span><span class="sxs-lookup"><span data-stu-id="4450f-129">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="4450f-130">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="4450f-130">Expression</span></span> | <span data-ttu-id="4450f-131">Wynik</span><span class="sxs-lookup"><span data-stu-id="4450f-131">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="4450f-132">Przebiegi testów, których `FullyQualifiedName` zawiera `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="4450f-132">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="4450f-133">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="4450f-133">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="4450f-134">Uruchamia testy, które mają `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="4450f-134">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="4450f-135">**Za pomocą operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="4450f-135">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="4450f-136">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="4450f-136">Expression</span></span> | <span data-ttu-id="4450f-137">Wynik</span><span class="sxs-lookup"><span data-stu-id="4450f-137">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="4450f-138">Przebiegów testów, które ma `TestClass1` w `FullyQualifiedName` **lub** `Category` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="4450f-138">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="4450f-139">Przebiegów testów, które ma `TestClass1` w `FullyQualifiedName` **i** `Category` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="4450f-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="4450f-140">Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `TestClass1` **i** `Category` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="4450f-140">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="4450f-141">Rozszerzenie NUnit</span><span class="sxs-lookup"><span data-stu-id="4450f-141">NUnit</span></span>

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

| <span data-ttu-id="4450f-142">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="4450f-142">Expression</span></span> | <span data-ttu-id="4450f-143">Wynik</span><span class="sxs-lookup"><span data-stu-id="4450f-143">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="4450f-144">Przebiegi testów, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="4450f-144">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="4450f-145">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="4450f-145">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="4450f-146">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="4450f-146">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="4450f-147">Uruchamia testy, które są w klasie `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="4450f-147">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="4450f-148">Uruchamia wszystkie testy z wyjątkiem `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="4450f-148">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="4450f-149">Uruchamia testy, które są przypisane przy użyciu `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="4450f-149">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="4450f-150">Uruchamia testy, które są przypisane przy użyciu `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="4450f-150">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="4450f-151">**Za pomocą operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="4450f-151">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="4450f-152">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="4450f-152">Expression</span></span> | <span data-ttu-id="4450f-153">Wynik</span><span class="sxs-lookup"><span data-stu-id="4450f-153">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="4450f-154">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="4450f-154">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="4450f-155">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="4450f-155">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="4450f-156">Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="4450f-156">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
