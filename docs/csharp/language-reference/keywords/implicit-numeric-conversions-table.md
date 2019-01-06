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
ms.openlocfilehash: ab6506e619c675ddd68237c4ddca870e9e14098f
ms.sourcegitcommit: deb9225a55485a5a6e6c7914deb30ccfceb69d3f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2019
ms.locfileid: "54058467"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tabela niejawnych konwersji liczbowych (odwołanie w C#)

W poniższej tabeli przedstawiono wstępnie zdefiniowanych niejawne konwersje między typów liczbowych .NET.
  
|Z|Zadanie|  
|----------|--------|  
|[sbyte](sbyte.md)|`short`, `int`, `long`, `float`, `double`, lub `decimal`|  
|[byte](byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`|  
|[char](char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`|  
|[short](short.md)|`int`, `long`, `float`, `double`, lub `decimal`|  
|[ushort](ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`|  
|[int](int.md)|`long`, `float`, `double`, lub `decimal`|  
|[uint](uint.md)|`long`, `ulong`, `float`, `double`, lub `decimal`|  
|[long](long.md)|`float`, `double`, lub `decimal`|  
|[ulong](ulong.md)|`float`, `double`, lub `decimal`|  
|[float](float.md)|`double`|  
  
## <a name="remarks"></a>Uwagi  

- Wszelkie [typu całkowitego](integral-types-table.md) jest niejawnie konwertowany na dowolny [typu zmiennoprzecinkowego](floating-point-types-table.md).

- Dokładności, ale wartość nie może być utracone w konwersje z `int`, `uint`, `long`, lub `ulong` do `float` i `long` lub `ulong` do `double`.  
  
- Brak konwersji niejawnych do `char`, `byte` i `sbyte` typów.  

- Brak niejawnej konwersji z `char`, `double` i `decimal` typów.
  
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
- [Tabela typów całkowitych](integral-types-table.md)
- [Tabela typów zmiennoprzecinkowych](floating-point-types-table.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Tabela jawnych konwersji liczbowych](explicit-numeric-conversions-table.md)
- [Konwersje rzutowania i typ](../../programming-guide/types/casting-and-type-conversions.md)
