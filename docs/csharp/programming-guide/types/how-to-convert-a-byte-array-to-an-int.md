---
title: Jak skonwertować tablicę bajtową na Przewodnik C# programowania w postaci liczby całkowitej
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 9f477649dba1b42d7a10d521c010977707daf3ec
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698758"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Jak skonwertować tablicę bajtową na liczbę całkowitą (C# Przewodnik programowania)

W tym przykładzie pokazano, jak za pomocą klasy <xref:System.BitConverter> skonwertować tablicę bajtów na [int](../../language-reference/builtin-types/integral-numeric-types.md) i z powrotem do tablicy bajtów. Może być konieczne przekonwertowanie z bajtów na typ danych wbudowanych po odczytaniu bajtów z sieci, na przykład. Oprócz metody [ToInt32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) w przykładzie Poniższa tabela zawiera listę metod w klasie <xref:System.BitConverter>, które konwertują bajty (z tablicy bajtów) na inne typy wbudowane.

|Zwrócony typ|Metoda|
|-------------------|------------|
|`bool`|[ToBoolean (bajt\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|
|`char`|[ToChar — (bajt\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|
|`double`|[ToDouble — (bajt\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|
|`short`|[Toint16 — (bajt\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|
|`int`|[Toint32 — (bajt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|
|`long`|[Toint64 — (bajt\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|
|`float`|[ToSingle — (bajt\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|
|`ushort`|[Touint16 — (bajt\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|
|`uint`|[Touint32 — (bajt\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|
|`ulong`|[Touint64 — (bajt\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|

## <a name="example"></a>Przykład

Ten przykład Inicjuje tablicę bajtów, odwraca tablicę, jeśli architektura komputera to little-endian (to znaczy, że najmniej znaczący bajt jest przechowywany jako pierwszy), a następnie wywołuje metodę [ToInt32 — (byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) , aby skonwertować cztery bajty w tablicy na `int`. Drugi argument [ToInt32 — (bajt\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) określa początkowy indeks tablicy bajtów.

> [!NOTE]
> Dane wyjściowe mogą się różnić w zależności od liczby bajtów architektury komputera.

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a>Przykład

W tym przykładzie metoda <xref:System.BitConverter.GetBytes%28System.Int32%29> klasy <xref:System.BitConverter> jest wywoływana w celu przekonwertowania `int` na tablicę bajtów.

> [!NOTE]
> Dane wyjściowe mogą się różnić w zależności od liczby bajtów architektury komputera.

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a>Zobacz także

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Typy](./index.md)
