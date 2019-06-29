---
title: Tabela typów wartości - C# odwołania
ms.custom: seodec18
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: 98829f30c2c25c0710cf3fe044359d3c7538fe76
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424041"
---
# <a name="value-types-table-c-reference"></a>Tabela typów wartości (odwołanie w C#)

W poniższej tabeli przedstawiono C# typów wartości:

|Typ wartości|Kategoria|Sufiksem typu|
|----------------|--------------|-----------------|
|[bool](bool.md)|Boolean||
|[byte](../builtin-types/integral-numeric-types.md)|Nieoznaczona, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)||
|[char](char.md)|Nieoznaczona, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)
)||
|[decimal](decimal.md)|Numeryczne, [zmiennoprzecinkowych](floating-point-types-table.md)|M lub m|
|[double](double.md)|Numeryczne, [zmiennoprzecinkowych](floating-point-types-table.md)|D lub d|
|[enum](enum.md)|Wyliczenie||
|[float](float.md)|Numeryczne, [zmiennoprzecinkowych](floating-point-types-table.md)|F lub f|
|[int](../builtin-types/integral-numeric-types.md)|Podpisany, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)||
|[long](../builtin-types/integral-numeric-types.md)|Podpisany, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)|L lub l|
|[sbyte](../builtin-types/integral-numeric-types.md)|Podpisany, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)||
|[short](../builtin-types/integral-numeric-types.md)|Podpisany, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)||
|[struct](struct.md)|Struktura zdefiniowanych przez użytkownika||
|[uint](../builtin-types/integral-numeric-types.md)|Nieoznaczona, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)|U lub u|
|[ulong](../builtin-types/integral-numeric-types.md)|Nieoznaczona, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)|UL, Ul, uL, ul, LU, Lu, lU lub lu|
|[ushort](../builtin-types/integral-numeric-types.md)|Nieoznaczona, numeryczne, [typu całkowitego](../builtin-types/integral-numeric-types.md)||

## <a name="remarks"></a>Uwagi

Sufiksem typu umożliwia określenie typu literał wartości liczbowych. Na przykład:

```csharp
decimal a = 0.1M;
```

Jeśli [literał numeryczny liczby całkowitej](~/_csharplang/spec/lexical-structure.md#integer-literals) nie sufiks ma pierwszy następujące typy, w których jej wartość może być reprezentowana: `int`, `uint`, `long`, `ulong`.

Jeśli [literał liczby rzeczywistej wartości liczbowych](~/_csharplang/spec/lexical-structure.md#real-literals) nie sufiks jest typu `double`.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Tabela wartości domyślnych](default-values-table.md)
- [Typy wartości](value-types.md)
- [Formatowanie tabeli wyników liczbowych](formatting-numeric-results-table.md)
