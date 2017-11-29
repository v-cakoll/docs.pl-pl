---
title: "Tabela niejawnych konwersji liczbowych (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6b1705dca357fd2a155fc1ea9c7fe0f65bad8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-numeric-conversions-table-c-reference"></a>Tabela niejawnych konwersji liczbowych (odwołanie w C#)
W poniższej tabeli przedstawiono wstępnie zdefiniowane niejawne konwersje liczbowe. Niejawne konwersje może wystąpić w wielu sytuacjach, w tym instrukcje metody wywoływania i przypisanie.  
  
|Z|Do|  
|----------|--------|  
|[sbyte —](../../../csharp/language-reference/keywords/sbyte.md)|`short`, `int`, `long`, `float`, `double`, lub`decimal`|  
|[bajtów](../../../csharp/language-reference/keywords/byte.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub`decimal`|  
|[krótki](../../../csharp/language-reference/keywords/short.md)|`int`, `long`, `float`, `double`, lub`decimal`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`int`, `uint`, `long`, `ulong`, `float`, `double`, lub`decimal`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`long`, `float`, `double`, lub`decimal`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`long`, `ulong`, `float`, `double`, lub`decimal`|  
|[długa](../../../csharp/language-reference/keywords/long.md)|`float`, `double`, lub`decimal`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, lub`decimal`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`float`, `double`, lub`decimal`|  
  
## <a name="remarks"></a>Uwagi  
  
-   Dokładności, ale nie wielkości mogą zostać utracone podczas konwersji z `int`, `uint`, `long`, lub `ulong` do `float` i z `long` lub `ulong` do `double`.  
  
-   Brak niejawnej konwersji do `char` typu.  
  
-   Brak niejawnej konwersji między typami liczb zmiennoprzecinkowych i `decimal` typu.  
  
-   Wyrażenie stałe typu `int` może zostać przekonwertowany na `sbyte`, `byte`, `short`, `ushort`, `uint`, lub `ulong`, jeśli wartość wyrażenia stałej jest spoza zakresu docelowego Typ.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela jawnych konwersji liczbowych](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
