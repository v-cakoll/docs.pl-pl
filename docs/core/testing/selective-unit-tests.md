---
title: Uruchamianie selektywnych testów jednostkowych
description: Jak używać wyrażenia filtru uruchamianie selektywnych testów jednostkowych za pomocą polecenia dotnet testu w programie .NET Core.
author: smadala
ms.date: 03/22/2017
ms.custom: seodec18
ms.openlocfilehash: 2ec6dc770f33acc4acea79e60cf6f9c33f1077d8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239946"
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="f7452-103">Uruchamianie selektywnych testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="f7452-103">Running selective unit tests</span></span>

<span data-ttu-id="f7452-104">Za pomocą `dotnet test` polecenia platformie .NET Core, można użyć wyrażenia filtru do uruchamiania testów selektywnego.</span><span class="sxs-lookup"><span data-stu-id="f7452-104">With the `dotnet test` command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="f7452-105">W tym artykule przedstawiono sposób filtrowania, które testu.</span><span class="sxs-lookup"><span data-stu-id="f7452-105">This article demonstrates how to filter which test are run.</span></span> <span data-ttu-id="f7452-106">W poniższych przykładach używane `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="f7452-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="f7452-107">Jeśli używasz `vstest.console.exe`, Zastąp `--filter ` z `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="f7452-107">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="f7452-108">MSTest</span><span class="sxs-lookup"><span data-stu-id="f7452-108">MSTest</span></span>

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

| <span data-ttu-id="f7452-109">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="f7452-109">Expression</span></span> | <span data-ttu-id="f7452-110">Wynik</span><span class="sxs-lookup"><span data-stu-id="f7452-110">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="f7452-111">Przebiegi testów, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="f7452-111">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="f7452-112">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="f7452-112">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="f7452-113">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="f7452-113">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="f7452-114">Uruchamia testy, które są w klasie `MSTestNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="f7452-114">Runs tests which are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="f7452-115">**Uwaga:** `ClassName` Wartości powinny mieć obszaru nazw, więc `ClassName=UnitTest1` nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="f7452-115">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="f7452-116">Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="f7452-116">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="f7452-117">Uruchamia testy, które są przypisane przy użyciu `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="f7452-117">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="f7452-118">Uruchamia testy, które są przypisane przy użyciu `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="f7452-118">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="f7452-119">**Za pomocą operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="f7452-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="f7452-120">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="f7452-120">Expression</span></span> | <span data-ttu-id="f7452-121">Wynik</span><span class="sxs-lookup"><span data-stu-id="f7452-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="f7452-122">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f7452-122">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="f7452-123">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f7452-123">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="f7452-124">Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="f7452-124">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="f7452-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="f7452-125">xUnit</span></span>

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

| <span data-ttu-id="f7452-126">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="f7452-126">Expression</span></span> | <span data-ttu-id="f7452-127">Wynik</span><span class="sxs-lookup"><span data-stu-id="f7452-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="f7452-128">Uruchamia tylko jeden test `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="f7452-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="f7452-129">Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="f7452-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="f7452-130">Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="f7452-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="f7452-131">W przykładzie kodu zdefiniowanych cech przy użyciu kluczy `Category` i `Priority` może służyć do filtrowania.</span><span class="sxs-lookup"><span data-stu-id="f7452-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="f7452-132">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="f7452-132">Expression</span></span> | <span data-ttu-id="f7452-133">Wynik</span><span class="sxs-lookup"><span data-stu-id="f7452-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="f7452-134">Przebiegi testów, których `FullyQualifiedName` zawiera `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="f7452-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="f7452-135">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="f7452-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="f7452-136">Uruchamia testy, które mają `[Trait("Category", "CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="f7452-136">Runs tests which have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="f7452-137">**Za pomocą operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="f7452-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="f7452-138">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="f7452-138">Expression</span></span> | <span data-ttu-id="f7452-139">Wynik</span><span class="sxs-lookup"><span data-stu-id="f7452-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | <span data-ttu-id="f7452-140">Przebiegów testów, które ma `TestClass1` w `FullyQualifiedName` **lub** `Category` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f7452-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | <span data-ttu-id="f7452-141">Przebiegów testów, które ma `TestClass1` w `FullyQualifiedName` **i** `Category` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f7452-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="f7452-142">Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `TestClass1` **i** `Category` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="f7452-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="nunit"></a><span data-ttu-id="f7452-143">Rozszerzenie NUnit</span><span class="sxs-lookup"><span data-stu-id="f7452-143">NUnit</span></span>

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

| <span data-ttu-id="f7452-144">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="f7452-144">Expression</span></span> | <span data-ttu-id="f7452-145">Wynik</span><span class="sxs-lookup"><span data-stu-id="f7452-145">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="f7452-146">Przebiegi testów, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="f7452-146">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="f7452-147">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="f7452-147">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="f7452-148">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="f7452-148">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="f7452-149">Uruchamia testy, które są w klasie `NUnitNamespace.UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="f7452-149">Runs tests which are in class `NUnitNamespace.UnitTest1`.</span></span><br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="f7452-150">Uruchamia wszystkie testy z wyjątkiem `NUnitNamespace.UnitTest1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="f7452-150">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="f7452-151">Uruchamia testy, które są przypisane przy użyciu `[Category("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="f7452-151">Runs tests which are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="f7452-152">Uruchamia testy, które są przypisane przy użyciu `[Priority(2)]`.</span><span class="sxs-lookup"><span data-stu-id="f7452-152">Runs tests which are annotated with `[Priority(2)]`.</span></span><br>

<span data-ttu-id="f7452-153">**Za pomocą operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="f7452-153">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="f7452-154">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="f7452-154">Expression</span></span> | <span data-ttu-id="f7452-155">Wynik</span><span class="sxs-lookup"><span data-stu-id="f7452-155">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="f7452-156">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f7452-156">Runs tests which have `UnitTest1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | <span data-ttu-id="f7452-157">Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f7452-157">Runs tests which have `UnitTest1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="f7452-158">Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="f7452-158">Runs tests which have either `FullyQualifiedName` containing `UnitTest1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |
