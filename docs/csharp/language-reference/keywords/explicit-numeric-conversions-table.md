---
title: Tabela jawnych konwersji liczbowych (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 5ca052dea4ee4abc866d2b02055188b0707499d4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071924"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Tabela jawnych konwersji liczbowych (odwołanie w C#)
Jawna konwersja liczbowa jest używana do konwersji dowolnego typu liczbowego do dowolnego innego typu liczbowego, dla których nie ma żadnych niejawna konwersja za pomocą wyrażenia rzutowania. W poniższej tabeli przedstawiono takiej konwersji.  
  
 Aby uzyskać więcej informacji dotyczących konwersji, zobacz [rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
|Z|Zadanie|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`, `ushort`, `uint`, `ulong`, lub `char`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte` lub `char`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong`, lub `char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`, `byte`, `short`, lub `char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, lub `char`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, lub `char`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, lub `char`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, lub `char`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`, `byte`, lub `short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, lub `decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, lub `decimal`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, lub `double`|  
  
## <a name="remarks"></a>Uwagi  
  
-   Jawna konwersja liczbowa może spowodować utratę precyzji lub wynik zgłaszanie wyjątków.  
  
-   Podczas konwertowania `decimal` wartości na typ całkowity, ta wartość jest zaokrąglana w kierunku zera do najbliższej wartości całkowitej. Jeśli wynikową wartość całkowitą znajduje się poza zakresem typu docelowego <xref:System.OverflowException> zgłaszany.  
  
-   Podczas konwersji z `double` lub `float` wartości na typ całkowity, wartość zostanie obcięta. Jeśli całkowitą wartość wynikowa znajduje się poza zakresem wartości docelowej, wynik zależy od przepełnienia, sprawdzając kontekst. W kontekście sprawdzanym `OverflowException` jest zgłaszany, gdy w kontekście niesprawdzanym, wynik jest wartością nieokreślonego typu miejsca docelowego.  
  
-   Podczas konwertowania `double` do `float`, `double` wartość jest zaokrąglana do najbliższej `float` wartość. Jeśli `double` wartość jest zbyt mała lub zbyt duży, aby zmieścić w typ docelowy wynik będzie zero lub nieskończoności.  
  
-   Podczas konwertowania `float` lub `double` do `decimal`, wartość źródłowa jest konwertowany na `decimal` reprezentacji i zaokrąglony do najbliższej liczby po 28 miejsce dziesiętne, jeśli jest to wymagane. W zależności od wartości wartość źródła może wystąpić jeden z poniższych wyników:  
  
    -   Jeśli wartość źródłowa jest za mały, może być reprezentowana jako `decimal`, wynik staje się zerem.  
  
    -   Jeśli wartość źródłowa jest wartością typu NaN (nieliczbową), nieskończoność, lub zbyt duży, może być reprezentowana jako `decimal`, `OverflowException` zgłaszany.  
  
-   Podczas konwertowania `decimal` do `float` lub `double`, `decimal` wartość jest zaokrąglana do najbliższej `double` lub `float` wartość.  
  
 Aby uzyskać więcej informacji dotyczących konwersji jawnej Zobacz jawne w specyfikacji języka C#. Aby uzyskać więcej informacji na temat sposobu dostępu specyfikacje, zobacz [specyfikacji języka C#](../../../csharp/language-reference/language-specification/index.md).  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
- [(), operator](../../../csharp/language-reference/operators/invocation-operator.md)  
- [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Tabela niejawnych konwersji liczbowych](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
