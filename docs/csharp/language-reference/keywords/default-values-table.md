---
title: "Tabela wartości domyślnych (odwołanie w C#)"
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.assetid: 4af2c1df-9e3a-48c1-83ac-b192986fc5bc
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d034c1daf495c50e299fec4c5bf399652dad08ce
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2017
---
# <a name="default-values-table-c-reference"></a>Tabela wartości domyślnych (odwołanie w C#)
W poniższej tabeli przedstawiono wartości domyślne typy wartości zwracanych przez domyślnych konstruktorów. Konstruktory domyślne są wywoływane przy użyciu `new` operatora w następujący sposób:

```csharp
int myInt = new int();
```

Powyższych instrukcji ma ten sam efekt co następująca instrukcja:

```csharp
int myInt = 0;
```

Należy pamiętać, że przy użyciu niezainicjowanych zmiennych w języku C# nie jest dozwolone.

|Typ wartości|Wartość domyślna|
|----------------|-------------------|
|[wartość logiczna](../../../csharp/language-reference/keywords/bool.md)|`false`|
|[bajtów](../../../csharp/language-reference/keywords/byte.md)|0|
|[char](../../../csharp/language-reference/keywords/char.md)|'\0'|
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|0M|
|[podwójne](../../../csharp/language-reference/keywords/double.md)|0,0 D|
|[wyliczenia](../../../csharp/language-reference/keywords/enum.md)|Wartość utworzonego przez wyrażenie (E) 0, gdzie E to identyfikator wyliczenia.|
|[float](../../../csharp/language-reference/keywords/float.md)|0,0|
|[int](../../../csharp/language-reference/keywords/int.md)|0|
|[długa](../../../csharp/language-reference/keywords/long.md)|0L|
|[sbyte —](../../../csharp/language-reference/keywords/sbyte.md)|0|
|[krótki](../../../csharp/language-reference/keywords/short.md)|0|
|[— Struktura](../../../csharp/language-reference/keywords/struct.md)|Wartość utworzonego przez ustawienie wszystkie pola typu wartość do wartości domyślnych i wszystkie pola typu odwołania do `null`.|
|[uint](../../../csharp/language-reference/keywords/uint.md)|0|
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|0|
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|0|

## <a name="see-also"></a>Zobacz także
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Tabela typów wartości](../../../csharp/language-reference/keywords/value-types-table.md)  
 [Typy wartości](../../../csharp/language-reference/keywords/value-types.md)  
 [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabele odwołań dla typów](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
