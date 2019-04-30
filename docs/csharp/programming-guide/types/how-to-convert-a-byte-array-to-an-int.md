---
title: 'Instrukcje: Konwertowanie tablicy typu byte na liczbę całkowitą — C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 3563b0ffd5360c575404ead81e0e847ccab46f0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678416"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="e81d4-102">Instrukcje: Konwertowanie tablicy typu byte na liczbę całkowitą (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="e81d4-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="e81d4-103">W tym przykładzie pokazano, jak używać <xref:System.BitConverter> klasy Konwertowanie tablicy bajtów, które mają [int](../../../csharp/language-reference/keywords/int.md) i z powrotem na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="e81d4-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../../csharp/language-reference/keywords/int.md) and back to an array of bytes.</span></span> <span data-ttu-id="e81d4-104">Być może trzeba przekonwertować z bajtów typu danych wbudowane po odczycie bajtów z sieci, na przykład.</span><span class="sxs-lookup"><span data-stu-id="e81d4-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="e81d4-105">Oprócz [toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) metody w przykładzie w poniższej tabeli wymieniono metody <xref:System.BitConverter> klasy, aby konwertować bajtów (z tablicy bajtów) do innych typów wbudowanych.</span><span class="sxs-lookup"><span data-stu-id="e81d4-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="e81d4-106">Typ zwracany</span><span class="sxs-lookup"><span data-stu-id="e81d4-106">Type returned</span></span>|<span data-ttu-id="e81d4-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="e81d4-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="e81d4-108">[ToBoolean (bajtów\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e81d4-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="e81d4-109">[Tochar — (bajtów\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e81d4-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="e81d4-110">[Todouble — (bajtów\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e81d4-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="e81d4-111">[Toint16 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e81d4-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="e81d4-112">[Toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e81d4-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="e81d4-113">[Toint64 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e81d4-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="e81d4-114">[Tosingle — (bajtów\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e81d4-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="e81d4-115">[Touint16 — (bajtów\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e81d4-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="e81d4-116">[Touint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e81d4-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="e81d4-117">[Touint64 — (bajtów\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="e81d4-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e81d4-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="e81d4-118">Example</span></span>  
 <span data-ttu-id="e81d4-119">W tym przykładzie Inicjuje tablicę bajtów, odwraca tablicy, jeśli architektura komputera jest little-endian (oznacza to, co najmniej znaczący bajt jest przechowywany najpierw), a następnie wywołuje [toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))metodę, aby przekonwertować czterech bajtów w tablicy do `int`.</span><span class="sxs-lookup"><span data-stu-id="e81d4-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="e81d4-120">Drugi argument [toint32 — (bajtów\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) Określa indeks początku tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="e81d4-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e81d4-121">Dane wyjściowe mogą się różnić w zależności od endianess architektury Twojego komputera.</span><span class="sxs-lookup"><span data-stu-id="e81d4-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]  
  
## <a name="example"></a><span data-ttu-id="e81d4-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="e81d4-122">Example</span></span>  
 <span data-ttu-id="e81d4-123">W tym przykładzie <xref:System.BitConverter.GetBytes%28System.Int32%29> metody <xref:System.BitConverter> klasy jest wywoływana w celu przekonwertowania `int` na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="e81d4-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e81d4-124">Dane wyjściowe mogą się różnić w zależności od endianess architektury Twojego komputera.</span><span class="sxs-lookup"><span data-stu-id="e81d4-124">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]  
  
## <a name="see-also"></a><span data-ttu-id="e81d4-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e81d4-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="e81d4-126">Typy</span><span class="sxs-lookup"><span data-stu-id="e81d4-126">Types</span></span>](../../../csharp/programming-guide/types/index.md)
