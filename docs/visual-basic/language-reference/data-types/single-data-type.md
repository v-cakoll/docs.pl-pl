---
title: "Single — Typ danych (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c91dbdf73ed1e26393518001ec8651557e5b780f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="c268d-102">Single — Typ danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c268d-102">Single Data Type (Visual Basic)</span></span>
<span data-ttu-id="c268d-103">Blokad podpisany IEEE 32-bitowe (4-bajtowych) pojedynczej precyzji liczb zmiennoprzecinkowych z zakresu od - 3.4028235E + 38 do - 1, 401298E-45 dla wartości ujemnych i od 1, 401298E-45 za pośrednictwem 3.4028235E + 38 dla wartości dodatnie.</span><span class="sxs-lookup"><span data-stu-id="c268d-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="c268d-104">Liczby o pojedynczej dokładności przechowywać zbliżenia liczba rzeczywista.</span><span class="sxs-lookup"><span data-stu-id="c268d-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c268d-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c268d-105">Remarks</span></span>  
 <span data-ttu-id="c268d-106">Użyj `Single` — typ danych zawierający wartości zmiennoprzecinkowych, które nie wymagają szerokość pełnych danych `Double`.</span><span class="sxs-lookup"><span data-stu-id="c268d-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="c268d-107">W niektórych przypadkach może mieć możliwość pakietu środowisko uruchomieniowe języka wspólnego programu `Single` zmienne ściśle współpracują, a następnie zapisz zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="c268d-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="c268d-108">Wartość domyślna `Single` ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="c268d-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="c268d-109">Porady dla programistów</span><span class="sxs-lookup"><span data-stu-id="c268d-109">Programming Tips</span></span>  
  
-   <span data-ttu-id="c268d-110">**Precyzja.**</span><span class="sxs-lookup"><span data-stu-id="c268d-110">**Precision.**</span></span> <span data-ttu-id="c268d-111">Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają dokładne reprezentacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c268d-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="c268d-112">Może to prowadzić do nieoczekiwanych wyników z niektórych operacji, takich jak porównania wartości i `Mod` operatora.</span><span class="sxs-lookup"><span data-stu-id="c268d-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="c268d-113">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="c268d-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="c268d-114">**Rozszerzanie.**</span><span class="sxs-lookup"><span data-stu-id="c268d-114">**Widening.**</span></span> <span data-ttu-id="c268d-115">`Single` Rozszerzenie typu danych do `Double`.</span><span class="sxs-lookup"><span data-stu-id="c268d-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="c268d-116">Oznacza to, że można przekonwertować `Single` do `Double` bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.</span><span class="sxs-lookup"><span data-stu-id="c268d-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="c268d-117">**Końcowe zero.**</span><span class="sxs-lookup"><span data-stu-id="c268d-117">**Trailing Zeros.**</span></span> <span data-ttu-id="c268d-118">Typy danych zmiennoprzecinkowych nie mają żadnych wewnętrznej reprezentacji końcowych 0 znaków.</span><span class="sxs-lookup"><span data-stu-id="c268d-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="c268d-119">Na przykład one rozróżnia 4.2000 i 4.2.</span><span class="sxs-lookup"><span data-stu-id="c268d-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="c268d-120">W rezultacie znakami 0 nie jest wyświetlana podczas wyświetlania lub drukowania wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="c268d-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="c268d-121">**Znaki typu.**</span><span class="sxs-lookup"><span data-stu-id="c268d-121">**Type Characters.**</span></span> <span data-ttu-id="c268d-122">Znak literalny typu dołączanie `F` do literału wymusza `Single` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="c268d-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="c268d-123">Dołączanie znak typu identyfikator `!` dla wszystkich identyfikatorów wymusza `Single`.</span><span class="sxs-lookup"><span data-stu-id="c268d-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
-   <span data-ttu-id="c268d-124">**Typ struktury.**</span><span class="sxs-lookup"><span data-stu-id="c268d-124">**Framework Type.**</span></span> <span data-ttu-id="c268d-125">Danego typu w programie .NET Framework jest <xref:System.Single?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="c268d-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c268d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c268d-126">See Also</span></span>  
 <xref:System.Single?displayProperty=nameWithType>  
 [<span data-ttu-id="c268d-127">Typy danych</span><span class="sxs-lookup"><span data-stu-id="c268d-127">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="c268d-128">Decimal — typ danych</span><span class="sxs-lookup"><span data-stu-id="c268d-128">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [<span data-ttu-id="c268d-129">Double — typ danych</span><span class="sxs-lookup"><span data-stu-id="c268d-129">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [<span data-ttu-id="c268d-130">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="c268d-130">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="c268d-131">Konwersja — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="c268d-131">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="c268d-132">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="c268d-132">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="c268d-133">Rozwiązywanie problemów z typów danych</span><span class="sxs-lookup"><span data-stu-id="c268d-133">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
