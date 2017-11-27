---
title: "Tabela jawnych konwersji liczbowych (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7a366328035b205b93a50ff6d212a06576ee801
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Tabela jawnych konwersji liczbowych (odwołanie w C#)
Jawna konwersja liczbowa jest używana do konwertowania dowolnego typu liczbowego żadnego innego liczbowego typu, które nie są niejawna konwersja, korzystając z wyrażeniem rzutowania. W poniższej tabeli przedstawiono te konwersji.  
  
 Aby uzyskać więcej informacji na temat konwersji, zobacz [rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
|Z|Do|  
|----------|--------|  
|[sbyte —](../../../csharp/language-reference/keywords/sbyte.md)|`byte`, `ushort`, `uint`, `ulong`, lub`char`|  
|[bajtów](../../../csharp/language-reference/keywords/byte.md)|`Sbyte`lub`char`|  
|[krótki](../../../csharp/language-reference/keywords/short.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong`, lub`char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`, `byte`, `short`, lub`char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, lub`char`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, lub`char`|  
|[długa](../../../csharp/language-reference/keywords/long.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, lub`char`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, lub`char`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`, `byte`, lub`short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, lub`decimal`|  
|[podwójne](../../../csharp/language-reference/keywords/double.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, lub`decimal`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, lub`double`|  
  
## <a name="remarks"></a>Uwagi  
  
-   Jawna konwersja liczbowa może spowodować utratę dokładności lub wynik przerzucane wyjątków.  
  
-   Podczas konwertowania `decimal` wartości na typ całkowity, ta wartość jest zaokrąglana do zero do najbliższej wartości całkowitej. Jeśli wynikowej wartości całkowite jest spoza zakresu typu docelowego <xref:System.OverflowException> jest generowany.  
  
-   Podczas konwersji z `double` lub `float` wartości na typ całkowity, wartość zostanie obcięta. Jeśli całkowitą wartość wynikowa znajduje się poza zakresem wartości docelowej, wynik zależy od przepełnienie sprawdzanie kontekstu. W kontekście zaznaczone `OverflowException` jest zgłoszony w kontekście niezaznaczone, wynik jest wartością nieokreślonego typu docelowego.  
  
-   Podczas konwertowania `double` do `float`, `double` wartość jest zaokrąglana do najbliższego `float` wartość. Jeśli `double` wartość jest zbyt mała lub zbyt duży, aby zmieścić na typ docelowy zostanie zero lub nieskończoności.  
  
-   Podczas konwertowania `float` lub `double` do `decimal`, wartości źródłowej jest konwertowana na `decimal` reprezentacja i zaokrąglona do najbliższej liczby po przecinku 28, jeśli jest to wymagane. W zależności od wartości wartość źródła może wystąpić jeden z następujących wyników:  
  
    -   Jeśli wartość źródła jest za mały, aby mogły być reprezentowane jako `decimal`, wynik wynosi zero.  
  
    -   Jeśli wartość źródła jest wartością typu NaN (nieliczbową), nieskończoności, lub zbyt duży, może być reprezentowana jako `decimal`, `OverflowException` jest generowany.  
  
-   Podczas konwertowania `decimal` do `float` lub `double`, `decimal` wartość jest zaokrąglana do najbliższego `double` lub `float` wartość.  
  
 Aby uzyskać więcej informacji na jawnej konwersji Zobacz Explicit w specyfikacji języka C#. Aby uzyskać więcej informacji na temat sposobu dostępu spec, zobacz [specyfikacji języka C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [() — Operator](../../../csharp/language-reference/operators/invocation-operator.md)  
 [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
