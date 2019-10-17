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
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="9a83b-102">Porady: konwertowanie tablicy typu Byte na liczbę całkowitą (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="9a83b-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>

<span data-ttu-id="9a83b-103">Ten przykład pokazuje, jak używać klasy <xref:System.BitConverter> do konwersji tablicy bajtów na [int](../../language-reference/builtin-types/integral-numeric-types.md) i z powrotem do tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="9a83b-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../language-reference/builtin-types/integral-numeric-types.md) and back to an array of bytes.</span></span> <span data-ttu-id="9a83b-104">Może być konieczne przekonwertowanie z bajtów na typ danych wbudowanych po odczytaniu bajtów z sieci, na przykład.</span><span class="sxs-lookup"><span data-stu-id="9a83b-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="9a83b-105">Oprócz metody [ToInt32 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) w przykładzie Poniższa tabela zawiera listę metod w klasie <xref:System.BitConverter>, które konwertują bajty (z tablicy bajtów) na inne typy wbudowane.</span><span class="sxs-lookup"><span data-stu-id="9a83b-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>

|<span data-ttu-id="9a83b-106">Zwrócony typ</span><span class="sxs-lookup"><span data-stu-id="9a83b-106">Type returned</span></span>|<span data-ttu-id="9a83b-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="9a83b-107">Method</span></span>|
|-------------------|------------|
|`bool`|<span data-ttu-id="9a83b-108">[ToBoolean (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="9a83b-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|
|`char`|<span data-ttu-id="9a83b-109">[ToChar — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="9a83b-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|
|`double`|<span data-ttu-id="9a83b-110">[ToDouble — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="9a83b-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|
|`short`|<span data-ttu-id="9a83b-111">[Toint16 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="9a83b-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|
|`int`|<span data-ttu-id="9a83b-112">[Toint32 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="9a83b-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|
|`long`|<span data-ttu-id="9a83b-113">[Toint64 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="9a83b-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|
|`float`|<span data-ttu-id="9a83b-114">[ToSingle — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="9a83b-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|
|`ushort`|<span data-ttu-id="9a83b-115">[Touint16 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="9a83b-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|
|`uint`|<span data-ttu-id="9a83b-116">[Touint32 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="9a83b-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|
|`ulong`|<span data-ttu-id="9a83b-117">[Touint64 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="9a83b-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|

## <a name="example"></a><span data-ttu-id="9a83b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a83b-118">Example</span></span>

<span data-ttu-id="9a83b-119">Ten przykład Inicjuje tablicę bajtów, odwraca tablicę, jeśli architektura komputera to little-endian (to znaczy, że najmniej znaczący bajt jest przechowywany jako pierwszy), a następnie wywołuje metodę [ToInt32 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) , aby skonwertować cztery bajty w Tablica do `int`.</span><span class="sxs-lookup"><span data-stu-id="9a83b-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="9a83b-120">Drugim argumentem [ToInt32 — (Byte @ no__t-1 @ no__t-2, Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) określa początkowy indeks tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="9a83b-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="9a83b-121">Dane wyjściowe mogą się różnić w zależności od endianess architektury komputera.</span><span class="sxs-lookup"><span data-stu-id="9a83b-121">The output may differ depending on the endianess of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#22)]

## <a name="example"></a><span data-ttu-id="9a83b-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a83b-122">Example</span></span>

<span data-ttu-id="9a83b-123">W tym przykładzie metoda <xref:System.BitConverter.GetBytes%28System.Int32%29> klasy <xref:System.BitConverter> jest wywoływana w celu konwersji `int` na tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="9a83b-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>

> [!NOTE]
> <span data-ttu-id="9a83b-124">Dane wyjściowe mogą się różnić w zależności od endianess architektury komputera.</span><span class="sxs-lookup"><span data-stu-id="9a83b-124">The output may differ depending on the endianess of your computer's architecture.</span></span>

[!code-csharp[csProgGuideTypes#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#23)]

## <a name="see-also"></a><span data-ttu-id="9a83b-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a83b-125">See also</span></span>

- <xref:System.BitConverter>
- <xref:System.BitConverter.IsLittleEndian>
- [<span data-ttu-id="9a83b-126">Typy</span><span class="sxs-lookup"><span data-stu-id="9a83b-126">Types</span></span>](./index.md)
