---
title: 'Instrukcje: Konwertuj tablicę bajtów na Przewodnik C# programowania int'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: ffb00325bc04aad79d61558925546e0aa8544551
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921752"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Instrukcje: Konwertuj tablicę bajtów na liczbę całkowitą (C# Przewodnik programowania)
W tym przykładzie pokazano, jak użyć <xref:System.BitConverter> klasy do konwersji tablicy bajtów na [int](../../language-reference/builtin-types/integral-numeric-types.md) i z powrotem do tablicy bajtów. Może być konieczne przekonwertowanie z bajtów na typ danych wbudowanych po odczytaniu bajtów z sieci, na przykład. Oprócz metody [ToInt32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) w przykładzie Poniższa tabela zawiera listę metod w <xref:System.BitConverter> klasie, które konwertują bajty (z tablicy bajtów) na inne typy wbudowane.  
  
|Zwrócony typ|Metoda|  
|-------------------|------------|  
|`bool`|[ToBoolean (Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|  
|`char`|[ToChar — (Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|  
|`double`|[ToDouble — (Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|  
|`short`|[ToInt16 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|  
|`int`|[ToInt32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|  
|`long`|[ToInt64 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|  
|`float`|[ToSingle — (Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|  
|`ushort`|[ToUInt16 — (Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|  
|`uint`|[ToUInt32 — (Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|  
|`ulong`|[ToUInt64 — (Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|  
  
## <a name="example"></a>Przykład  
 Ten przykład Inicjuje tablicę bajtów, odwraca tablicę, jeśli architektura komputera jest w stanie little-endian (oznacza to, że najpierw jest przechowywany najmniej znaczący bajt), a następnie wywołuje metodę [ToInt32 — (\[Byte\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) do konwersji cztery bajty w tablicy do `int`. Drugi argument [ToInt32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) określa początkowy indeks tablicy bajtów.  
  
> [!NOTE]
> Dane wyjściowe mogą się różnić w zależności od endianess architektury komputera.  
  
 [!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.BitConverter.GetBytes%28System.Int32%29> Metoda <xref:System.BitConverter> klasy `int` jest wywoływana w celu przekonwertowania na tablicę bajtów.  
  
> [!NOTE]
> Dane wyjściowe mogą się różnić w zależności od endianess architektury komputera.  
  
 [!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Typy](./index.md)
