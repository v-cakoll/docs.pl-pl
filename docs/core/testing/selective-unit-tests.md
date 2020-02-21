---
title: Uruchamianie selektywnych testów jednostkowych
description: Jak używać wyrażenia filtru do uruchamiania selektywnych testów jednostkowych za pomocą polecenia Test dotnet w programie .NET Core.
author: smadala
ms.date: 03/22/2017
ms.openlocfilehash: b9156300587215e68c01c609e298dbc1a2c53d11
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543511"
---
# <a name="running-selective-unit-tests"></a>Uruchamianie selektywnych testów jednostkowych

Za pomocą polecenia `dotnet test` w programie .NET Core można użyć wyrażenia filtru, aby uruchomić testy selektywne. W tym artykule pokazano, jak odfiltrować, który test jest uruchamiany. W poniższych przykładach użyto `dotnet test`. Jeśli używasz `vstest.console.exe`, Zastąp `--filter` `--testcasefilter:`.

> [!NOTE]
> Użycie filtrów, które zawierają znak wykrzyknika (!) na `*nix` wymaga ucieczki, ponieważ `!` jest zarezerwowany. Na przykład ten filtr pomija wszystkie testy, jeśli przestrzeń nazw zawiera IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.
> Zwróć uwagę na ukośnik odwrotny poprzedzający wykrzyknik.

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
| `dotnet test --filter Method` | Uruchamia testy, których `FullyQualifiedName` zawiera `Method`. Dostępne w `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Uruchamia testy, których nazwa zawiera `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Uruchamia testy, które znajdują się w klasie `MSTestNamespace.UnitTest1`.<br>**Uwaga:** Wartość `ClassName` powinna mieć przestrzeń nazw, dlatego `ClassName=UnitTest1` nie będzie działała. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Uruchamia testy, które są opatrzone adnotacją `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Uruchamia testy, które są opatrzone adnotacją `[Priority(2)]`.<br>

**Używanie operatorów warunkowych | i &amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Uruchamia testy, które mają `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` to 1. |

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
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Uruchamia tylko jeden test, `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1`. |

W przykładzie kodu zdefiniowane cechy z kluczami `Category` i `Priority` mogą służyć do filtrowania.

| Wyrażenie | Wynik |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Uruchamia testy, których `FullyQualifiedName` zawiera `XUnit`.  Dostępne w `vstest 15.1+`. |
| `dotnet test --filter Category=CategoryA` | Uruchamia testy, które mają `[Trait("Category", "CategoryA")]`. |

**Używanie operatorów warunkowych | i &amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | Uruchamia testy, które mają `TestClass1` w `FullyQualifiedName` **lub** `Category` jest `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | Uruchamia testy, które mają `TestClass1` w `FullyQualifiedName` **i** `Category` `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | Uruchamia testy, które mają `FullyQualifiedName` zawierający `TestClass1` **i** `Category` jest `CategoryA` **lub** `Priority` to 1. |

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
| `dotnet test --filter Method` | Uruchamia testy, których `FullyQualifiedName` zawiera `Method`. Dostępne w `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Uruchamia testy, których nazwa zawiera `TestMethod1`. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Uruchamia testy, które znajdują się w klasie `NUnitNamespace.UnitTest1`.<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Uruchamia wszystkie testy z wyjątkiem `NUnitNamespace.UnitTest1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Uruchamia testy, które są opatrzone adnotacją `[Category("CategoryA")]`. |
| `dotnet test --filter Priority=2` | Uruchamia testy, które są opatrzone adnotacją `[Priority(2)]`.<br>

**Używanie operatorów warunkowych | i &amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Uruchamia testy, które mają `UnitTest1` w `FullyQualifiedName` **i** `TestCategory` `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Uruchamia testy, które mają `FullyQualifiedName` zawierający `UnitTest1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` to 1. |
