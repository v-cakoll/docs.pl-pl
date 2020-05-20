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
# <a name="run-selective-unit-tests"></a>Uruchamianie selektywnych testów jednostkowych

Za pomocą [`dotnet test`](../tools/dotnet-test.md) polecenia w programie .NET Core można używać wyrażenia filtru do uruchamiania selektywnych testów. W tym artykule przedstawiono sposób filtrowania, które testy są uruchamiane. W poniższych przykładach użyto `dotnet test` . Jeśli używasz programu `vstest.console.exe` , Zamień `--filter` na `--testcasefilter:` .

## <a name="character-escaping"></a>Znak ucieczki

Użycie filtrów, które zawierają znak wykrzyknika, `!` `*nix` wymaga ucieczki, ponieważ `!` jest zarezerwowany. Na przykład ten filtr pomija wszystkie testy, jeśli przestrzeń nazw zawiera IntegrationTests:

```dotnetcli
dotnet test --filter FullyQualifiedName\!~IntegrationTests
```

> [!IMPORTANT]
> Ukośnik odwrotny poprzedza znak wykrzyknika, aby wskazać, że jest znakiem ucieczki `\!` .

Dla `FullyQualifiedName` wartości, które zawierają przecinek dla parametrów typu generycznego, wpisz przecinek `%2C` . Na przykład:

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

| Wyrażenie | Wynik |
|--|--|
| `dotnet test --filter Method` | Uruchamia testy, których <xref:System.Reflection.Module.FullyQualifiedName> zawiera `Method` . Dostępne w `vstest 15.1+` . |
| `dotnet test --filter Name~TestMethod1` | Uruchamia testy, których nazwa zawiera `TestMethod1` . |
| `dotnet test --filter ClassName=MSTestNamespace.UnitTest1` | Uruchamia testy, które znajdują się w klasie `MSTestNamespace.UnitTest1` .<br>**Uwaga:** `ClassName`Wartość powinna mieć przestrzeń nazw, dlatego `ClassName=UnitTest1` nie będzie działała. |
| `dotnet test --filter FullyQualifiedName!=MSTestNamespace.UnitTest1.TestMethod1` | Uruchamia wszystkie testy z wyjątkiem `MSTestNamespace.UnitTest1.TestMethod1` . |
| `dotnet test --filter TestCategory=CategoryA` | Uruchamia testy, które są opatrzone adnotacją `[TestCategory("CategoryA")]` . |
| `dotnet test --filter Priority=2` | Uruchamia testy, które są opatrzone adnotacją `[Priority(2)]` . |

Przykłady wykorzystujące operatory warunkowe `|` i `&` :

Do uruchamiania testów, które mają `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **lub** <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> są `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

Do uruchamiania testów, które znajdują się `UnitTest1` w ich <xref:System.Reflection.Module.FullyQualifiedName> **i** mają <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

Do uruchamiania testów, które mają <xref:System.Reflection.Module.FullyQualifiedName> `UnitTest1` **co** najmniej jeden z <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute> `"CategoryA"` **lub** mają <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute> priorytet `1` .

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

| Wyrażenie | Wynik |
|--|--|
| `dotnet test --filter DisplayName=XUnitNamespace.TestClass1.Test1` | Uruchamia tylko jeden test, `XUnitNamespace.TestClass1.Test1` . |
| `dotnet test --filter FullyQualifiedName!=XUnitNamespace.TestClass1.Test1` | Uruchamia wszystkie testy z wyjątkiem `XUnitNamespace.TestClass1.Test1` . |
| `dotnet test --filter DisplayName~TestClass1` | Uruchamia testy, których nazwa wyświetlana zawiera `TestClass1` . |

W przykładzie kodu, zdefiniowane cechy z kluczami `"Category"` i `"Priority"` mogą być używane do filtrowania.

| Wyrażenie | Wynik |
|--|--|
| `dotnet test --filter XUnit` | Uruchamia testy, których <xref:System.Reflection.Module.FullyQualifiedName> zawiera `XUnit` .  Dostępne w `vstest 15.1+` . |
| `dotnet test --filter Category=CategoryA` | Uruchamia testy, które mają `[Trait("Category", "CategoryA")]` . |

Przykłady wykorzystujące operatory warunkowe `|` i `&` :

Do uruchamiania testów, które mają `TestClass1` <xref:System.Reflection.Module.FullyQualifiedName> **lub** mają `Trait` klucz `"Category"` i wartość `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1|Category=CategoryA"
```

Do uruchamiania testów, które mają `TestClass1` <xref:System.Reflection.Module.FullyQualifiedName> **i** mają klucz o `Trait` `"Category"` i wartości `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~TestClass1&Category=CategoryA"
```

Do uruchamiania testów, które zawierają <xref:System.Reflection.Module.FullyQualifiedName> `TestClass1` **i** mają klucz z `Trait` `"Category"` i wartością `"CategoryA"` **lub** mają klucz z i `Trait` `"Priority"` wartość `1` .

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

| Wyrażenie | Wynik |
|--|--|
| `dotnet test --filter Method` | Uruchamia testy, których <xref:System.Reflection.Module.FullyQualifiedName> zawiera `Method` . Dostępne w `vstest 15.1+` . |
| `dotnet test --filter Name~TestMethod1` | Uruchamia testy, których nazwa zawiera `TestMethod1` . |
| `dotnet test --filter FullyQualifiedName~NUnitNamespace.UnitTest1` | Uruchamia testy, które znajdują się w klasie `NUnitNamespace.UnitTest1` . |
| `dotnet test --filter FullyQualifiedName!=NUnitNamespace.UnitTest1.TestMethod1` | Uruchamia wszystkie testy z wyjątkiem `NUnitNamespace.UnitTest1.TestMethod1` . |
| `dotnet test --filter TestCategory=CategoryA` | Uruchamia testy, które są opatrzone adnotacją `[Category("CategoryA")]` . |
| `dotnet test --filter Priority=2` | Uruchamia testy, które są opatrzone adnotacją `[Priority(2)]` . |

Przykłady wykorzystujące operatory warunkowe `|` i `&` :

Do uruchamiania testów, które mają `UnitTest1` <xref:System.Reflection.Module.FullyQualifiedName> **lub** mają `Category` `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1|TestCategory=CategoryA"
```

Do uruchamiania testów, które znajdują się `UnitTest1` w ich <xref:System.Reflection.Module.FullyQualifiedName> **i** mają `Category` `"CategoryA"` .

```dotnetcli
dotnet test --filter "FullyQualifiedName~UnitTest1&TestCategory=CategoryA"
```

Do uruchamiania testów, które mają element <xref:System.Reflection.Module.FullyQualifiedName> zawierający `UnitTest1` **i** ma `Category` `"CategoryA"` **lub** mieć z `Property` `"Priority"` `1` .

```dotnetcli
dotnet test --filter "(FullyQualifiedName~UnitTest1&TestCategory=CategoryA)|Priority=1"
```

Aby uzyskać więcej informacji, zobacz [przypadku testowego Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

:::zone-end

## <a name="see-also"></a>Zobacz także

- [dotnet test](../tools/dotnet-test.md)
- [Test dotnet--Filter](../tools/dotnet-test.md#filter-option-details)

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Zamów testy jednostkowe](order-unit-tests.md)
