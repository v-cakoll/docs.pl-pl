---
title: Ciągi formatujące Wyliczenie
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
ms.openlocfilehash: da7634758f5c4319fa18612d216682dc141318fd
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155961"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="9cf76-102">Ciągi formatujące Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9cf76-102">Enumeration format strings</span></span>

<span data-ttu-id="9cf76-103">Za pomocą metody <xref:System.Enum.ToString%2A?displayProperty=nameWithType> można utworzyć nowy obiekt ciągu, który reprezentuje wartość liczbową, szesnastkową lub ciąg elementu członkowskiego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9cf76-103">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="9cf76-104">Ta metoda przyjmuje jeden z ciągów formatowania wyliczenia, aby określić wartość, która ma zostać zwrócona.</span><span class="sxs-lookup"><span data-stu-id="9cf76-104">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="9cf76-105">W poniższych sekcjach wymieniono ciągi formatowania wyliczenia i zwracane przez nie wartości.</span><span class="sxs-lookup"><span data-stu-id="9cf76-105">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="9cf76-106">W tych specyfikatorach formatu nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="9cf76-106">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="9cf76-107">G lub g</span><span class="sxs-lookup"><span data-stu-id="9cf76-107">G or g</span></span>

<span data-ttu-id="9cf76-108">Wyświetla wpis wyliczenia jako wartość ciągu, jeśli jest to możliwe, i w przeciwnym razie wyświetla wartość całkowitą bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9cf76-108">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="9cf76-109">Jeśli Wyliczenie jest zdefiniowane przy użyciu ustawionych atrybutów **flag** , wartości ciągów każdego poprawnego wpisu są łączone razem, oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="9cf76-109">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="9cf76-110">Jeśli atrybut **flags** nie jest ustawiony, nieprawidłowa wartość jest wyświetlana jako wpis liczbowy.</span><span class="sxs-lookup"><span data-stu-id="9cf76-110">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="9cf76-111">Poniższy przykład ilustruje specyfikator formatu G.</span><span class="sxs-lookup"><span data-stu-id="9cf76-111">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="9cf76-112">F lub f</span><span class="sxs-lookup"><span data-stu-id="9cf76-112">F or f</span></span>

<span data-ttu-id="9cf76-113">Wyświetla wpis wyliczenia jako wartość ciągu, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="9cf76-113">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="9cf76-114">Jeśli wartość może być w pełni wyświetlana jako suma wpisów w wyliczeniu (nawet jeśli nie ma atrybutu **flags** ), wartości ciągu każdego z prawidłowych wpisów są połączone, oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="9cf76-114">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="9cf76-115">Jeśli wartość nie może być całkowicie określona przez wpisy wyliczenia, wartość jest formatowana jako wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="9cf76-115">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="9cf76-116">Poniższy przykład ilustruje specyfikator formatu F.</span><span class="sxs-lookup"><span data-stu-id="9cf76-116">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="9cf76-117">D lub d</span><span class="sxs-lookup"><span data-stu-id="9cf76-117">D or d</span></span>

<span data-ttu-id="9cf76-118">Wyświetla wpis wyliczenia jako wartość całkowitą w najkrótszej możliwej reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="9cf76-118">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="9cf76-119">Poniższy przykład ilustruje specyfikator formatu D.</span><span class="sxs-lookup"><span data-stu-id="9cf76-119">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="9cf76-120">X lub x</span><span class="sxs-lookup"><span data-stu-id="9cf76-120">X or x</span></span>

<span data-ttu-id="9cf76-121">Wyświetla wpis wyliczenia jako wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="9cf76-121">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="9cf76-122">Wartość jest reprezentowana z wiodącymi zerami w razie potrzeby, aby upewnić się, że ciąg wynikowy ma dwa znaki dla każdego bajtu w [podstawowym typie liczbowym](xref:System.Enum.GetUnderlyingType%2A)typu wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9cf76-122">The value is represented with leading zeros as necessary, to ensure that the result string has two characters for each byte in the enumeration type's [underlying numeric type](xref:System.Enum.GetUnderlyingType%2A).</span></span> <span data-ttu-id="9cf76-123">Poniższy przykład ilustruje specyfikator formatu X.</span><span class="sxs-lookup"><span data-stu-id="9cf76-123">The following example illustrates the X format specifier.</span></span> <span data-ttu-id="9cf76-124">W tym przykładzie typ podstawowy obu <xref:System.ConsoleColor> i <xref:System.IO.FileAttributes> jest <xref:System.Int32>lub 32-bitową (lub 4-bajtową) liczbą całkowitą, która tworzy 8-znakowy ciąg wynikowy.</span><span class="sxs-lookup"><span data-stu-id="9cf76-124">In the example, the underlying type of both <xref:System.ConsoleColor> and <xref:System.IO.FileAttributes> is <xref:System.Int32>, or a 32-bit (or 4-byte) integer, which produces an 8-character result string.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="9cf76-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cf76-125">Example</span></span>

<span data-ttu-id="9cf76-126">Poniższy przykład definiuje wyliczenie o nazwie `Colors`, które składa się z trzech wpisów: `Red`, `Blue`i `Green`.</span><span class="sxs-lookup"><span data-stu-id="9cf76-126">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="9cf76-127">Po zdefiniowaniu wyliczenia wystąpienie może być deklarowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="9cf76-127">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="9cf76-128">Metodę `Color.ToString(System.String)` można następnie użyć do wyświetlenia wartości wyliczenia na różne sposoby, w zależności od przenoszonego specyfikatora formatu.</span><span class="sxs-lookup"><span data-stu-id="9cf76-128">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="9cf76-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cf76-129">See also</span></span>

- [<span data-ttu-id="9cf76-130">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="9cf76-130">Formatting Types</span></span>](formatting-types.md)
