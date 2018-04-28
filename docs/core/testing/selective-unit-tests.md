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
# <a name="running-selective-unit-tests"></a>Testy jednostkowe Uruchamianie selektywne

W poniższych przykładach użyto `dotnet test`. Jeśli używasz `vstest.console.exe`, Zastąp `--filter ` z `--testcasefilter:`.

## <a name="mstest"></a>MSTest

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

| Wyrażenie | Wynik |
| ---------- | ------ |
| `dotnet test --filter Method` | Uruchamia testy, których `FullyQualifiedName` zawiera `Method`. Dostępne w `vstest 15.1+`. |
| `dotnet test --filter Name~TestMethod1` | Uruchamia testy, których nazwa zawiera `TestMethod1`. |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTestClass1` | Uruchamia testy, które należą do klasy `MSTestNamespace.UnitTestClass1`.<br>**Uwaga:** `ClassName` wartość powinien mieć obszar nazw, dlatego `ClassName=UnitTestClass1` nie będzie działać. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTestClass1.TestMethod1` | Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTestClass1.TestMethod1`. |
| `dotnet test --filter TestCategory=CategoryA` | Uruchamia testy, które są przypisane z `[TestCategory("CategoryA")]`. |
| `dotnet test --filter Priority=3` | Uruchamia testy, które są przypisane z `[Priority(3)]`.<br>**Uwaga:** `Priority~3` wartość jest nieprawidłowa, ponieważ nie jest ciąg. |

**Przy użyciu operatorów warunkowych | i &amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~UnitTestClass1&#124;TestCategory=CategoryA"</code> | Uruchamia testy, które mają `UnitTestClass1` w `FullyQualifiedName` **lub** `TestCategory` jest `CategoryA`. |
| `dotnet test --filter "FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA"` | Uruchamia testy, które mają `UnitTestClass1` w `FullyQualifiedName` **i** `TestCategory` jest `CategoryA`. |
| <code>dotnet test --filter "(FullyQualifiedName~UnitTestClass1&TestCategory=CategoryA)&#124;Priority=1"</code> | Uruchamia testy, które `FullyQualifiedName` zawierający `UnitTestClass1` **i** `TestCategory` jest `CategoryA` **lub** `Priority` 1. |

## <a name="xunit"></a>xUnit

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

| Wyrażenie | Wynik |
| ---------- | ------ |
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Uruchamia test tylko jeden `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1`. |
| `dotnet test --filter DisplayName~TestClass1` | Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1`. |

W przykładzie kodu zdefiniowanych cech z kluczami `Category` i `Priority` może służyć do filtrowania.

| Wyrażenie | Wynik |
| ---------- | ------ |
| `dotnet test --filter XUnit` | Uruchamia testy, których `FullyQualifiedName` zawiera `XUnit`.  Dostępne w `vstest 15.1+`. |
| `dotnet test --filter Category=bvt` | Uruchamia testy, które mają `[Trait("Category", "bvt")]`. |

**Przy użyciu operatorów warunkowych | i &amp;**

| Wyrażenie | Wynik |
| ---------- | ------ |
| <code>dotnet test --filter "FullyQualifiedName~TestClass1&#124;Category=Nightly"</code> | Uruchamia testy, które ma `TestClass1` w `FullyQualifiedName` **lub** `Category` jest `Nightly`. |
| `dotnet test --filter "FullyQualifiedName~TestClass1&Category=Nightly"` | Uruchamia testy, które ma `TestClass1` w `FullyQualifiedName` **i** `Category` jest `Nightly`. |
| <code>dotnet test --filter "(FullyQualifiedName~TestClass1&Category=Nightly)&#124;Priority=1"</code> | Uruchamia testy, które `FullyQualifiedName` zawierający `TestClass1` **i** `Category` jest `CategoryA` **lub** `Priority` 1. |
