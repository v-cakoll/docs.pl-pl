---
title: Tabela wartości domyślnych (odwołanie w C#)
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
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
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e249dd2f352fe6177f3afbfd089fc4dc9b1b7798
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
