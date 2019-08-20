---
title: 'Instrukcje: Konwertuj tablicę bajtów na Przewodnik C# programowania int'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
ms.openlocfilehash: 6d272a1a20cc5eb35edc7f6d971cbffbd9bfdbae
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588415"
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="2150d-102">Instrukcje: Konwertuj tablicę bajtów na liczbę całkowitą (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="2150d-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="2150d-103">W tym przykładzie pokazano, jak użyć <xref:System.BitConverter> klasy do konwersji tablicy bajtów na [int](../../language-reference/builtin-types/integral-numeric-types.md) i z powrotem do tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="2150d-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="2150d-104">Może być konieczne przekonwertowanie z bajtów na typ danych wbudowanych po odczytaniu bajtów z sieci, na przykład.</span><span class="sxs-lookup"><span data-stu-id="2150d-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="2150d-105">Oprócz metody [ToInt32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) w przykładzie Poniższa tabela zawiera listę metod w <xref:System.BitConverter> klasie, które konwertują bajty (z tablicy bajtów) na inne typy wbudowane.</span><span class="sxs-lookup"><span data-stu-id="2150d-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="2150d-106">Zwrócony typ</span><span class="sxs-lookup"><span data-stu-id="2150d-106">Type returned</span></span>|<span data-ttu-id="2150d-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="2150d-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="2150d-108">[ToBoolean (Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="2150d-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="2150d-109">[ToChar — (Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="2150d-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="2150d-110">[ToDouble — (Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="2150d-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="2150d-111">[ToInt16 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="2150d-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="2150d-112">[ToInt32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="2150d-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="2150d-113">[ToInt64 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="2150d-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="2150d-114">[ToSingle — (Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="2150d-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="2150d-115">[ToUInt16 — (Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="2150d-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="2150d-116">[ToUInt32 — (Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="2150d-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="2150d-117">[ToUInt64 — (Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="2150d-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2150d-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2150d-118">Example</span></span>  
 <span data-ttu-id="2150d-119">Ten przykład Inicjuje tablicę bajtów, odwraca tablicę, jeśli architektura komputera jest w stanie little-endian (oznacza to, że najpierw jest przechowywany najmniej znaczący bajt), a następnie wywołuje metodę [ToInt32 — (\[Byte\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) do konwersji cztery bajty w tablicy do `int`.</span><span class="sxs-lookup"><span data-stu-id="2150d-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="2150d-120">Drugi argument [ToInt32 — (Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) określa początkowy indeks tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="2150d-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2150d-121">Dane wyjściowe mogą się różnić w zależności od endianess architektury komputera.</span><span class="sxs-lookup"><span data-stu-id="2150d-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]  
  
## <a name="example"></a><span data-ttu-id="2150d-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="2150d-122">Example</span></span>  
 <span data-ttu-id="2150d-123">W tym przykładzie <xref:System.BitConverter.GetBytes%28System.Int32%29> Metoda <xref:System.BitConverter> klasy `int` jest wywoływana w celu przekonwertowania na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="2150d-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2150d-124">Dane wyjściowe mogą się różnić w zależności od endianess architektury komputera.</span><span class="sxs-lookup"><span data-stu-id="2150d-124">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]  
  
## <a name="see-also"></a><span data-ttu-id="2150d-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2150d-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="2150d-126">Typy</span><span class="sxs-lookup"><span data-stu-id="2150d-126">Types</span></span>](./index.md)
