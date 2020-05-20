---
title: Uruchamianie selektywnych testów jednostkowych
description: Jak używać wyrażenia filtru do uruchamiania selektywnych testów jednostkowych za pomocą polecenia Test dotnet w programie .NET Core.
author: smadala
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: 6a6bbb0687742d1e3288d64fb88f6825dc678e28
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702983"
---
# <a name="run-selective-unit-tests"></a><span data-ttu-id="23974-103">Uruchamianie selektywnych testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="23974-103">Run selective unit tests</span></span>

<span data-ttu-id="23974-104">Za pomocą [`dotnet test`](../tools/dotnet-test.md) polecenia w programie .NET Core można używać wyrażenia filtru do uruchamiania selektywnych testów.</span><span class="sxs-lookup"><span data-stu-id="23974-104">With the [`dotnet test`](../tools/dotnet-test.md) command in .NET Core, you can use a filter expression to run selective tests.</span></span> <span data-ttu-id="23974-105">W tym artykule przedstawiono sposób filtrowania, które testy są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="23974-105">This article demonstrates how to filter which tests are run.</span></span> <span data-ttu-id="23974-106">W poniższych przykładach użyto `dotnet test` .</span><span class="sxs-lookup"><span data-stu-id="23974-106">The following examples use `dotnet test`.</span></span> <span data-ttu-id="23974-107">Jeśli używasz programu `vstest.console.exe` , Zamień `--filter` na `--testcasefilter:` .</span><span class="sxs-lookup"><span data-stu-id="23974-107">If you're using `vstest.console.exe`, replace `--filter` with `--testcasefilter:`.</span></span>

## <a name="character-escaping"></a><span data-ttu-id="23974-108">Znak ucieczki</span><span class="sxs-lookup"><span data-stu-id="23974-108">Character escaping</span></span>

<span data-ttu-id="23974-109">Użycie filtrów, które zawierają znak wykrzyknika, `!` `*nix` wymaga ucieczki, ponieważ `!` jest zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="23974-109">Using filters that include exclamation mark `!` on `*nix` requires escaping since `!` is reserved.</span></span> <span data-ttu-id="23974-110">Na przykład ten filtr pomija wszystkie testy, jeśli przestrzeń nazw zawiera IntegrationTests:</span><span class="sxs-lookup"><span data-stu-id="23974-110">For example, this filter skips all tests if the namespace contains IntegrationTests:</span></span>

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> <span data-ttu-id="23974-111">Ukośnik odwrotny poprzedza znak wykrzyknika, aby wskazać, że jest znakiem ucieczki `\!` .</span><span class="sxs-lookup"><span data-stu-id="23974-111">The backslash precedes the exclamation mark to indicate it is an escaped character `\!`.</span></span>

<span data-ttu-id="23974-112">Dla `FullyQualifiedName` wartości, które zawierają przecinek dla parametrów typu generycznego, wpisz przecinek `%2C` .</span><span class="sxs-lookup"><span data-stu-id="23974-112">For `FullyQualifiedName` values that include a comma for generic type parameters, escape the comma with `%2C`.</span></span> <span data-ttu-id="23974-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="23974-113">For example:</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

:::zone pivot="mstest"

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace MSTestNamespace
{
    [TestClass]
    public class UnitTest1
    {
        [TestMethod, Priority(1), TestCategory("CategoryA")]
        public void TestMethod1()
        {
        }

        [TestMethod, Priority(2)]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="23974-114">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="23974-114">Expression</span></span> | <span data-ttu-id="23974-115">Wynik</span><span class="sxs-lookup"><span data-stu-id="23974-115">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="23974-116">Uruchamia testy, których <xref:System.Reflection.Module.FullyQualifiedName> zawiera `Method` .</span><span class="sxs-lookup"><span data-stu-id="23974-116">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="23974-117">Dostępne w `vstest 15.1+` .</span><span class="sxs-lookup"><span data-stu-id="23974-117">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="23974-118">Uruchamia testy, których nazwa zawiera `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="23974-118">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | <span data-ttu-id="23974-119">Uruchamia testy, które znajdują się w klasie `MSTestNamespace.UnitTest1` .</span><span class="sxs-lookup"><span data-stu-id="23974-119">Runs tests that are in class `MSTestNamespace.UnitTest1`.</span></span><br><span data-ttu-id="23974-120">**Uwaga:** `ClassName`Wartość powinna mieć przestrzeń nazw, dlatego `ClassName=UnitTest1` nie będzie działała.</span><span class="sxs-lookup"><span data-stu-id="23974-120">**Note:** The `ClassName` value should have a namespace, so `ClassName=UnitTest1` won't work.</span></span> |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="23974-121">Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTest1.TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="23974-121">Runs all tests except `MSTestNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="23974-122">Uruchamia testy, które są opatrzone adnotacją `[TestCategory("CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="23974-122">Runs tests that are annotated with `[TestCategory("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="23974-123">Uruchamia testy, które są opatrzone adnotacją `[Priority(2)]` .</span><span class="sxs-lookup"><span data-stu-id="23974-123">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="23974-124">Przykłady wykorzystujące operatory warunkowe `|` i `&` :</span><span class="sxs-lookup"><span data-stu-id="23974-124">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="23974-125">Do uruchamiania testów, które mają `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **lub** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> są `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="23974-125">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> is `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="23974-126">Do uruchamiania testów, które znajdują się `UnitTest1` w ich <xref:System.Reflection.Module.FullyQualifiedName> **i** mają <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="23974-126">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="23974-127">Do uruchamiania testów, które mają <xref:System.Reflection.Module.FullyQualifiedName> `UnitTest1` **co** najmniej jeden z <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` **lub** mają <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> priorytet `1` .</span><span class="sxs-lookup"><span data-stu-id="23974-127">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> of `"CategoryA"` **or** have a <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> with a priority of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="xunit"

```csharp
using Xunit;

namespace XUnitNamespace
{
    public class TestClass1
    {
        [Fact, Trait("Priority", "1"), Trait("Category", "CategoryA")]
        public void Test1()
        {
        }

        [Fact, Trait("Priority", "2")]
        public void Test2()
        {
        }
    }
}
```

| <span data-ttu-id="23974-128">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="23974-128">Expression</span></span> | <span data-ttu-id="23974-129">Wynik</span><span class="sxs-lookup"><span data-stu-id="23974-129">Result</span></span> |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="23974-130">Uruchamia tylko jeden test, `XUnitNamespace.TestClass1.Test1` .</span><span class="sxs-lookup"><span data-stu-id="23974-130">Runs only one test, `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | <span data-ttu-id="23974-131">Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1` .</span><span class="sxs-lookup"><span data-stu-id="23974-131">Runs all tests except `XUnitNamespace.TestClass1.Test1`.</span></span> |
| `dotnet test --filter DisplayName~TestClass1` | <span data-ttu-id="23974-132">Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1` .</span><span class="sxs-lookup"><span data-stu-id="23974-132">Runs tests whose display name contains `TestClass1`.</span></span> |

<span data-ttu-id="23974-133">W przykładzie kodu, zdefiniowane cechy z kluczami `"Category"` i `"Priority"` mogą być używane do filtrowania.</span><span class="sxs-lookup"><span data-stu-id="23974-133">In the code example, the defined traits with keys `"Category"` and `"Priority"` can be used for filtering.</span></span>

| <span data-ttu-id="23974-134">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="23974-134">Expression</span></span> | <span data-ttu-id="23974-135">Wynik</span><span class="sxs-lookup"><span data-stu-id="23974-135">Result</span></span> |
|--|--|
| `dotnet test --filter XUnit` | <span data-ttu-id="23974-136">Uruchamia testy, których <xref:System.Reflection.Module.FullyQualifiedName> zawiera `XUnit` .</span><span class="sxs-lookup"><span data-stu-id="23974-136">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `XUnit`.</span></span>  <span data-ttu-id="23974-137">Dostępne w `vstest 15.1+` .</span><span class="sxs-lookup"><span data-stu-id="23974-137">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Category=CategoryA` | <span data-ttu-id="23974-138">Uruchamia testy, które mają `[Trait("Category", "CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="23974-138">Runs tests that have `[Trait("Category", "CategoryA")]`.</span></span> |

<span data-ttu-id="23974-139">Przykłady wykorzystujące operatory warunkowe `|` i `&` :</span><span class="sxs-lookup"><span data-stu-id="23974-139">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="23974-140">Do uruchamiania testów, które mają `TestClass1` <xref:System.Reflection.Module.FullyQualifiedName> **lub** mają `Trait` klucz `"Category"` i wartość `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="23974-140">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

<span data-ttu-id="23974-141">Do uruchamiania testów, które mają `TestClass1` <xref:System.Reflection.Module.FullyQualifiedName> **i** mają klucz o `Trait` `"Category"` i wartości `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="23974-141">To run tests that have `TestClass1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

<span data-ttu-id="23974-142">Do uruchamiania testów, które zawierają <xref:System.Reflection.Module.FullyQualifiedName> `TestClass1` **i** mają klucz z `Trait` `"Category"` i wartością `"CategoryA"` **lub** mają klucz z i `Trait` `"Priority"` wartość `1` .</span><span class="sxs-lookup"><span data-stu-id="23974-142">To run tests that have either <xref:System.Reflection.Module.FullyQualifiedName> containing `TestClass1` **and** have a `Trait` with a key of `"Category"` and value of `"CategoryA"` **or** have a `Trait` with a key of `"Priority"` and value of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)|Priority=1"
```

:::zone-end
:::zone pivot="nunit"

```csharp
using NUnit.Framework;

namespace NUnitNamespace
{
    public class UnitTest1
    {
        [Test, Property("Priority", 1), Category("CategoryA")]
        public void TestMethod1()
        {
        }

        [Test, Property("Priority", 2)]
        public void TestMethod2()
        {
        }
    }
}
```

| <span data-ttu-id="23974-143">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="23974-143">Expression</span></span> | <span data-ttu-id="23974-144">Wynik</span><span class="sxs-lookup"><span data-stu-id="23974-144">Result</span></span> |
|--|--|
| `dotnet test --filter Method` | <span data-ttu-id="23974-145">Uruchamia testy, których <xref:System.Reflection.Module.FullyQualifiedName> zawiera `Method` .</span><span class="sxs-lookup"><span data-stu-id="23974-145">Runs tests whose <xref:System.Reflection.Module.FullyQualifiedName> contains `Method`.</span></span> <span data-ttu-id="23974-146">Dostępne w `vstest 15.1+` .</span><span class="sxs-lookup"><span data-stu-id="23974-146">Available in `vstest 15.1+`.</span></span> |
| `dotnet test --filter Name~TestMethod1` | <span data-ttu-id="23974-147">Uruchamia testy, których nazwa zawiera `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="23974-147">Runs tests whose name contains `TestMethod1`.</span></span> |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | <span data-ttu-id="23974-148">Uruchamia testy, które znajdują się w klasie `NUnitNamespace.UnitTest1` .</span><span class="sxs-lookup"><span data-stu-id="23974-148">Runs tests that are in class `NUnitNamespace.UnitTest1`.</span></span> |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | <span data-ttu-id="23974-149">Uruchamia wszystkie testy z wyjątkiem `NUnitNamespace.UnitTest1.TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="23974-149">Runs all tests except `NUnitNamespace.UnitTest1.TestMethod1`.</span></span> |
| `dotnet test --filter TestCategory=CategoryA` | <span data-ttu-id="23974-150">Uruchamia testy, które są opatrzone adnotacją `[Category("CategoryA")]` .</span><span class="sxs-lookup"><span data-stu-id="23974-150">Runs tests that are annotated with `[Category("CategoryA")]`.</span></span> |
| `dotnet test --filter Priority=2` | <span data-ttu-id="23974-151">Uruchamia testy, które są opatrzone adnotacją `[Priority(2)]` .</span><span class="sxs-lookup"><span data-stu-id="23974-151">Runs tests that are annotated with `[Priority(2)]`.</span></span> |

<span data-ttu-id="23974-152">Przykłady wykorzystujące operatory warunkowe `|` i `&` :</span><span class="sxs-lookup"><span data-stu-id="23974-152">Examples using the conditional operators `|` and `&`:</span></span>

<span data-ttu-id="23974-153">Do uruchamiania testów, które mają `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **lub** mają `Category` `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="23974-153">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **or** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

<span data-ttu-id="23974-154">Do uruchamiania testów, które znajdują się `UnitTest1` w ich <xref:System.Reflection.Module.FullyQualifiedName> **i** mają `Category` `"CategoryA"` .</span><span class="sxs-lookup"><span data-stu-id="23974-154">To run tests that have `UnitTest1` in their <xref:System.Reflection.Module.FullyQualifiedName> **and** have a `Category` of `"CategoryA"`.</span></span>

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

<span data-ttu-id="23974-155">Do uruchamiania testów, które mają element <xref:System.Reflection.Module.FullyQualifiedName> zawierający `UnitTest1` **i** ma `Category` `"CategoryA"` **lub** mieć z `Property` `"Priority"` `1` .</span><span class="sxs-lookup"><span data-stu-id="23974-155">To run tests that have either a <xref:System.Reflection.Module.FullyQualifiedName> containing `UnitTest1` **and** have a `Category` of `"CategoryA"` **or** have a `Property` with a `"Priority"` of `1`.</span></span>

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

<span data-ttu-id="23974-156">Aby uzyskać więcej informacji, zobacz [przypadku testowego Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span><span class="sxs-lookup"><span data-stu-id="23974-156">For more information, see [TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).</span></span>

:::zone-end

## <a name="see-also"></a><span data-ttu-id="23974-157">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23974-157">See also</span></span>

- [<span data-ttu-id="23974-158">dotnet test</span><span class="sxs-lookup"><span data-stu-id="23974-158">dotnet test</span></span>](../tools/dotnet-test.md)
- [<span data-ttu-id="23974-159">Test dotnet--Filter</span><span class="sxs-lookup"><span data-stu-id="23974-159">dotnet test --filter</span></span>](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a><span data-ttu-id="23974-160">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="23974-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="23974-161">Zamów testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="23974-161">Order unit tests</span></span>](order-unit-tests.md)
