---
title: 'Instrukcje: konwertowanie tablicy bajtów na Przewodnik C# programowania w postaci liczby całkowitej'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 96507f03a3d64b96ef6059a92459bfc7fa854372
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395685"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Porady: konwertowanie tablicy typu Byte na liczbę całkowitą (Przewodnik programowania w języku C#)

Ten przykład pokazuje, jak używać klasy <xref:System.BitConverter> do konwersji tablicy bajtów na [int](../../language-reference/builtin-types/integral-numeric-types.md) i z powrotem do tablicy bajtów. Może być konieczne przekonwertowanie z bajtów na typ danych wbudowanych po odczytaniu bajtów z sieci, na przykład. Oprócz metody [ToInt32 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) w przykładzie Poniższa tabela zawiera listę metod w klasie <xref:System.BitConverter>, które konwertują bajty (z tablicy bajtów) na inne typy wbudowane.

|Zwrócony typ|Metoda|
|-------------------|------------|
|`bool`|[ToBoolean (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|
|`char`|[ToChar — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|
|`double`|[ToDouble — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|
|`short`|[Toint16 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|
|`int`|[Toint32 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|
|`long`|[Toint64 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|
|`float`|[ToSingle — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|
|`ushort`|[Touint16 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|
|`uint`|[Touint32 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|
|`ulong`|[Touint64 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|

## <a name="example"></a>Przykład

Ten przykład Inicjuje tablicę bajtów, odwraca tablicę, jeśli architektura komputera to little-endian (to znaczy, że najmniej znaczący bajt jest przechowywany jako pierwszy), a następnie wywołuje metodę [ToInt32 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) , aby skonwertować cztery bajty w Tablica do `int`. Drugim argumentem [ToInt32 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) określa początkowy indeks tablicy bajtów.

> [!NOTE]
> Dane wyjściowe mogą się różnić w zależności od endianess architektury komputera.

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a>Przykład

W tym przykładzie metoda <xref:System.BitConverter.GetBytes%28System.Int32%29> klasy <xref:System.BitConverter> jest wywoływana w celu konwersji `int` na tablicę bajtów.

> [!NOTE]
> Dane wyjściowe mogą się różnić w zależności od endianess architektury komputera.

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a>Zobacz także

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Typy](./index.md)
