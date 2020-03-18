---
title: Uruchamianie selektywnych testów jednostkowych
description: Jak używać wyrażenia filtru do uruchamiania testów jednostek selektywnych za pomocą polecenia testu dotnet w .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: b9156300587215e68c01c609e298dbc1a2c53d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543511"
---
# <a name="running-selective-unit-tests"></a>Uruchamianie selektywnych testów jednostkowych

Za `dotnet test` pomocą polecenia w .NET Core można użyć wyrażenia filtru do uruchamiania testów selektywnych. W tym artykule pokazano, jak filtrować, które testy są uruchamiane. W poniższych `dotnet test`przykładach używa się . Jeśli używasz `vstest.console.exe`, zamień `--filter` na `--testcasefilter:`.

> [!NOTE]
> Korzystanie z filtrów, które zawierają `*nix` wykrzyknik (!) na wymaga ucieczki, ponieważ `!` jest zarezerwowany. Na przykład ten filtr pomija wszystkie testy, jeśli `dotnet test --filter FullyQualifiedName\!~IntegrationTests`obszar nazw zawiera IntegrationTests: .
> Zwróć uwagę na ukośnik odwrotny, który poprzedza wykrzyknik.

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
| `dotnet test --filter Method` | Uruchamia testy, których `FullyQualifiedName` zawiera `Method`. Dostępne `vstest 15.1+`w . |
| `dotnet test --filter Name~TestMethod1` | Uruchamia testy, `TestMethod1`których nazwa zawiera . |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Uruchamia testy, które `MSTestNamespace.UnitTest1`są w klasie .<br>**Uwaga:** Wartość `ClassName` powinna mieć obszar nazw, więc `ClassName=UnitTest1` nie będzie działać. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Uruchamia wszystkie `MSTestNamespace.UnitTest1.TestMethod1`testy z wyjątkiem . |
| `dotnet test --filter TestCategory=CategoryA` | Uruchamia testy, które są `[TestCategory("CategoryA")]`z adnotatorem . |
| `dotnet test --filter Priority=2` | Uruchamia testy, które są `[Priority(2)]`z adnotatorem .<br>

**Korzystanie z operatorów warunkowych | I&amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Uruchamia testy, `UnitTest1` `FullyQualifiedName` które `CategoryA`mają **lub** `TestCategory` są . |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Uruchamia testy, `UnitTest1` `FullyQualifiedName` które `CategoryA`mają **i** `TestCategory` jest . |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Uruchamia testy, `FullyQualifiedName` które `UnitTest1` zawierają `CategoryA` **i** `TestCategory` jest **lub** `Priority` jest 1. |

## <a name="xunit"></a>Xunit

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
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Uruchamia tylko jeden `XUnitNamespace.TestClass1.Test1`test, . |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Uruchamia wszystkie `XUnitNamespace.TestClass1.Test1`testy z wyjątkiem . |
| `dotnet test --filter DisplayName~TestClass1` | Uruchamia testy, których `TestClass1`nazwa wyświetlana zawiera . |

W przykładzie kodu zdefiniowane cechy z `Category` `Priority` kluczami i mogą być używane do filtrowania.

| Wyrażenie | Wynik |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Uruchamia testy, których `FullyQualifiedName` zawiera `XUnit`.  Dostępne `vstest 15.1+`w . |
| `dotnet test --filter Category=CategoryA` | Uruchamia testy, `[Trait("Category", "CategoryA")]`które mają . |

**Korzystanie z operatorów warunkowych | I&amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | Uruchamia testy, `TestClass1` `FullyQualifiedName` które `CategoryA`mają **lub** `Category` są . |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | Uruchamia testy, `TestClass1` `FullyQualifiedName` które `CategoryA`ma **i** `Category` jest . |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | Uruchamia testy, `FullyQualifiedName` które `TestClass1` zawierają `CategoryA` **i** `Category` jest **lub** `Priority` jest 1. |

## <a name="nunit"></a>Nunit

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
| `dotnet test --filter Method` | Uruchamia testy, których `FullyQualifiedName` zawiera `Method`. Dostępne `vstest 15.1+`w . |
| `dotnet test --filter Name~TestMethod1` | Uruchamia testy, `TestMethod1`których nazwa zawiera . |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Uruchamia testy, które `NUnitNamespace.UnitTest1`są w klasie .<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Uruchamia wszystkie `NUnitNamespace.UnitTest1.TestMethod1`testy z wyjątkiem . |
| `dotnet test --filter TestCategory=CategoryA` | Uruchamia testy, które są `[Category("CategoryA")]`z adnotatorem . |
| `dotnet test --filter Priority=2` | Uruchamia testy, które są `[Priority(2)]`z adnotatorem .<br>

**Korzystanie z operatorów warunkowych | I&amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Uruchamia testy, `UnitTest1` `FullyQualifiedName` które `CategoryA`mają **lub** `TestCategory` są . |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Uruchamia testy, `UnitTest1` `FullyQualifiedName` które `CategoryA`mają **i** `TestCategory` jest . |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Uruchamia testy, `FullyQualifiedName` które `UnitTest1` zawierają `CategoryA` **i** `TestCategory` jest **lub** `Priority` jest 1. |
