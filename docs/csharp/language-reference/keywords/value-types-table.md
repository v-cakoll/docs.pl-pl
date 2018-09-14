---
title: Tabela typów wartości (odwołanie w C#)
ms.date: 08/24/2018
helpviewer_keywords:
- value types [C#], table
- types [C#], value types
- types [C#], suffixes
ms.assetid: 67d8f631-b6e3-4d83-9910-5ec497f8c5f3
ms.openlocfilehash: bc7143b9f006af20b0bb91203d3093410d4ac0bf
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45609726"
---
# <a name="value-types-table-c-reference"></a>Tabela typów wartości (odwołanie w C#)

W poniższej tabeli przedstawiono typy wartości języka C#.  
  
|Typ wartości|Kategoria|Sufiksem typu|  
|----------------|--------------|-----------------|  
|[bool](bool.md)|Boolean||  
|[byte](byte.md)|Nieoznaczona, numeryczne, [typu całkowitego](integral-types-table.md)||  
|[char](char.md)|Nieoznaczona, numeryczne, [typu całkowitego](integral-types-table.md)||  
|[decimal](decimal.md)|Numeryczne, [zmiennoprzecinkowych](floating-point-types-table.md)|M lub m|  
|[double](double.md)|Numeryczne, [zmiennoprzecinkowych](floating-point-types-table.md)|D lub d|  
|[enum](enum.md)|Wyliczenie||  
|[float](float.md)|Numeryczne, [zmiennoprzecinkowych](floating-point-types-table.md)|F lub f|  
|[int](int.md)|Podpisany, numeryczne, [typu całkowitego](integral-types-table.md)||  
|[long](long.md)|Podpisany, numeryczne, [typu całkowitego](integral-types-table.md)|L lub l|  
|[sbyte](sbyte.md)|Podpisany, numeryczne, [typu całkowitego](integral-types-table.md)||  
|[short](short.md)|Podpisany, numeryczne, [typu całkowitego](integral-types-table.md)||  
|[struct](struct.md)|Struktura zdefiniowanych przez użytkownika||  
|[uint](uint.md)|Nieoznaczona, numeryczne, [typu całkowitego](integral-types-table.md)|U lub u|  
|[ulong](ulong.md)|Nieoznaczona, numeryczne, [typu całkowitego](integral-types-table.md)|UL, Ul, uL, ul, LU, Lu, lU lub lu|  
|[ushort](ushort.md)|Nieoznaczona, numeryczne, [typu całkowitego](integral-types-table.md)||  

## <a name="remarks"></a>Uwagi

Sufiksem typu umożliwia określenie typu literał wartości liczbowych. Na przykład:

```csharp
decimal a = 0.1M;
```

Jeśli [literał numeryczny liczby całkowitej](/dotnet/csharp/language-reference/language-specification/lexical-structure#integer-literals) nie sufiks ma pierwszy następujące typy, w których jej wartość może być reprezentowana: `int`, `uint`, `long`, `ulong`.

Jeśli [literał liczby rzeczywistej wartości liczbowych](/dotnet/csharp/language-reference/language-specification/lexical-structure#real-literals) nie sufiks jest typu `double`.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Tabele odwołań dla typów](reference-tables-for-types.md)
- [Tabela wartości domyślnych](default-values-table.md)
- [Typy wartości](value-types.md)
- [Formatowanie tabeli wyników liczbowych](formatting-numeric-results-table.md)
