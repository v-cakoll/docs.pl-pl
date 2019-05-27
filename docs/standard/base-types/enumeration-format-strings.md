---
title: Wyliczanie ciągów formatujących — .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be2e5dbe0d02bcec8974a1e52c0dce107d3bf46b
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052852"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="f83a8-102">Wyliczanie ciągów formatujących</span><span class="sxs-lookup"><span data-stu-id="f83a8-102">Enumeration format strings</span></span>

<span data-ttu-id="f83a8-103">Możesz użyć <xref:System.Enum.ToString%2A?displayProperty=nameWithType> metodę, aby utworzyć nowy obiekt ciągu reprezentujący liczbowy, szesnastkowo lub wartości ciągu elementu członkowskiego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f83a8-103">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="f83a8-104">Ta metoda przyjmuje jeden wyliczenie formatowanie ciągów, aby określić wartości, które mają być zwracane.</span><span class="sxs-lookup"><span data-stu-id="f83a8-104">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="f83a8-105">W poniższych sekcjach wymieniono wyliczenie formatowanie ciągów i wartości, które zwracają.</span><span class="sxs-lookup"><span data-stu-id="f83a8-105">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="f83a8-106">Te specyfikatory formatu nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="f83a8-106">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="f83a8-107">G lub g</span><span class="sxs-lookup"><span data-stu-id="f83a8-107">G or g</span></span>

<span data-ttu-id="f83a8-108">Wyświetla wpis wyliczenia jako wartość ciągu, jeśli jest to możliwe, a w przeciwnym razie wyświetlana jest wartość całkowitą bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f83a8-108">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="f83a8-109">Jeśli nie zdefiniowano wyliczenia z **flagi** zestaw atrybutów, ciąg wartości każdego prawidłowego wpisu są łączone ze sobą, oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="f83a8-109">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="f83a8-110">Jeśli **flagi** atrybut nie jest ustawiony, nieprawidłową wartość jest wyświetlana jako wpisy numeryczne.</span><span class="sxs-lookup"><span data-stu-id="f83a8-110">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="f83a8-111">Poniższy przykład ilustruje specyfikator formatu G.</span><span class="sxs-lookup"><span data-stu-id="f83a8-111">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="f83a8-112">F lub f</span><span class="sxs-lookup"><span data-stu-id="f83a8-112">F or f</span></span>

<span data-ttu-id="f83a8-113">Wyświetla wpis wyliczenia jako wartość ciągu, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="f83a8-113">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="f83a8-114">Jeśli wartość, które mogą być całkowicie wyświetlane jako suma pozycji w wyliczeniu (nawet wtedy, gdy **flagi** atrybut nie jest obecny), wartości ciągu każdego wpisu prawidłowe są połączone ze sobą, oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="f83a8-114">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="f83a8-115">Jeśli wartość nie może całkowicie określana przez wpisy wyliczenie, wartość jest formatowana jako wartość całkowitą.</span><span class="sxs-lookup"><span data-stu-id="f83a8-115">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="f83a8-116">Poniższy przykład ilustruje specyfikator formatu F.</span><span class="sxs-lookup"><span data-stu-id="f83a8-116">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="f83a8-117">D lub d</span><span class="sxs-lookup"><span data-stu-id="f83a8-117">D or d</span></span>

<span data-ttu-id="f83a8-118">Wyświetla wpis wyliczenia jako wartość całkowitą w możliwie najkrótszym reprezentacji możliwe.</span><span class="sxs-lookup"><span data-stu-id="f83a8-118">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="f83a8-119">Poniższy przykład ilustruje specyfikator formatu D.</span><span class="sxs-lookup"><span data-stu-id="f83a8-119">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="f83a8-120">X lub x</span><span class="sxs-lookup"><span data-stu-id="f83a8-120">X or x</span></span>

<span data-ttu-id="f83a8-121">Wyświetla wpis wyliczenia jako wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="f83a8-121">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="f83a8-122">Wartość jest reprezentowana z zerami zgodnie z potrzebami upewnić się, że ciąg wynikowy ma dwa znaki dla każdego bajtu w typ wyliczeniowy [bazowy typ liczbowy](xref:System.Enum.GetUnderlyingType%2A).</span><span class="sxs-lookup"><span data-stu-id="f83a8-122">The value is represented with leading zeros as necessary, to ensure that the result string has two characters for each byte in the enumeration type's [underlying numeric type](xref:System.Enum.GetUnderlyingType%2A).</span></span> <span data-ttu-id="f83a8-123">Poniższy przykład ilustruje specyfikator formatu X.</span><span class="sxs-lookup"><span data-stu-id="f83a8-123">The following example illustrates the X format specifier.</span></span> <span data-ttu-id="f83a8-124">W tym przykładzie typ podstawowy elementu zarówno <xref:System.ConsoleColor> i <xref:System.IO.FileAttributes> jest <xref:System.Int32>, lub 32-bitowego (lub 4-bajtowych) całkowitą, która tworzy ciąg wyniku 8 znaków.</span><span class="sxs-lookup"><span data-stu-id="f83a8-124">In the example, the underlying type of both <xref:System.ConsoleColor> and <xref:System.IO.FileAttributes> is <xref:System.Int32>, or a 32-bit (or 4-byte) integer, which produces an 8-character result string.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]      
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="f83a8-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f83a8-125">Example</span></span>

<span data-ttu-id="f83a8-126">W poniższym przykładzie zdefiniowano wyliczenia zwanego `Colors` składający się z trzech wpisów: `Red`, `Blue`, i `Green`.</span><span class="sxs-lookup"><span data-stu-id="f83a8-126">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="f83a8-127">Po zdefiniowaniu wyliczenia wystąpienie może być zadeklarowana w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f83a8-127">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="f83a8-128">`Color.ToString(System.String)` Metoda następnie może służyć do wyświetlania wartości wyliczenia na różne sposoby, w zależności od specyfikatora formatu przekazane do niego.</span><span class="sxs-lookup"><span data-stu-id="f83a8-128">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="f83a8-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f83a8-129">See also</span></span>

- [<span data-ttu-id="f83a8-130">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="f83a8-130">Formatting Types</span></span>](formatting-types.md)
