---
title: Testy jednostkowe Uruchamianie selektywne
description: "Pokazuje, jak używać do uruchamiania testów jednostkowych selektywnego przy użyciu polecenia testowego dotnet wyrażenie filtru."
keywords: Test jednostkowy .NET i .NET core, selektywnego testu
author: smadala
ms.author: mairaw
ms.date: 03/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13d01272-bbf8-456c-a97a-560001d1a7f2
ms.workload: dotnetcore
ms.openlocfilehash: a650e971afd63171b0cc12f679d81bc222a609a5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="running-selective-unit-tests"></a><span data-ttu-id="876a5-104">Testy jednostkowe Uruchamianie selektywne</span><span class="sxs-lookup"><span data-stu-id="876a5-104">Running selective unit tests</span></span>

<span data-ttu-id="876a5-105">W poniższych przykładach użyto `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="876a5-105">The following examples use `dotnet test`.</span></span> <span data-ttu-id="876a5-106">Jeśli używasz `vstest.console.exe`, Zastąp `--filter ` z `--testcasefilter:`.</span><span class="sxs-lookup"><span data-stu-id="876a5-106">If you're using `vstest.console.exe`, replace `--filter ` with `--testcasefilter:`.</span></span>

## <a name="mstest"></a><span data-ttu-id="876a5-107">MSTest</span><span class="sxs-lookup"><span data-stu-id="876a5-107">MSTest</span></span>

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

| <span data-ttu-id="876a5-108">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="876a5-108">Expression</span></span> | <span data-ttu-id="876a5-109">Wynik</span><span class="sxs-lookup"><span data-stu-id="876a5-109">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter Method` | <span data-ttu-id="876a5-110">Uruchamia testy, których `FullyQualifiedName` zawiera `Method`.</span><span class="sxs-lookup"><span data-stu-id="876a5-110">Runs tests whose `FullyQualifiedName` contains `Method`.</span></span> <span data-ttu-id="876a5-111">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="876a5-111">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="876a5-112">Uruchamia testy, których nazwa zawiera `TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="876a5-112">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | <span data-ttu-id="876a5-113">Uruchamia testy, które należą do klasy `MSTestNamespace.UnitTestClass1`.</span><span class="sxs-lookup"><span data-stu-id="876a5-113">Runs tests which are in class `MSTestNamespace.UnitTestClass1`.</span></span><br><span data-ttu-id="876a5-114">**Uwaga:** `ClassName` wartość powinien mieć obszar nazw, dlatego `ClassName=UnitTestClass1` nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="876a5-114">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTestClass1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | <span data-ttu-id="876a5-115">Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTestClass1.TestMethod1`.</span><span class="sxs-lookup"><span data-stu-id="876a5-115">Runs all tests except `MSTestNamespace.UnitTestClass1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="876a5-116">Uruchamia testy, które są przypisane z `[TestCategory("CategoryA")]`.</span><span class="sxs-lookup"><span data-stu-id="876a5-116">Runs tests which are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=3` | <span data-ttu-id="876a5-117">Uruchamia testy, które są przypisane z `[Priority(3)]`.</span><span class="sxs-lookup"><span data-stu-id="876a5-117">Runs tests which are annotated with `[Priority(3)]`.</span></span><br><span data-ttu-id="876a5-118">**Uwaga:** `Priority~3` wartość jest nieprawidłowa, ponieważ nie jest ciąg.</span><span class="sxs-lookup"><span data-stu-id="876a5-118">**Note:** `Priority~3` is an invalid value, as it isn't a string.</span></span> |

<span data-ttu-id="876a5-119">**Przy użyciu operatorów warunkowych | i&amp;**</span><span class="sxs-lookup"><span data-stu-id="876a5-119">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="876a5-120">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="876a5-120">Expression</span></span> | <span data-ttu-id="876a5-121">Wynik</span><span class="sxs-lookup"><span data-stu-id="876a5-121">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | <span data-ttu-id="876a5-122">Uruchamia testy, które mają `UnitTestClass1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="876a5-122">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **or** `TestCategory` is `CategoryA`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | <span data-ttu-id="876a5-123">Uruchamia testy, które mają `UnitTestClass1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`.</span><span class="sxs-lookup"><span data-stu-id="876a5-123">Runs tests which have `UnitTestClass1` in `FullyQualifiedName` **and** `TestCategory` is `CategoryA`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | <span data-ttu-id="876a5-124">Uruchamia testy, które `FullyQualifiedName` zawierający `UnitTestClass1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="876a5-124">Runs tests which have either `FullyQualifiedName` containing `UnitTestClass1` **and** `TestCategory` is `CategoryA` **or** `Priority` is 1.</span></span> |

## <a name="xunit"></a><span data-ttu-id="876a5-125">xUnit</span><span class="sxs-lookup"><span data-stu-id="876a5-125">xUnit</span></span>

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

| <span data-ttu-id="876a5-126">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="876a5-126">Expression</span></span> | <span data-ttu-id="876a5-127">Wynik</span><span class="sxs-lookup"><span data-stu-id="876a5-127">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="876a5-128">Uruchamia test tylko jeden `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="876a5-128">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="876a5-129">Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1`.</span><span class="sxs-lookup"><span data-stu-id="876a5-129">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="876a5-130">Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1`.</span><span class="sxs-lookup"><span data-stu-id="876a5-130">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="876a5-131">W przykładzie kodu zdefiniowanych cech z kluczami `Category` i `Priority` może służyć do filtrowania.</span><span class="sxs-lookup"><span data-stu-id="876a5-131">In the code example, the defined traits with keys `Category` and `Priority` can be used for filtering.</span></span>

| <span data-ttu-id="876a5-132">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="876a5-132">Expression</span></span> | <span data-ttu-id="876a5-133">Wynik</span><span class="sxs-lookup"><span data-stu-id="876a5-133">Result</span></span> |
| ---------- | ------ |
| `dotnet test --filter XUnit` | <span data-ttu-id="876a5-134">Uruchamia testy, których `FullyQualifiedName` zawiera `XUnit`.</span><span class="sxs-lookup"><span data-stu-id="876a5-134">Runs tests whose `FullyQualifiedName` contains `XUnit`.</span></span>  <span data-ttu-id="876a5-135">Dostępne w `vstest 15.1+`.</span><span class="sxs-lookup"><span data-stu-id="876a5-135">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=bvt` | <span data-ttu-id="876a5-136">Uruchamia testy, które mają `[Trait("Category", "bvt")]`.</span><span class="sxs-lookup"><span data-stu-id="876a5-136">Runs tests which have `[Trait("Category", "bvt")]`.</span></span> |

<span data-ttu-id="876a5-137">**Przy użyciu operatorów warunkowych | i&amp;**</span><span class="sxs-lookup"><span data-stu-id="876a5-137">**Using conditional operators | and &amp;**</span></span>

| <span data-ttu-id="876a5-138">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="876a5-138">Expression</span></span> | <span data-ttu-id="876a5-139">Wynik</span><span class="sxs-lookup"><span data-stu-id="876a5-139">Result</span></span> |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | <span data-ttu-id="876a5-140">Uruchamia testy, które ma `TestClass1` w `FullyQualifiedName` **lub** `Category` jest `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="876a5-140">Runs tests which has `TestClass1` in `FullyQualifiedName` **or** `Category` is `Nightly`.</span></span> |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | <span data-ttu-id="876a5-141">Uruchamia testy, które ma `TestClass1` w `FullyQualifiedName` **i** `Category` jest `Nightly`.</span><span class="sxs-lookup"><span data-stu-id="876a5-141">Runs tests which has `TestClass1` in `FullyQualifiedName` **and** `Category` is `Nightly`.</span></span> |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | <span data-ttu-id="876a5-142">Uruchamia testy, które `FullyQualifiedName` zawierający `TestClass1` **i** `Category` jest `CategoryA` **lub** `Priority` 1.</span><span class="sxs-lookup"><span data-stu-id="876a5-142">Runs tests which have either `FullyQualifiedName` containing `TestClass1` **and** `Category` is `CategoryA` **or** `Priority` is 1.</span></span> |
