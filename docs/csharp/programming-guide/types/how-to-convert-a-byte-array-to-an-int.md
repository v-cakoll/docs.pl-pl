---
title: 'Porady: konwertowanie tablicy typu Byte na liczbę całkowitą (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 4e8c232a604837d32675229f7f91b8e329ac4b5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337876"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Porady: konwertowanie tablicy typu Byte na liczbę całkowitą (Przewodnik programowania w języku C#)
W tym przykładzie przedstawiono sposób użycia <xref:System.BitConverter> klasy w celu przekonwertowania na tablicę bajtów do [int](../../../csharp/language-reference/keywords/int.md) i z powrotem na tablicę bajtów. Być może trzeba przekonwertować z bajtów z typem danych wbudowanych po przeczytaniu bajtów poza siecią, na przykład. Oprócz [toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) metody w przykładzie w poniższej tabeli przedstawiono metody <xref:System.BitConverter> klasy, która przekonwertować bajtów (od tablicę bajtów) na inne typy wbudowane.  
  
|Typ zwracany|Metoda|  
|-------------------|------------|  
|`bool`|[ToBoolean (Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|  
|`char`|[Tochar — (Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|  
|`double`|[Todouble — (Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|  
|`short`|[Toint16 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|  
|`int`|[Toint32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|  
|`long`|[Toint64 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|  
|`float`|[Tosingle — (Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|  
|`ushort`|[Touint16 — (Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|  
|`uint`|[Touint32 — (Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|  
|`ulong`|[Touint64 — (Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie Inicjuje tablicę bajtów, odwraca tablica, jeśli architektura komputera jest little endian (to znaczy najmniej znaczący bajt jest przechowywana najpierw), a następnie wywołuje [toint32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))metodę, aby przekonwertować cztery bajty w tablicy, tak aby `int`. Drugi argument [toint32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) Określa początkowy indeks tablicy bajtów.  
  
> [!NOTE]
>  Dane wyjściowe mogą się różnić w zależności od endianess architektury Twojego komputera.  
  
 [!code-csharp[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.BitConverter.GetBytes%28System.Int32%29> metody <xref:System.BitConverter> klasy jest wywoływana, aby przekonwertować `int` na tablicę bajtów.  
  
> [!NOTE]
>  Dane wyjściowe mogą się różnić w zależności od endianess architektury Twojego komputera.  
  
 [!code-csharp[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.BitConverter>  
 <xref:System.BitConverter.IsLittleEndian>  
 [Typy](../../../csharp/programming-guide/types/index.md)
