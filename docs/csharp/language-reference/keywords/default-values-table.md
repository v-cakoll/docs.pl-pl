---
title: Tabela wartości domyślnych (odwołanie w C#)
description: Dowiedz się, jakie są wartości domyślne typy wartości zwracanych przez domyślnych konstruktorów.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 634a55304534b4269487f29be1fbb4930f51d8ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218793"
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
|[bool](bool.md)|`false`|
|[byte](byte.md)|0|
|[char](char.md)|'\0'|
|[decimal](decimal.md)|0M|
|[double](double.md)|0,0 D|
|[enum](enum.md)|Wartość utworzonego przez wyrażenie (E) 0, gdzie E to identyfikator wyliczenia.|
|[float](float.md)|0,0|
|[int](int.md)|0|
|[long](long.md)|0L|
|[sbyte](sbyte.md)|0|
|[short](short.md)|0|
|[struct](struct.md)|Wartość utworzonego przez ustawienie wszystkie pola typu wartość do wartości domyślnych i wszystkie pola typu odwołania do `null`.|
|[uint](uint.md)|0|
|[ulong](ulong.md)|0|
|[ushort](ushort.md)|0|

## <a name="see-also"></a>Zobacz także
 [Odwołanie w C#](../index.md)  
 [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
 [Tabela typów wartości](value-types-table.md)  
 [Typy wartości](value-types.md)  
 [Tabela typów wbudowanych](built-in-types-table.md)  
 [Tabele odwołań dla typów](reference-tables-for-types.md)
