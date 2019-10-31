---
title: Analizowanie ciągów w programie .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: e4bf14981e538d95aebac3b0f36d38b61747989f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084312"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="b9eb7-102">Analizowanie ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="b9eb7-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="b9eb7-103">Operacja analizowania konwertuje ciąg, który reprezentuje typ podstawowy platformy .NET do tego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="b9eb7-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="b9eb7-104">Na przykład operacja analizowania służy do konwertowania ciągu na liczbę zmiennoprzecinkową lub na wartość daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="b9eb7-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="b9eb7-105">Metoda najczęściej używana do wykonywania operacji analizowania jest metodą `Parse`.</span><span class="sxs-lookup"><span data-stu-id="b9eb7-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="b9eb7-106">Ponieważ analizowanie jest operacją wsteczną formatowania (która wymaga przekonwertowania typu bazowego na jego reprezentację ciągu), mają zastosowanie wiele z tych samych zasad i Konwencji.</span><span class="sxs-lookup"><span data-stu-id="b9eb7-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="b9eb7-107">Podobnie jak formatowanie korzysta z obiektu, który implementuje interfejs <xref:System.IFormatProvider>, aby zapewnić informacje o formatowaniu z uwzględnieniem kultury, podczas analizowania używa również obiektu, który implementuje interfejs <xref:System.IFormatProvider>, aby określić sposób interpretowania reprezentacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="b9eb7-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="b9eb7-108">Aby uzyskać więcej informacji, zobacz [Typy formatowania](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="b9eb7-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9eb7-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b9eb7-109">In This Section</span></span>  
 [<span data-ttu-id="b9eb7-110">Analizowanie ciągów liczbowych</span><span class="sxs-lookup"><span data-stu-id="b9eb7-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="b9eb7-111">Opisuje sposób konwersji ciągów na typy liczbowe platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b9eb7-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="b9eb7-112">Analizowanie ciągów daty i godziny</span><span class="sxs-lookup"><span data-stu-id="b9eb7-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="b9eb7-113">Opisuje sposób konwertowania ciągów na typy **datetimes** platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b9eb7-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="b9eb7-114">Analizowanie innych typów ciągów</span><span class="sxs-lookup"><span data-stu-id="b9eb7-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="b9eb7-115">Opisuje sposób konwersji ciągów na typy **znaków**, **wartości logicznych**i typów **wyliczeniowych** .</span><span class="sxs-lookup"><span data-stu-id="b9eb7-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b9eb7-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b9eb7-116">Related Sections</span></span>  
 [<span data-ttu-id="b9eb7-117">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="b9eb7-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="b9eb7-118">Opisuje podstawowe pojęcia dotyczące formatowania, takie jak specyfikatory formatu i dostawcy formatowania.</span><span class="sxs-lookup"><span data-stu-id="b9eb7-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="b9eb7-119">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="b9eb7-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="b9eb7-120">Opisuje sposób konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="b9eb7-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="b9eb7-121">Typy podstawowe</span><span class="sxs-lookup"><span data-stu-id="b9eb7-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="b9eb7-122">Opisuje Typowe operacje, które można wykonywać na podstawowych typach .NET.</span><span class="sxs-lookup"><span data-stu-id="b9eb7-122">Describes common operations that you can perform on .NET base types.</span></span>
