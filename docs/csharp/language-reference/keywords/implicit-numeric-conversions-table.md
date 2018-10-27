---
title: Tabela niejawnych konwersji liczbowych (odwołanie w C#)
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: c3c0153a0ae3e07839822c8bb978b1a09277bd53
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188706"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tabela niejawnych konwersji liczbowych (odwołanie w C#)

W poniższej tabeli przedstawiono wstępnie zdefiniowanych niejawne konwersje między typów liczbowych .NET.
  
|Z|Zadanie|  
|----------|--------|  
|[sbyte](sbyte.md)|`short`, `int`, `long`, `float`, `double`, lub `decimal`|  
|[byte](byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`|  
|[short](short.md)|`int`, `long`, `float`, `double`, lub `decimal`|  
|[ushort](ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`|  
|[int](int.md)|`long`, `float`, `double`, lub `decimal`|  
|[uint](uint.md)|`long`, `ulong`, `float`, `double`, lub `decimal`|  
|[long](long.md)|`float`, `double`, lub `decimal`|  
|[char](char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub `decimal`|  
|[float](float.md)|`double`|  
|[ulong](ulong.md)|`float`, `double`, lub `decimal`|  
  
## <a name="remarks"></a>Uwagi  

- Wszelkie [typu całkowitego](integral-types-table.md) jest niejawnie konwertowany na dowolny [typu zmiennoprzecinkowego](floating-point-types-table.md).

- Dokładności, ale wartość nie może być utracone w konwersje z `int`, `uint`, `long`, lub `ulong` do `float` i `long` lub `ulong` do `double`.  
  
- Brak konwersji niejawnych do `char` typu.  
  
- Brak niejawnej konwersji między `float` i `double` typów i `decimal` typu.  
  
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
