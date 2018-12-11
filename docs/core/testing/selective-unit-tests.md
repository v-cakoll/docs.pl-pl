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
# <a name="running-selective-unit-tests"></a>Uruchamianie selektywnych testów jednostkowych

W poniższych przykładach używane `dotnet test`. Jeśli używasz `vstest.console.exe`, Zastąp `--filter ` z `--testcasefilter:`.

## <a name="mstest"></a>MSTest

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

| Wyrażenie | Wynik |
| ---------- | ------ |
| `dotnet test --filter Method` | Przebiegi testów, których `FullyQualifiedName` zawiera `Method`. Dostępne w `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Uruchamia testy, których nazwa zawiera `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Uruchamia testy, które są w klasie `MSTestNamespace.UnitTest1`.<br>**Uwaga:** `ClassName` Wartości powinny mieć obszaru nazw, więc `ClassName=UnitTest1` nie będzie działać. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Uruchamia testy, które są przypisane przy użyciu `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Uruchamia testy, które są przypisane przy użyciu `[Priority(2)]`.<br>

**Za pomocą operatorów warunkowych | i &amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1. |

## <a name="xunit"></a>xUnit

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

| Wyrażenie | Wynik |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Uruchamia tylko jeden test `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1`. |

W przykładzie kodu zdefiniowanych cech przy użyciu kluczy `Category` i `Priority` może służyć do filtrowania.

| Wyrażenie | Wynik |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Przebiegi testów, których `FullyQualifiedName` zawiera `XUnit`.  Dostępne w `vstest 15.1+`. |
| `dotnet test --filter Category=CategoryA` | Uruchamia testy, które mają `[Trait("Category", "CategoryA")]`. |

**Za pomocą operatorów warunkowych | i &amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | Przebiegów testów, które ma `TestClass1` w `FullyQualifiedName` **lub** `Category` jest `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | Przebiegów testów, które ma `TestClass1` w `FullyQualifiedName` **i** `Category` jest `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `TestClass1` **i** `Category` jest `CategoryA` **lub** `Priority` 1. |

## <a name="nunit"></a>Rozszerzenie NUnit

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

| Wyrażenie | Wynik |
| ---------- | ------ |
| `dotnet test --filter Method` | Przebiegi testów, których `FullyQualifiedName` zawiera `Method`. Dostępne w `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Uruchamia testy, których nazwa zawiera `TestMethod1`. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Uruchamia testy, które są w klasie `NUnitNamespace.UnitTest1`.<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Uruchamia wszystkie testy z wyjątkiem `NUnitNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Uruchamia testy, które są przypisane przy użyciu `[Category("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Uruchamia testy, które są przypisane przy użyciu `[Priority(2)]`.<br>

**Za pomocą operatorów warunkowych | i &amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Uruchamia testy, które mają jedną `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1. |
