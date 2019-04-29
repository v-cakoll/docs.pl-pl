---
title: Typy — wartości C# odwołania
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 5ff883e541c614832286b4027bc1574952f8fd3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660258"
---
# <a name="value-types-c-reference"></a>Typy wartości (C# odwołania)

Istnieją dwa rodzaje typów wartości:

- [Struktury](struct.md)

- [Wyliczenia](enum.md)

## <a name="main-features-of-value-types"></a>Główne funkcje typów wartości

Zmienna typu wartości zawiera wartość typu. Na przykład zmiennej `int` typ może zawierać wartość `42`. To różni się od zmiennej typu odwołania, który zawiera odwołanie do wystąpienia typu, znany także jako obiekt. Po przypisaniu nową wartość do zmiennej typu wartości jest kopiowana. Po przypisaniu nową wartość do zmiennej typu odwołania odwołanie jest kopiowane, nie samego obiektu.

Wszystkie typy wartości niejawnie pochodzą od <xref:System.ValueType?displayProperty=nameWithType>.

Inaczej niż w przypadku typów referencyjnych nie może pochodzić nowy typ z typem wartości. Jednakże, takie jak typy odwołań struktury mogą implementować interfejsów.

Zmienne typu wartości nie może być `null` domyślnie. Jednakże zmienne odpowiadającego [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md) może być `null`.

Każdy typ wartości ma niejawnego konstruktora bez parametrów, która inicjuje wartością domyślną tego typu. Aby uzyskać informacje o wartościach domyślnych typów wartości, zobacz [tabela wartości domyślnych](default-values-table.md).

## <a name="simple-types"></a>Typy proste

*Typów prostych* zestaw wstępnie zdefiniowanych struktura typów dostarczonych przez C# i składają się następujące typy:

- [Typy całkowite](integral-types-table.md): liczbowych typów całkowitych i [char](char.md) typu
- [Typy zmiennoprzecinkowe](floating-point-types-table.md)
- [bool](bool.md)

Proste typy są identyfikowane za pomocą słów kluczowych, ale te słowa kluczowe są po prostu aliasami dla struktury wstępnie zdefiniowanych typów w pakietach <xref:System> przestrzeni nazw. Na przykład [int](int.md) jest aliasem <xref:System.Int32?displayProperty=nameWithType>. Aby uzyskać pełną listę aliasów, zobacz [Tabela typów wbudowanych](built-in-types-table.md).

Proste typy różnią się od innych typów struktury w sposób, aby umożliwić pewne dodatkowe operacje:

- Proste typy mogą być inicjowane za pomocą literałów ciągów. Na przykład `'A'` jest literał o typie `char` i `2001` jest literał o typie `int`.

- Można zadeklarować stałe proste typy z [const](const.md) — słowo kluczowe. Nie jest możliwe stałe inne typy struktury.

- Wyrażenia stałe, w której argumenty operacji są stałymi typu prostego, są oceniane w czasie kompilacji.

Aby uzyskać więcej informacji, zobacz [typów prostych](~/_csharplang/spec/types.md#simple-types) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="initializing-value-types"></a>Inicjowanie typów wartości

Zmienne lokalne w języku C# muszą zostać zainicjowane, przed są one używane. Na przykład może zadeklarować zmienną lokalną bez inicjowania, jak w poniższym przykładzie:

```csharp
int myInt;
```

Nie można użyć go, przed jej inicjalizację. Można zainicjować za pomocą następującej instrukcji:

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

Ta instrukcja jest równoważna następującej instrukcji:

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

Można oczywiście masz deklaracji i inicjowania w tej samej instrukcji, co pokazano w następujących przykładach:

```csharp
int myInt = new int();
```

— lub —

```csharp
int myInt = 0;
```

Za pomocą [nowe](new.md) operator wywołuje konstruktora bez parametrów od określonego typu i przypisuje wartość domyślną do zmiennej. W powyższym przykładzie konstruktora bez parametrów przypisaną wartość `0` do `myInt`. Aby uzyskać więcej informacji na temat wartości przypisane przez wywołanie metody konstruktory domyślne zobacz [tabela wartości domyślnych](default-values-table.md).

W przypadku typów zdefiniowanych przez użytkownika, należy użyć [nowe](new.md) do wywołania konstruktora bez parametrów. Na przykład następująca instrukcja wywołuje konstruktora bez parametrów z `Point` struktury:

```csharp
Point p = new Point(); // Invoke parameterless constructor for the struct.
```

Po tym wywołaniu struktury uznaje się być zdecydowanie przypisywany; oznacza to, że wszystkie jego elementy członkowskie są inicjowane do wartości domyślnych.

Aby uzyskać więcej informacji na temat `new` operatora, zobacz [nowe](new.md).

Aby dowiedzieć się, jak formatowanie danych wyjściowych typów liczbowych, zobacz [formatowanie tabeli wyników liczbowych](formatting-numeric-results-table.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy](types.md)
- [Tabele odwołań dla typów](reference-tables-for-types.md)
- [Typy odwołań](reference-types.md)
- [Typy dopuszczające wartości zerowe](../../programming-guide/nullable-types/index.md)