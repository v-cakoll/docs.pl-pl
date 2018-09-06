---
title: Tabela typów całkowitych (odwołanie w C#)
description: Omówienie wbudowanego języka C# typy całkowite
ms.date: 08/20/2018
helpviewer_keywords:
- integral types, C#
- Visual C#, integral types
- types [C#], integral types
- ranges of integral types [C#]
ms.assetid: 62e86126-46ff-40b0-9028-e61d7558268c
ms.openlocfilehash: 4ac16d185a52cdb03fcb22f57ebf7506f2fb2745
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890668"
---
# <a name="integral-types-table-c-reference"></a>Tabela typów całkowitych (odwołanie w C#)

W poniższej tabeli przedstawiono rozmiary i zakresy typów całkowitych, które stanowią podzbiór typów prostych.  
  
|Typ|Zakres|Rozmiar|  
|----------|-----------|----------|  
|[sbyte](sbyte.md)|-128 do 127 znaków.|8-bitową liczbę całkowitą ze znakiem|  
|[byte](byte.md)|od 0 do 255|Liczba całkowita bez znaku 8-bitowa|  
|[char](char.md)|U + 0000 do U + ffff|Znak 16-bitowych Unicode|  
|[short](short.md)|-32768 do 32767.|16-bitową liczbę całkowitą ze znakiem|  
|[ushort](ushort.md)|0 do 65 535.|Liczba całkowita bez znaku 16-bitowych|  
|[int](int.md)|-2 147 483 2 147 483 648 do 647|32-bitowa liczba całkowita ze znakiem|  
|[uint](uint.md)|4 294 967 0 Aby 295|Liczba całkowita bez znaku 32-bitowy|  
|[long](long.md)|-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807|64-bitowa liczba całkowita ze znakiem|  
|[ulong](ulong.md)|0 — 18,446,744,073,709,551,615|Liczba całkowita bez znaku 64-bitowych|  

## <a name="remarks"></a>Uwagi
  
Jeśli wartości w postaci literału typu integer przekracza <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, błąd kompilatora [CS1021](../../misc/cs1021.md) występuje.

Użyj <xref:System.Numerics.BigInteger?displayProperty=nameWithType> klasy do reprezentowania dowolnie dużą całkowita.
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Tabele odwołań dla typów](reference-tables-for-types.md)
- [Tabela typów zmiennoprzecinkowych](floating-point-types-table.md)
- [Tabela wartości domyślnych](default-values-table.md)
- [Formatowanie tabeli wyników liczbowych](formatting-numeric-results-table.md)
- [Tabela typów wbudowanych](built-in-types-table.md)
