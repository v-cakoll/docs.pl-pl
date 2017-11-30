---
title: "Porady: konwertowanie tablicy typu Byte na liczbę całkowitą (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee51cd94e961c7274286c812cb6900d26c6ce033
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="c5bdb-102">Porady: konwertowanie tablicy typu Byte na liczbę całkowitą (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c5bdb-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="c5bdb-103">W tym przykładzie przedstawiono sposób użycia <xref:System.BitConverter> klasy w celu przekonwertowania na tablicę bajtów do [int](../../../csharp/language-reference/keywords/int.md) i z powrotem na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="c5bdb-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../../csharp/language-reference/keywords/int.md) and back to an array of bytes.</span></span> <span data-ttu-id="c5bdb-104">Być może trzeba przekonwertować z bajtów z typem danych wbudowanych po przeczytaniu bajtów poza siecią, na przykład.</span><span class="sxs-lookup"><span data-stu-id="c5bdb-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="c5bdb-105">Oprócz [toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) metody w przykładzie w poniższej tabeli przedstawiono metody <xref:System.BitConverter> klasy, która przekonwertować bajtów (od tablicę bajtów) na inne typy wbudowane.</span><span class="sxs-lookup"><span data-stu-id="c5bdb-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="c5bdb-106">Typ zwracany</span><span class="sxs-lookup"><span data-stu-id="c5bdb-106">Type returned</span></span>|<span data-ttu-id="c5bdb-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="c5bdb-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="c5bdb-108">[ToBoolean (Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c5bdb-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="c5bdb-109">[Tochar — (Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c5bdb-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="c5bdb-110">[Todouble — (Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c5bdb-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="c5bdb-111">[Toint16 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c5bdb-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="c5bdb-112">[Toint32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c5bdb-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="c5bdb-113">[Toint64 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c5bdb-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="c5bdb-114">[Tosingle — (Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c5bdb-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="c5bdb-115">[Touint16 — (Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c5bdb-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="c5bdb-116">[Touint32 — (Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c5bdb-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="c5bdb-117">[Touint64 — (Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="c5bdb-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c5bdb-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5bdb-118">Example</span></span>  
 <span data-ttu-id="c5bdb-119">W tym przykładzie Inicjuje tablicę bajtów, odwraca tablica, jeśli architektura komputera jest little endian (to znaczy najmniej znaczący bajt jest przechowywana najpierw), a następnie wywołuje [toint32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))metodę, aby przekonwertować cztery bajty w tablicy, tak aby `int`.</span><span class="sxs-lookup"><span data-stu-id="c5bdb-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="c5bdb-120">Drugi argument [toint32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) Określa początkowy indeks tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="c5bdb-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5bdb-121">Dane wyjściowe mogą się różnić w zależności od endianess architektury Twojego komputera.</span><span class="sxs-lookup"><span data-stu-id="c5bdb-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c5bdb-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5bdb-122">Example</span></span>  
 <span data-ttu-id="c5bdb-123">W tym przykładzie <xref:System.BitConverter.GetBytes%28System.Int32%29> metody <xref:System.BitConverter> klasy jest wywoływana, aby przekonwertować `int` na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="c5bdb-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5bdb-124">Dane wyjściowe mogą się różnić w zależności od endianess architektury Twojego komputera.</span><span class="sxs-lookup"><span data-stu-id="c5bdb-124">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c5bdb-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5bdb-125">See Also</span></span>  
 <xref:System.BitConverter>  
 <xref:System.BitConverter.IsLittleEndian>  
 [<span data-ttu-id="c5bdb-126">Typy</span><span class="sxs-lookup"><span data-stu-id="c5bdb-126">Types</span></span>](../../../csharp/programming-guide/types/index.md)
