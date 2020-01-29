---
title: Tabela typów wbudowanych — C# odwołanie
description: Słowa kluczowe dla C# typów wbudowanych
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: f26da848d58426472d2c2ab755ecadfd267b096a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734484"
---
# <a name="built-in-types-table-c-reference"></a>Tabela typów wbudowanych (C# odwołanie)

W poniższej tabeli przedstawiono słowa kluczowe dla C# typów wbudowanych, które są aliasami wstępnie zdefiniowanych typów w przestrzeni nazw <xref:System>:

|C#Wprowadź|Typ .NET|  
|--------------|-------------------------|  
|[bool](../builtin-types/bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](../builtin-types/char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](../builtin-types/floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](../builtin-types/floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](../builtin-types/floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](../builtin-types/integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](../builtin-types/integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](../builtin-types/integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](../builtin-types/integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](../builtin-types/reference-types.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](../builtin-types/integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](../builtin-types/integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](../builtin-types/reference-types.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Uwagi

Wszystkie typy w tabeli, z wyjątkiem `object` i `string`, są określane jako typy proste.

Typy .NET i ich C# aliasy słów kluczowych są zamienne. Na przykład można zadeklarować zmienną całkowitą przy użyciu jednej z następujących deklaracji:

```csharp
int x = 123;
System.Int32 y = 123;
```

Użyj operatora [typeof](../operators/type-testing-and-cast.md#typeof-operator) , aby pobrać wystąpienie <xref:System.Type?displayProperty=nameWithType> reprezentujące określony typ:

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

- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Typy wartości](../builtin-types/value-types.md)
- [Typy odwołań](reference-types.md)
- [Wartości domyślne C# typów](../builtin-types/default-values.md)
- [dynamic](../builtin-types/reference-types.md#the-dynamic-type)
