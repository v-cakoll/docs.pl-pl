---
title: Tabela niejawnych konwersji liczbowych - C# odwołania
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 516505ccacfd2a8a5c275b0de033e1316fa06d3a
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661338"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tabela niejawnych konwersji liczbowych (odwołanie w C#)

W poniższej tabeli przedstawiono wstępnie zdefiniowanych niejawne konwersje między typów liczbowych .NET.
  
|Z|Zadanie|  
|----------|--------|  
|[sbyte](../builtin-types/integral-numeric-types.md)|`short`, `int`, `long`, `float`, `double`, lub `decimal`|  
|[byte](../builtin-types/integral-numeric-types.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`|  
|[char](char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`|  
|[short](../builtin-types/integral-numeric-types.md)|`int`, `long`, `float`, `double`, lub `decimal`|  
|[ushort](../builtin-types/integral-numeric-types.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`|  
|[int](../builtin-types/integral-numeric-types.md)|`long`, `float`, `double`, lub `decimal`|  
|[uint](../builtin-types/integral-numeric-types.md)|`long`, `ulong`, `float`, `double`, lub `decimal`|  
|[long](../builtin-types/integral-numeric-types.md)|`float`, `double`, lub `decimal`|  
|[ulong](../builtin-types/integral-numeric-types.md)|`float`, `double`, lub `decimal`|  
|[float](../builtin-types/floating-point-numeric-types.md)|`double`|  
  
## <a name="remarks"></a>Uwagi  

- Wszelkie [typu całkowitego](../builtin-types/integral-numeric-types.md) jest niejawnie konwertowany na dowolny [typu zmiennoprzecinkowego](../builtin-types/floating-point-numeric-types.md).

- Dokładności, ale wartość nie może być utracone w konwersje z `int`, `uint`, `long`, lub `ulong` do `float` i `long` lub `ulong` do `double`.  
  
- Brak konwersji niejawnych do `char`, `byte`, i `sbyte` typów.  

- Brak niejawnej konwersji z `double` i `decimal` typów.
  
- Brak niejawnej konwersji między `decimal` typu i `float` lub `double` typów.  
  
- Wartości stałe wyrażenia typu `int` (na przykład, wartość reprezentowany przez całkowite literał) mogą być konwertowane na `sbyte`, `byte`, `short`, `ushort`, `uint`, lub `ulong`, o ile ma on w zakresie typu miejsca docelowego:

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

Aby uzyskać więcej informacji dotyczących niejawnych konwersji, zobacz [niejawne konwersje](~/_csharplang/spec/conversions.md#implicit-conversions) części [specyfikacji języka C#](../language-specification/index.md).
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Typy całkowite](../builtin-types/integral-numeric-types.md)
- [Tabela typów zmiennoprzecinkowych](../builtin-types/floating-point-numeric-types.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Tabela jawnych konwersji liczbowych](explicit-numeric-conversions-table.md)
- [Konwersje rzutowania i typ](../../programming-guide/types/casting-and-type-conversions.md)
