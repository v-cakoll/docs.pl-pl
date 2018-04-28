---
title: Testy jednostkowe Uruchamianie selektywne
description: Pokazuje, jak używać do uruchamiania testów jednostkowych selektywnego przy użyciu polecenia testowego dotnet wyrażenie filtru.
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 77ac7ab5a46150bd3654d50e6686087c804b8440
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="f170c-103">Testy jednostkowe Uruchamianie selektywne</span><span class="sxs-lookup"><span data-stu-id="f170c-103">Running selective unit tests</span></span>

<span data-ttu-id="f170c-104">W poniższych przykładach użyto `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="f170c-104">The following examples use `dotnet test`.</span></span> <span data-ttu-id="f170c-105">Jeśli używasz `vstest.console.exe`, Zastąp `--filter ` z `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="f170c-105">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="f170c-106">MSTest</span><span class="sxs-lookup"><span data-stu-id="f170c-106">MSTest</span></span>

```csharp
namespace MSTestNamespace
{
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    [TestClass]
    public class UnitTestClass1
    {
        [Priority(2)]
        [TestMethod]
        public void TestMethod1()
        {
        }

        [TestCategory("CategoryA")]
        [Priority(3)]
        [TestMethod]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="f170c-107">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="f170c-107">Expression</span></span> | <span data-ttu-id="f170c-108">Wynik</span><span class="sxs-lookup"><span data-stu-id="f170c-108">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="f170c-109">Uruchamia testy, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="f170c-109">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="f170c-110">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="f170c-110">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="f170c-111">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="f170c-111">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="f170c-112">Uruchamia testy, które należą do klasy `MSTestNamespace.UnitTestClass1`.</span><span class="sxs-lookup"><span data-stu-id="f170c-112">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="f170c-113">**Uwaga:** `ClassName` wartość powinien mieć obszar nazw, dlatego `ClassName=UnitTestClass1` nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="f170c-113">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="f170c-114">Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTestClass1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="f170c-114">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="f170c-115">Uruchamia testy, które są przypisane z `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="f170c-115">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="f170c-116">Uruchamia testy, które są przypisane z `[Priority(3)]`.</span><span class="sxs-lookup"><span data-stu-id="f170c-116">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="f170c-117">**Uwaga:** `Priority~3` wartość jest nieprawidłowa, ponieważ nie jest ciąg.</span><span class="sxs-lookup"><span data-stu-id="f170c-117">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="f170c-118">**Przy użyciu operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="f170c-118">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="f170c-119">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="f170c-119">Expression</span></span> | <span data-ttu-id="f170c-120">Wynik</span><span class="sxs-lookup"><span data-stu-id="f170c-120">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="f170c-121">Uruchamia testy, które mają `UnitTestClass1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f170c-121">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="f170c-122">Uruchamia testy, które mają `UnitTestClass1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="f170c-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="f170c-123">Uruchamia testy, które `FullyQualifiedName` zawierający `UnitTestClass1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="f170c-123">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="f170c-124">xUnit</span><span class="sxs-lookup"><span data-stu-id="f170c-124">xUnit</span></span>

```csharp
namespace XUnitNamespace
{
    public class TestClass1
    {
        [Trait("Category", "bvt")]
        [Trait("Priority", "1")]
        [Fact]
        public void foo()
        {
        }

        [Trait("Category", "Nightly")]
        [Trait("Priority", "2")]
        [Fact]
        public void bar()
        {
        }
    }
}
```

| <span data-ttu-id="f170c-125">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="f170c-125">Expression</span></span> | <span data-ttu-id="f170c-126">Wynik</span><span class="sxs-lookup"><span data-stu-id="f170c-126">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="f170c-127">Uruchamia test tylko jeden `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="f170c-127">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="f170c-128">Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="f170c-128">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="f170c-129">Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="f170c-129">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="f170c-130">W przykładzie kodu zdefiniowanych cech z kluczami `Category` i `Priority` może służyć do filtrowania.</span><span class="sxs-lookup"><span data-stu-id="f170c-130">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="f170c-131">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="f170c-131">Expression</span></span> | <span data-ttu-id="f170c-132">Wynik</span><span class="sxs-lookup"><span data-stu-id="f170c-132">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="f170c-133">Uruchamia testy, których `FullyQualifiedName` zawiera `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="f170c-133">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="f170c-134">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="f170c-134">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="f170c-135">Uruchamia testy, które mają `[Trait("Category", "bvt")]`.</span><span class="sxs-lookup"><span data-stu-id="f170c-135">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="f170c-136">**Przy użyciu operatorów warunkowych | i &amp;**</span><span class="sxs-lookup"><span data-stu-id="f170c-136">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="f170c-137">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="f170c-137">Expression</span></span> | <span data-ttu-id="f170c-138">Wynik</span><span class="sxs-lookup"><span data-stu-id="f170c-138">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="f170c-139">Uruchamia testy, które ma `TestClass1` w `FullyQualifiedName` **lub** `Category` jest `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="f170c-139">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="f170c-140">Uruchamia testy, które ma `TestClass1` w `FullyQualifiedName` **i** `Category` jest `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="f170c-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="f170c-141">Uruchamia testy, które `FullyQualifiedName` zawierający `TestClass1` **i** `Category` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="f170c-141">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |
