---
title: 'Instrukcje: Konwertowanie tablicy typu byte na liczbę całkowitą — C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 82ed87bbcbc741695afc49069c413ae440bd147b
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423553"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Instrukcje: Konwertowanie tablicy typu byte na liczbę całkowitą (C# Programming Guide)
W tym przykładzie pokazano, jak używać <xref:System.BitConverter> klasy Konwertowanie tablicy bajtów, które mają [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) i z powrotem na tablicę bajtów. Być może trzeba przekonwertować z bajtów typu danych wbudowane po odczycie bajtów z sieci, na przykład. Oprócz [toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) metody w przykładzie w poniższej tabeli wymieniono metody <xref:System.BitConverter> klasy, aby konwertować bajtów (z tablicy bajtów) do innych typów wbudowanych.  
  
|Typ zwracany|Metoda|  
|-------------------|------------|  
|`bool`|[ToBoolean (bajtów\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|  
|`char`|[Tochar — (bajtów\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|  
|`double`|[Todouble — (bajtów\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|  
|`short`|[Toint16 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|  
|`int`|[Toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|  
|`long`|[Toint64 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|  
|`float`|[Tosingle — (bajtów\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|  
|`ushort`|[Touint16 — (bajtów\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|  
|`uint`|[Touint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|  
|`ulong`|[Touint64 — (bajtów\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie Inicjuje tablicę bajtów, odwraca tablicy, jeśli architektura komputera jest little-endian (oznacza to, co najmniej znaczący bajt jest przechowywany najpierw), a następnie wywołuje [toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))metodę, aby przekonwertować czterech bajtów w tablicy do `int`. Drugi argument [toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) Określa indeks początku tablicy bajtów.  
  
> [!NOTE]
>  Dane wyjściowe mogą się różnić w zależności od endianess architektury Twojego komputera.  
  
 [!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.BitConverter.GetBytes%28System.Int32%29> metody <xref:System.BitConverter> klasy jest wywoływana w celu przekonwertowania `int` na tablicę bajtów.  
  
> [!NOTE]
>  Dane wyjściowe mogą się różnić w zależności od endianess architektury Twojego komputera.  
  
 [!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [Typy](../../../csharp/programming-guide/types/index.md)
