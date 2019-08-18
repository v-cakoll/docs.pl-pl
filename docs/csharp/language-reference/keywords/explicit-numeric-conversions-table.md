---
title: Tabela jawnych konwersji liczbowych — C# odwołanie
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
ms.openlocfilehash: 4dee46d075ea3d45d53ac0f64b539231188cf867
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566321"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a>Tabela jawnych konwersji liczbowych (C# odwołanie)

W poniższej tabeli przedstawiono wstępnie zdefiniowane jawne konwersje między typami liczbowymi .NET, dla których nie istnieje niejawna [Konwersja](implicit-numeric-conversions-table.md).

|Z|Zadanie|  
|----------|--------|  
|[sbyte](../builtin-types/integral-numeric-types.md)|`byte`, `ushort`, `uint`, lub`ulong``char`|  
|[byte](../builtin-types/integral-numeric-types.md)|`sbyte` lub `char`|  
|[short](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `ushort`, `uint`, lub`ulong``char`|  
|[ushort](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`lub`char`|  
|[int](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort` ,,lub`uint` `ulong``char`|  
|[uint](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, lub`int``char`|  
|[long](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, ,,`ushort`,lub `int` `uint` `ulong``char`|  
|[ulong](../builtin-types/integral-numeric-types.md)|`sbyte`, `byte`, `short`, ,,`ushort`,lub `int` `uint` `long``char`|  
|[char](char.md)|`sbyte`, `byte`lub`short`|  
|[float](../builtin-types/floating-point-numeric-types.md)|`sbyte`, `byte` ,`short` ,,`long`, ,,`char`, lub `ulong` `ushort` `int` `uint``decimal`|  
|[double](../builtin-types/floating-point-numeric-types.md)|`sbyte`, `byte` `short` ,`uint`,,,, ,`ulong`, ,lub`char` `long` `ushort` `int` `float``decimal`|  
|[decimal](../builtin-types/floating-point-numeric-types.md)|`sbyte`, `byte` `short` ,`uint`,,,, ,`ulong`, ,lub`char` `long` `ushort` `int` `float``double`|  
  
## <a name="remarks"></a>Uwagi  
  
- Jawna konwersja liczbowa może spowodować utratę precyzji lub wynik zgłaszania wyjątku, zwykle jest <xref:System.OverflowException>.  

- W przypadku konwersji wartości typu całkowitego na inny typ całkowity wynik zależy od [kontekstu sprawdzania](checked-and-unchecked.md)przepełnienia. W kontekście zaznaczania konwersja powiedzie się, jeśli wartość źródłowa należy do zakresu typu docelowego. W przeciwnym razie jest zgłaszany. <xref:System.OverflowException> W kontekście niesprawdzonym konwersja zawsze kończy się powodzeniem i przechodzi w następujący sposób:

  - Jeśli typ źródła jest większy niż typ docelowy, wartość źródłowa zostanie obcięta przez odrzucenie jej najbardziej znaczących bitów. Następnie wynik jest traktowany jako wartość typu docelowego.

  - Jeśli typ źródła jest mniejszy niż typ docelowy, wartość źródłowa jest podwyższana lub równa zero, tak że jest to ten sam rozmiar, co typ docelowy. Jeśli typ źródła jest podpisany, jest używane rozszerzenie-znak. Jeśli typ źródła jest niepodpisany, jest używane rozszerzenie o wartości zero. Następnie wynik jest traktowany jako wartość typu docelowego.

  - Jeśli typ źródła ma taki sam rozmiar jak typ docelowy, wartość źródłowa jest traktowana jako wartość typu docelowego.
  
- Podczas konwersji `decimal` wartości na typ całkowity, ta wartość jest zaokrąglana do zera do najbliższej wartości całkowitej. Jeśli uzyskana wartość całkowita jest poza zakresem typu docelowego, <xref:System.OverflowException> zostanie zgłoszony.  
  
- W przypadku konwersji `double` lub `float` wartości na typ całkowity ta wartość jest zaokrąglana do zera do najbliższej wartości całkowitej. Jeśli wynikowa wartość całkowita znajduje się poza zakresem typu docelowego, wynik zależy od [kontekstu sprawdzania](checked-and-unchecked.md)przepełnienia. W kontekście <xref:System.OverflowException> , który jest zgłaszany, a w kontekście niesprawdzonym, wynik jest nieokreśloną wartością typu docelowego.  
  
- Podczas konwersji `double` na `float` wartość`double` jest zaokrąglana do najbliższej `float` wartości. `double` Jeśli wartość jest za mała lub zbyt duża, aby zmieścić ją w typie docelowym, wynik będzie wynosić zero lub nieskończoność.  
  
- Podczas konwertowania `float` `decimal` lub `double` do`decimal`, wartość źródłowa jest konwertowana na reprezentację i zaokrąglana do najbliższej liczby po 28 miejscach dziesiętnych, jeśli jest to wymagane. W zależności od wartości źródłowej może wystąpić jeden z następujących wyników:  

  - Jeśli wartość źródłowa jest zbyt mała `decimal`, aby była reprezentowana jako, wynik zmieni się na zero.  

  - Jeśli wartością źródłową jest NaN (nie liczba), nieskończoność lub zbyt duża do reprezentowania jako `decimal` <xref:System.OverflowException> , jest generowany.  
  
- Podczas `decimal` konwertowania `float` `double` na `float` lub`double` ,`decimal` wartość jest zaokrąglana do najbliższej lub wartości.  
  
 Aby uzyskać więcej informacji na temat konwersji jawnych, zobacz sekcję [Konwersje jawne](~/_csharplang/spec/conversions.md#explicit-conversions) w [ C# specyfikacji języka](../language-specification/index.md).
  
## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Rzutowanie i konwersje typów](../../programming-guide/types/casting-and-type-conversions.md)
- [() — operator](../operators/type-testing-and-cast.md#cast-operator-)
- [Typy całkowite](../builtin-types/integral-numeric-types.md)
- [Tabela typów zmiennoprzecinkowych](../builtin-types/floating-point-numeric-types.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
- [Tabela niejawnych konwersji liczbowych](implicit-numeric-conversions-table.md)
