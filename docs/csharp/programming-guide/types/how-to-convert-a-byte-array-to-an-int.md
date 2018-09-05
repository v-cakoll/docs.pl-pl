---
title: 'Porady: konwertowanie tablicy typu Byte na liczbę całkowitą (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 0da6cbc6967f5e495bacfb9e032a403b4a39791b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542505"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="8540c-102">Porady: konwertowanie tablicy typu Byte na liczbę całkowitą (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="8540c-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="8540c-103">W tym przykładzie pokazano, jak używać <xref:System.BitConverter> klasy Konwertowanie tablicy bajtów, które mają [int](../../../csharp/language-reference/keywords/int.md) i z powrotem na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="8540c-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../../csharp/language-reference/keywords/int.md) and back to an array of bytes.</span></span> <span data-ttu-id="8540c-104">Być może trzeba przekonwertować z bajtów typu danych wbudowane po odczycie bajtów z sieci, na przykład.</span><span class="sxs-lookup"><span data-stu-id="8540c-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="8540c-105">Oprócz [toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) metody w przykładzie w poniższej tabeli wymieniono metody <xref:System.BitConverter> klasy, aby konwertować bajtów (z tablicy bajtów) do innych typów wbudowanych.</span><span class="sxs-lookup"><span data-stu-id="8540c-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="8540c-106">Typ zwracany</span><span class="sxs-lookup"><span data-stu-id="8540c-106">Type returned</span></span>|<span data-ttu-id="8540c-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="8540c-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="8540c-108">[ToBoolean (bajtów\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8540c-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="8540c-109">[Tochar — (bajtów\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8540c-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="8540c-110">[Todouble — (bajtów\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8540c-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="8540c-111">[Toint16 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8540c-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="8540c-112">[Toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8540c-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="8540c-113">[Toint64 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8540c-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="8540c-114">[Tosingle — (bajtów\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8540c-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="8540c-115">[Touint16 — (bajtów\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8540c-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="8540c-116">[Touint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8540c-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="8540c-117">[Touint64 — (bajtów\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8540c-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8540c-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="8540c-118">Example</span></span>  
 <span data-ttu-id="8540c-119">W tym przykładzie Inicjuje tablicę bajtów, odwraca tablicy, jeśli architektura komputera jest little-endian (oznacza to, co najmniej znaczący bajt jest przechowywany najpierw), a następnie wywołuje [toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))metodę, aby przekonwertować czterech bajtów w tablicy do `int`.</span><span class="sxs-lookup"><span data-stu-id="8540c-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="8540c-120">Drugi argument [toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) Określa indeks początku tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="8540c-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8540c-121">Dane wyjściowe mogą się różnić w zależności od endianess architektury Twojego komputera.</span><span class="sxs-lookup"><span data-stu-id="8540c-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8540c-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="8540c-122">Example</span></span>  
 <span data-ttu-id="8540c-123">W tym przykładzie <xref:System.BitConverter.GetBytes%28System.Int32%29> metody <xref:System.BitConverter> klasy jest wywoływana w celu przekonwertowania `int` na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="8540c-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8540c-124">Dane wyjściowe mogą się różnić w zależności od endianess architektury Twojego komputera.</span><span class="sxs-lookup"><span data-stu-id="8540c-124">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8540c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8540c-125">See Also</span></span>

- <xref:System.BitConverter>  
- <xref:System.BitConverter.IsLittleEndian>  
- [<span data-ttu-id="8540c-126">Typy</span><span class="sxs-lookup"><span data-stu-id="8540c-126">Types</span></span>](../../../csharp/programming-guide/types/index.md)
