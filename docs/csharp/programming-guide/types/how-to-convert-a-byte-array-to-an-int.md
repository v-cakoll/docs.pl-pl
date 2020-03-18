---
title: Jak przekonwertować tablicę bajtów na int - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 9f477649dba1b42d7a10d521c010977707daf3ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698758"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Jak przekonwertować tablicę bajtów na int (Przewodnik programowania C#)

W tym przykładzie pokazano, jak użyć <xref:System.BitConverter> klasy do konwersji tablicy bajtów do [int](../../language-reference/builtin-types/integral-numeric-types.md) i z powrotem do tablicy bajtów. Może być trzeba przekonwertować z bajtów na wbudowany typ danych po przeczytaniu bajtów poza siecią, na przykład. Oprócz metody [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) w przykładzie w poniższej tabeli <xref:System.BitConverter> wymieniono metody w klasie, które konwertują bajty (z tablicy bajtów) na inne wbudowane typy.

|Tekst zwrócony|Metoda|
|-------------------|------------|
|`bool`|[ToBoolean(Bajt\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|
|`char`|[ToChar(Bajt\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|
|`double`|[ToDouble(Bajt\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|
|`short`|[ToInt16(Bajt\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|
|`int`|[ToInt32(Bajt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|
|`long`|[ToInt64(Bajt\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|
|`float`|[ToSingle(Bajt\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|
|`ushort`|[ToUInt16(Bajt\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|
|`uint`|[ToUInt32(Bajt\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|
|`ulong`|[ToUInt64(Bajt\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|

## <a name="example"></a>Przykład

W tym przykładzie inicjuje tablicę bajtów, odwraca tablicy, jeśli architektura komputera jest little-endian (to znaczy najmniej znaczący bajt jest przechowywany pierwszy), a następnie wywołuje [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) metoda do konwersji czterech bajtów w tablicy do . `int` Drugi argument [do ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) określa indeks początkowy tablicy bajtów.

> [!NOTE]
> Dane wyjściowe mogą się różnić w zależności od endianness architektury komputera.

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a>Przykład

W tym przykładzie <xref:System.BitConverter.GetBytes%28System.Int32%29> metoda <xref:System.BitConverter> klasy jest wywoływana `int` do konwersji do tablicy bajtów.

> [!NOTE]
> Dane wyjściowe mogą się różnić w zależności od endianness architektury komputera.

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a>Zobacz też

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Typy](./index.md)
