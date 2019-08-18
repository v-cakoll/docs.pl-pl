---
title: Tabela typów wbudowanych — C# odwołanie
ms.custom: seodec18
description: Słowa kluczowe dla C# typów wbudowanych
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 61701cc38c38b5e7235fbadb6d2a86e0e66b09ac
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566359"
---
# <a name="built-in-types-table-c-reference"></a>Tabela typów wbudowanych (C# odwołanie)

W poniższej tabeli przedstawiono słowa kluczowe dla C# typów wbudowanych, które są aliasami wstępnie zdefiniowanych typów w <xref:System> przestrzeni nazw.  
  
|C#Wprowadź|Typ .NET|  
|--------------|-------------------------|  
|[bool](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](../builtin-types/floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](../builtin-types/floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](../builtin-types/floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](../builtin-types/integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](../builtin-types/integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](../builtin-types/integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](../builtin-types/integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](../builtin-types/integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](../builtin-types/integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Uwagi

Wszystkie typy w tabeli, z wyjątkiem `object` i `string`, są określane jako typy proste.  
  
Typy .NET i ich C# aliasy słów kluczowych są zamienne. Na przykład można zadeklarować zmienną całkowitą przy użyciu jednej z następujących deklaracji:  

```csharp
int x = 123;
System.Int32 y = 123;
```

Użyj operatora [typeof](../operators/type-testing-and-cast.md#typeof-operator) , aby uzyskać <xref:System.Type?displayProperty=nameWithType> wystąpienie, które reprezentuje określony typ:

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy wartości](value-types.md)
- [Typy odwołań](reference-types.md)
- [Tabela wartości domyślnych](default-values-table.md)
- [dynamic](dynamic.md)
