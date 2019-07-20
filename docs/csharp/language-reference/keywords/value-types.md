---
title: Typy wartości — C# odwołanie
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 72771ee494b6be7142ce3f9bec43dcb8aa8a8401
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363088"
---
# <a name="value-types-c-reference"></a>Typy wartości (C# odwołanie)

Istnieją dwa rodzaje typów wartości:

- [Struktury](struct.md)

- [Wyliczenia](enum.md)

## <a name="main-features-of-value-types"></a>Główne funkcje typów wartości

Zmienna typu wartości zawiera wartość typu. Na przykład zmienna `int` typu może zawierać wartość `42`. Różni się to od zmiennej typu referencyjnego, która zawiera odwołanie do wystąpienia typu, znanego również jako obiekt. Gdy przypiszesz nową wartość do zmiennej typu wartości, ta wartość jest kopiowana. Gdy przypiszesz nową wartość do zmiennej typu referencyjnego, odwołanie jest kopiowane, a nie samego obiektu.

Wszystkie typy wartości są wyprowadzane niejawnie <xref:System.ValueType?displayProperty=nameWithType>z.

W przeciwieństwie do typów referencyjnych nie można utworzyć nowego typu z typu wartości. Jednak takie jak typy odwołań, struktury mogą implementować interfejsy.

Zmienne typu wartości nie mogą `null` być domyślnie. Jednak zmienne odpowiednich [typów dopuszczających wartości null](../../../csharp/programming-guide/nullable-types/index.md) mogą być `null`.

Każdy typ wartości ma niejawny Konstruktor bez parametrów, który inicjuje wartość domyślną tego typu. Aby uzyskać informacje o domyślnych wartościach typów wartości, zobacz [tabela wartości domyślnych](default-values-table.md).

## <a name="simple-types"></a>Typy proste

*Typy proste* są zestawem wstępnie zdefiniowanych typów struktur udostępnianych przez C# i składają się z następujących typów:

- [Typy całkowite](../builtin-types/integral-numeric-types.md): typy liczbowe liczb całkowitych i typ [char](char.md)
- [Typy zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md)
- [bool](bool.md)

Typy proste są identyfikowane za pomocą słów kluczowych, ale te słowa kluczowe są po prostu aliasami dla <xref:System> wstępnie zdefiniowanych typów struktur w przestrzeni nazw. Na przykład [int](../builtin-types/integral-numeric-types.md) jest aliasem <xref:System.Int32?displayProperty=nameWithType>. Aby uzyskać pełną listę aliasów, zobacz [Tabela typów wbudowanych](built-in-types-table.md).

Proste typy różnią się od innych typów struktur w tym, że dopuszczają pewne dodatkowe operacje:

- Typy proste można inicjować przy użyciu literałów. Na przykład `'A'` jest literałem typu `char` i `2001` jest literałem typu `int`.

- Stałe typów prostych można zadeklarować za pomocą słowa kluczowego [const](const.md) . Nie jest możliwe posiadanie stałych z innych typów struktur.

- Wyrażenia stałe, których operandy to wszystkie proste typy stałe, są oceniane w czasie kompilacji.

Aby uzyskać więcej informacji, zobacz sekcję [typy proste](~/_csharplang/spec/types.md#simple-types) [ C# specyfikacji języka](../language-specification/index.md).

## <a name="initializing-value-types"></a>Inicjowanie typów wartości

Zmienne lokalne w C# programie muszą zostać zainicjowane przed ich użyciem. Na przykład można zadeklarować zmienną lokalną bez inicjalizacji, jak w poniższym przykładzie:

```csharp
int myInt;
```

Nie można jej użyć przed zainicjowaniem. Można go zainicjować przy użyciu następującej instrukcji:

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

Ta instrukcja jest równoznaczna z następującą instrukcją:

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

Można oczywiście mieć deklarację i inicjalizację w tej samej instrukcji, jak w następujących przykładach:

```csharp
int myInt = new int();
```

oraz

```csharp
int myInt = 0;
```

Użycie operatora [New](../operators/new-operator.md) wywołuje konstruktora bez parametrów określonego typu i przypisuje wartość domyślną zmiennej. W poprzednim przykładzie Konstruktor bez parametrów przypisał wartość `0` do. `myInt` Aby uzyskać więcej informacji na temat wartości przypisanych przez wywoływanie konstruktorów bez parametrów, zobacz [tabela wartości domyślnych](default-values-table.md).

W przypadku typów zdefiniowanych przez użytkownika Użyj metody [New](../operators/new-operator.md) , aby wywołać Konstruktor bez parametrów. Na przykład następująca instrukcja wywołuje Konstruktor `Point` bez parametrów struktury:

```csharp
var p = new Point(); // Invoke parameterless constructor for the struct.
```

Po tym wywołaniu struktura jest uznawana za ostatecznie przypisaną; oznacza to, że wszystkie jego elementy członkowskie są inicjowane do ich wartości domyślnych.

Aby uzyskać więcej informacji na `new` temat operatora, zobacz [Nowość](../operators/new-operator.md).

Informacje o formatowaniu danych wyjściowych typów liczbowych znajdują się w temacie [formatowanie tabeli wyników liczbowych](formatting-numeric-results-table.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy](types.md)
- [Typy odwołań](reference-types.md)
- [Typy dopuszczające wartości null](../../programming-guide/nullable-types/index.md)
