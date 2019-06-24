---
title: Tabela typów wbudowanych - C# odwołania
ms.custom: seodec18
description: Słowa kluczowe dla typy wbudowane C#
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: d93176b850d84753106accef3bcaedab38f4ddc7
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306797"
---
# <a name="built-in-types-table-c-reference"></a>Tabela typów wbudowanych (odwołanie w C#)

W poniższej tabeli przedstawiono typy wbudowane C#, które są aliasy wstępnie zdefiniowanych typów słowa kluczowe w <xref:System> przestrzeni nazw.  
  
|Typ C#|Typ architektury .NET|  
|--------------|-------------------------|  
|[bool](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Uwagi

Wszystkie typy w tabeli, z wyjątkiem `object` i `string`, są nazywane typów prostych.  
  
Słowa kluczowe typu C# i ich aliasy są wymienne. Na przykład można zadeklarować zmienną całkowitoliczbową przy użyciu jednej z następujących deklaracje:  

```csharp
int x = 123;
System.Int32 y = 123;
```

Użyj [typeof](../operators/type-testing-and-conversion-operators.md#typeof-operator) operatorem w celu uzyskania <xref:System.Type?displayProperty=nameWithType> wystąpienia, który reprezentuje określony typ:

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
