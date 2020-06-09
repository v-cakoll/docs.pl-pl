---
title: Wyliczanie ciągów formatujących
description: Utwórz ciągi formatujące Wyliczenie przy użyciu metody enum. ToString w programie .NET. Formatowanie wartości liczbowych, szesnastkowych lub ciągów elementów członkowskich wyliczenia.
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
ms.openlocfilehash: 825357cf4a56132dae0870972d316eff89b0c94f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583430"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="d55ba-104">Wyliczanie ciągów formatujących</span><span class="sxs-lookup"><span data-stu-id="d55ba-104">Enumeration format strings</span></span>

<span data-ttu-id="d55ba-105">Możesz użyć metody, <xref:System.Enum.ToString%2A?displayProperty=nameWithType> Aby utworzyć nowy obiekt ciągu, który reprezentuje wartość liczbową, szesnastkową lub ciąg elementu członkowskiego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d55ba-105">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="d55ba-106">Ta metoda przyjmuje jeden z ciągów formatowania wyliczenia, aby określić wartość, która ma zostać zwrócona.</span><span class="sxs-lookup"><span data-stu-id="d55ba-106">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="d55ba-107">W poniższych sekcjach wymieniono ciągi formatowania wyliczenia i zwracane przez nie wartości.</span><span class="sxs-lookup"><span data-stu-id="d55ba-107">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="d55ba-108">W tych specyfikatorach formatu nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="d55ba-108">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="d55ba-109">G lub g</span><span class="sxs-lookup"><span data-stu-id="d55ba-109">G or g</span></span>

<span data-ttu-id="d55ba-110">Wyświetla wpis wyliczenia jako wartość ciągu, jeśli jest to możliwe, i w przeciwnym razie wyświetla wartość całkowitą bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d55ba-110">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="d55ba-111">Jeśli Wyliczenie jest zdefiniowane przy użyciu ustawionych atrybutów **flag** , wartości ciągów każdego poprawnego wpisu są łączone razem, oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="d55ba-111">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="d55ba-112">Jeśli atrybut **flags** nie jest ustawiony, nieprawidłowa wartość jest wyświetlana jako wpis liczbowy.</span><span class="sxs-lookup"><span data-stu-id="d55ba-112">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="d55ba-113">Poniższy przykład ilustruje specyfikator formatu G.</span><span class="sxs-lookup"><span data-stu-id="d55ba-113">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="d55ba-114">F lub f</span><span class="sxs-lookup"><span data-stu-id="d55ba-114">F or f</span></span>

<span data-ttu-id="d55ba-115">Wyświetla wpis wyliczenia jako wartość ciągu, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="d55ba-115">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="d55ba-116">Jeśli wartość może być w pełni wyświetlana jako suma wpisów w wyliczeniu (nawet jeśli nie ma atrybutu **flags** ), wartości ciągu każdego z prawidłowych wpisów są połączone, oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="d55ba-116">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="d55ba-117">Jeśli wartość nie może być całkowicie określona przez wpisy wyliczenia, wartość jest formatowana jako wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="d55ba-117">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="d55ba-118">Poniższy przykład ilustruje specyfikator formatu F.</span><span class="sxs-lookup"><span data-stu-id="d55ba-118">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="d55ba-119">D lub d</span><span class="sxs-lookup"><span data-stu-id="d55ba-119">D or d</span></span>

<span data-ttu-id="d55ba-120">Wyświetla wpis wyliczenia jako wartość całkowitą w najkrótszej możliwej reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="d55ba-120">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="d55ba-121">Poniższy przykład ilustruje specyfikator formatu D.</span><span class="sxs-lookup"><span data-stu-id="d55ba-121">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="d55ba-122">X lub x</span><span class="sxs-lookup"><span data-stu-id="d55ba-122">X or x</span></span>

<span data-ttu-id="d55ba-123">Wyświetla wpis wyliczenia jako wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="d55ba-123">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="d55ba-124">Wartość jest reprezentowana z wiodącymi zerami w razie potrzeby, aby upewnić się, że ciąg wynikowy ma dwa znaki dla każdego bajtu w [podstawowym typie liczbowym](xref:System.Enum.GetUnderlyingType%2A)typu wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d55ba-124">The value is represented with leading zeros as necessary, to ensure that the result string has two characters for each byte in the enumeration type's [underlying numeric type](xref:System.Enum.GetUnderlyingType%2A).</span></span> <span data-ttu-id="d55ba-125">Poniższy przykład ilustruje specyfikator formatu X.</span><span class="sxs-lookup"><span data-stu-id="d55ba-125">The following example illustrates the X format specifier.</span></span> <span data-ttu-id="d55ba-126">W przykładzie typ podstawowy obu <xref:System.ConsoleColor> i <xref:System.IO.FileAttributes> jest <xref:System.Int32> lub 32-bitową (lub 4-bajtową) liczbę całkowitą, która tworzy 8-znakowy ciąg wynikowy.</span><span class="sxs-lookup"><span data-stu-id="d55ba-126">In the example, the underlying type of both <xref:System.ConsoleColor> and <xref:System.IO.FileAttributes> is <xref:System.Int32>, or a 32-bit (or 4-byte) integer, which produces an 8-character result string.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="d55ba-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="d55ba-127">Example</span></span>

<span data-ttu-id="d55ba-128">W poniższym przykładzie zdefiniowano Wyliczenie `Colors` , które składa się z trzech wpisów: `Red` , `Blue` , i `Green` .</span><span class="sxs-lookup"><span data-stu-id="d55ba-128">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="d55ba-129">Po zdefiniowaniu wyliczenia wystąpienie może być deklarowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="d55ba-129">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="d55ba-130">`Color.ToString(System.String)`Metoda może następnie służyć do wyświetlania wartości wyliczenia na różne sposoby, w zależności od przenoszonego specyfikatora formatu.</span><span class="sxs-lookup"><span data-stu-id="d55ba-130">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="d55ba-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d55ba-131">See also</span></span>

- [<span data-ttu-id="d55ba-132">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="d55ba-132">Formatting Types</span></span>](formatting-types.md)
