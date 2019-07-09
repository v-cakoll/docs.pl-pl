---
title: Tabela jawnych konwersji liczbowych - C# odwołania
ms.custom: seodec18
ms.date: 09/06/2018
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: d1533872850a953a38800aaeac85b9e6e565d374
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661371"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Tabela jawnych konwersji liczbowych (odwołanie w C#)

W poniższej tabeli przedstawiono wstępnie zdefiniowanych jawne konwersje między typów liczbowych .NET, na których działa nie [niejawna konwersja](implicit-numeric-conversions-table.md).

|Z|Zadanie|  
|----------|--------|  
|[sbyte](../builtin-types/integral-numeric-types.md)|`byte`, `ushort`, `uint`, `ulong`, lub `char`|  
|[byte](../builtin-types/integral-numeric-types.md)|`sbyte` lub `char`|  
|[short](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong`, lub `char`|  
|[ushort](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, lub `char`|  
|[int](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, lub `char`|  
|[uint](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, lub `char`|  
|[long](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, lub `char`|  
|[ulong](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, lub `char`|  
|[char](char.md)|`sbyte`, `byte`, lub `short`|  
|[float](../builtin-types/floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, lub `decimal`|  
|[double](../builtin-types/floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, lub `decimal`|  
|[decimal](../builtin-types/floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, lub `double`|  
  
## <a name="remarks"></a>Uwagi  
  
- Jawna konwersja liczbowa może spowodować utratę precyzji lub wynik w zostanie zgłoszony wyjątek, zwykle <xref:System.OverflowException>.  

- Podczas konwertowania wartości typu całkowitego innego typu całkowitego, wynik zależy od przeciążenia [sprawdzanie kontekstu](checked-and-unchecked.md). W kontekście sprawdzanym konwersja powiedzie się, gdy wartość źródła znajduje się w zakresie typu miejsca docelowego. W przeciwnym razie <xref:System.OverflowException> zgłaszany. W kontekście niesprawdzanym konwersji zawsze powiedzie się i będzie kontynuowane w następujący sposób:

  - Jeśli typ źródła jest większy niż typ docelowy, a następnie wartość źródłowa zostanie obcięta przez odrzucenie jego "dodatkowe" najbardziej znaczące bity. Wynik jest traktowane jako wartość typu miejsca docelowego.

  - Jeśli typ źródła jest mniejszy niż typ docelowy, następnie wartość źródłowa jest rozszerzona o znak lub rozszerzone zero tak, aby jest taki sam rozmiar jak typ docelowy. Rozszerzenia znaku jest używana, jeśli typ źródła jest podpisany; rozszerzenie zero jest używana, jeśli typ źródła jest niepodpisany. Wynik jest traktowane jako wartość typu miejsca docelowego.

  - Jeśli typ źródła jest taki sam rozmiar jak typ docelowy, wartość źródłowa jest traktowany jako wartość typu miejsca docelowego.
  
- Podczas konwertowania `decimal` wartości na typ całkowity, ta wartość jest zaokrąglana w kierunku zera do najbliższej wartości całkowitej. Jeśli wynikową wartość całkowitą znajduje się poza zakresem typu docelowego <xref:System.OverflowException> zgłaszany.  
  
- Podczas konwertowania `double` lub `float` wartości na typ całkowity, ta wartość jest zaokrąglana w kierunku zera do najbliższej wartości całkowitej. Jeśli całkowitą wartość wynikowa znajduje się poza zakresem typu miejsca docelowego, wynik zależy od przeciążenia [sprawdzanie kontekstu](checked-and-unchecked.md). W kontekście sprawdzanym <xref:System.OverflowException> jest zgłaszany, gdy w kontekście niesprawdzanym, wynik jest wartością nieokreślonego typu miejsca docelowego.  
  
- Podczas konwertowania `double` do `float`, `double` wartość jest zaokrąglana do najbliższej `float` wartość. Jeśli `double` wartość jest zbyt mała lub zbyt duży, aby zmieścić w typ docelowy wynik będzie zero lub nieskończoności.  
  
- Podczas konwertowania `float` lub `double` do `decimal`, wartość źródłowa jest konwertowany na `decimal` reprezentacji i zaokrąglony do najbliższej liczby po 28 miejsce dziesiętne, jeśli jest to wymagane. W zależności od wartości wartość źródła może wystąpić jeden z poniższych wyników:  

  - Jeśli wartość źródłowa jest za mały, może być reprezentowana jako `decimal`, wynik staje się zerem.  

  - Jeśli wartość źródłowa jest wartością typu NaN (nieliczbową), nieskończoność, lub zbyt duży, może być reprezentowana jako `decimal`, <xref:System.OverflowException> zgłaszany.  
  
- Podczas konwertowania `decimal` do `float` lub `double`, `decimal` wartość jest zaokrąglana do najbliższej `double` lub `float` wartość.  
  
 Aby uzyskać więcej informacji dotyczących jawnych konwersji, zobacz [jawne konwersje](~/_csharplang/spec/conversions.md#explicit-conversions) części [specyfikacji języka C#](../language-specification/index.md).
  
## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Konwersje rzutowania i typ](../../programming-guide/types/casting-and-type-conversions.md)
- [operator)](../operators/type-testing-and-conversion-operators.md#cast-operator-)
- [Typy całkowite](../builtin-types/integral-numeric-types.md)
- [Tabela typów zmiennoprzecinkowych](../builtin-types/floating-point-numeric-types.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](implicit-numeric-conversions-table.md)
