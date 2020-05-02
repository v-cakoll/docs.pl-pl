---
title: Uruchamianie selektywnych testów jednostkowych
description: Jak używać wyrażenia filtru do uruchamiania selektywnych testów jednostkowych za pomocą polecenia Test dotnet w programie .NET Core.
author: smadala
ms.date: 04/29/2020
ms.openlocfilehash: 50642126f3b470180ddd303ed4a2d2d90bfa5b8f
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728183"
---
# <a name="run-selective-unit-tests"></a>Uruchamianie selektywnych testów jednostkowych

Za pomocą `dotnet test` polecenia w programie .NET Core można używać wyrażenia filtru do uruchamiania selektywnych testów. W tym artykule przedstawiono sposób filtrowania, które testy są uruchamiane. W poniższych przykładach `dotnet test`użyto. Jeśli używasz programu `vstest.console.exe`, Zamień `--filter` na. `--testcasefilter:`

## <a name="character-escaping"></a>Znak ucieczki

Użycie filtrów, które zawierają znak wykrzyknika (! `*nix` ), wymaga ucieczki, ponieważ `!` jest zarezerwowany. Na przykład ten filtr pomija wszystkie testy, jeśli przestrzeń nazw zawiera IntegrationTests: `dotnet test --filter FullyQualifiedName\!~IntegrationTests`.
Zwróć uwagę na ukośnik odwrotny poprzedzający wykrzyknik.

Dla `FullyQualifiedName` wartości, które zawierają przecinek dla parametrów typu generycznego, wpisz przecinek `%2C`. Przykład:

```dotnetcli
dotnet test --filter "FullyQualifiedName=MyNamespace.MyTestsClass<ParameterType1%2CParameterType2>.MyTestMethod"
```

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
| `dotnet test --filter Method` | Uruchamia testy, `FullyQualifiedName` których `Method`zawiera. Dostępne w `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Uruchamia testy, których nazwa `TestMethod1`zawiera. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Uruchamia testy, które znajdują `MSTestNamespace.UnitTest1`się w klasie.<br>**Uwaga:** `ClassName` Wartość powinna mieć przestrzeń nazw, dlatego `ClassName=UnitTest1` nie będzie działała. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Uruchamia wszystkie testy z `MSTestNamespace.UnitTest1.TestMethod1`wyjątkiem. |
| `dotnet test --filter TestCategory=CategoryA` | Uruchamia testy, które są opatrzone `[TestCategory("CategoryA")]`adnotacją. |
| `dotnet test --filter Priority=2` | Uruchamia testy, które są opatrzone `[Priority(2)]`adnotacją.<br>

**Używanie operatorów warunkowych | lub&amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Uruchamia testy, które `UnitTest1` mają `FullyQualifiedName` w **lub** `TestCategory` jest `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Uruchamia testy, które `UnitTest1` mają `FullyQualifiedName` w **i** `TestCategory` to `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Uruchamia testy z parametrami `FullyQualifiedName` zawierającymi `UnitTest1` **i** `TestCategory` is `CategoryA` **lub** `Priority` 1. |

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
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Uruchamia wszystkie testy z `XUnitNamespace.TestClass1.Test1`wyjątkiem. |
| `dotnet test --filter DisplayName~TestClass1` | Uruchamia testy, których nazwa wyświetlana `TestClass1`zawiera. |

W przykładzie kodu, zdefiniowane cechy z kluczami `Category` i `Priority` mogą być używane do filtrowania.

| Wyrażenie | Wynik |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Uruchamia testy, `FullyQualifiedName` których `XUnit`zawiera.  Dostępne w `vstest 15.1+`. |
| `dotnet test --filter Category=CategoryA` | Uruchamia testy, które `[Trait("Category", "CategoryA")]`mają. |

**Używanie operatorów warunkowych | lub&amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=CategoryA"</code> | Uruchamia testy, które `TestClass1` mają `FullyQualifiedName` w **lub** `Category` jest `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"` | Uruchamia testy, które `TestClass1` mają `FullyQualifiedName` w **i** `Category` to `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=CategoryA)&#124;Priority=1"</code> | Uruchamia testy z parametrami `FullyQualifiedName` zawierającymi `TestClass1` **i** `Category` is `CategoryA` **lub** `Priority` 1. |

## <a name="nunit"></a>NUnit

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
| `dotnet test --filter Method` | Uruchamia testy, `FullyQualifiedName` których `Method`zawiera. Dostępne w `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Uruchamia testy, których nazwa `TestMethod1`zawiera. |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Uruchamia testy, które znajdują `NUnitNamespace.UnitTest1`się w klasie.<br>
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Uruchamia wszystkie testy z `NUnitNamespace.UnitTest1.TestMethod1`wyjątkiem. |
| `dotnet test --filter TestCategory=CategoryA` | Uruchamia testy, które są opatrzone `[Category("CategoryA")]`adnotacją. |
| `dotnet test --filter Priority=2` | Uruchamia testy, które są opatrzone `[Priority(2)]`adnotacją.<br>

**Używanie operatorów warunkowych | lub&amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTest1&#124;TestCategory=CategoryA"</code> | Uruchamia testy, które `UnitTest1` mają `FullyQualifiedName` w **lub** `TestCategory` jest `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"` | Uruchamia testy, które `UnitTest1` mają `FullyQualifiedName` w **i** `TestCategory` to `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)&#124;Priority=1"</code> | Uruchamia testy z parametrami `FullyQualifiedName` zawierającymi `UnitTest1` **i** `TestCategory` is `CategoryA` **lub** `Priority` 1. |

Aby uzyskać więcej informacji, zobacz [przypadku testowego Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).
