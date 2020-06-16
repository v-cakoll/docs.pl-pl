---
title: Analizowanie ciągów w programie .NET
description: Zrozumienie analizy ciągów w programie .NET. Analizowanie konwertuje ciąg reprezentujący typ podstawowy platformy .NET na ten typ podstawowy. Analizowanie jest operacją wsteczną do formatowania.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 5e297c8f689fdabc268ee6e269a7969155befe7b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769291"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="9a086-105">Analizowanie ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="9a086-105">Parsing Strings in .NET</span></span>
<span data-ttu-id="9a086-106">Operacja analizowania konwertuje ciąg, który reprezentuje typ podstawowy platformy .NET do tego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="9a086-106">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="9a086-107">Na przykład operacja analizowania służy do konwertowania ciągu na liczbę zmiennoprzecinkową lub na wartość daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="9a086-107">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="9a086-108">Metoda najczęściej używana do wykonywania operacji analizowania jest `Parse` metodą.</span><span class="sxs-lookup"><span data-stu-id="9a086-108">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="9a086-109">Ponieważ analizowanie jest operacją wsteczną formatowania (która wymaga przekonwertowania typu bazowego na jego reprezentację ciągu), mają zastosowanie wiele z tych samych zasad i Konwencji.</span><span class="sxs-lookup"><span data-stu-id="9a086-109">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="9a086-110">Tak samo jak formatowanie korzysta z obiektu, który implementuje <xref:System.IFormatProvider> interfejs, aby zapewnić informacje o formatowaniu z uwzględnieniem kultury, podczas analizy używa również obiektu, który implementuje <xref:System.IFormatProvider> interfejs, aby określić sposób interpretowania przedstawienia ciągu.</span><span class="sxs-lookup"><span data-stu-id="9a086-110">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="9a086-111">Aby uzyskać więcej informacji, zobacz [Typy formatowania](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="9a086-111">For more information, see [Formatting Types](formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a086-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9a086-112">In This Section</span></span>  
 [<span data-ttu-id="9a086-113">Analizowanie ciągów liczbowych</span><span class="sxs-lookup"><span data-stu-id="9a086-113">Parsing Numeric Strings</span></span>](parsing-numeric.md)  
 <span data-ttu-id="9a086-114">Opisuje sposób konwersji ciągów na typy liczbowe platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="9a086-114">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="9a086-115">Analizowanie ciągów daty i godziny</span><span class="sxs-lookup"><span data-stu-id="9a086-115">Parsing Date and Time Strings</span></span>](parsing-datetime.md)  
 <span data-ttu-id="9a086-116">Opisuje sposób konwertowania ciągów na typy **datetimes** platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="9a086-116">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="9a086-117">Analiza składniowa innych ciągów</span><span class="sxs-lookup"><span data-stu-id="9a086-117">Parsing Other Strings</span></span>](parsing-other.md)  
 <span data-ttu-id="9a086-118">Opisuje sposób konwersji ciągów na typy **znaków**, **wartości logicznych**i typów **wyliczeniowych** .</span><span class="sxs-lookup"><span data-stu-id="9a086-118">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a086-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9a086-119">Related Sections</span></span>  
 [<span data-ttu-id="9a086-120">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="9a086-120">Formatting Types</span></span>](formatting-types.md)  
 <span data-ttu-id="9a086-121">Opisuje podstawowe pojęcia dotyczące formatowania, takie jak specyfikatory formatu i dostawcy formatowania.</span><span class="sxs-lookup"><span data-stu-id="9a086-121">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="9a086-122">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="9a086-122">Type Conversion in .NET</span></span>](type-conversion.md)  
 <span data-ttu-id="9a086-123">Opisuje sposób konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="9a086-123">Describes how to convert types.</span></span>
