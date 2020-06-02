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
ms.openlocfilehash: ab446a8f868cabdeff73d1b72e1399b7c2beb1e1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277417"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="1f334-102">Analizowanie ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="1f334-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="1f334-103">Operacja analizowania konwertuje ciąg, który reprezentuje typ podstawowy platformy .NET do tego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="1f334-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="1f334-104">Na przykład operacja analizowania służy do konwertowania ciągu na liczbę zmiennoprzecinkową lub na wartość daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="1f334-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="1f334-105">Metoda najczęściej używana do wykonywania operacji analizowania jest `Parse` metodą.</span><span class="sxs-lookup"><span data-stu-id="1f334-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="1f334-106">Ponieważ analizowanie jest operacją wsteczną formatowania (która wymaga przekonwertowania typu bazowego na jego reprezentację ciągu), mają zastosowanie wiele z tych samych zasad i Konwencji.</span><span class="sxs-lookup"><span data-stu-id="1f334-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="1f334-107">Tak samo jak formatowanie korzysta z obiektu, który implementuje <xref:System.IFormatProvider> interfejs, aby zapewnić informacje o formatowaniu z uwzględnieniem kultury, podczas analizy używa również obiektu, który implementuje <xref:System.IFormatProvider> interfejs, aby określić sposób interpretowania przedstawienia ciągu.</span><span class="sxs-lookup"><span data-stu-id="1f334-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="1f334-108">Aby uzyskać więcej informacji, zobacz [Typy formatowania](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="1f334-108">For more information, see [Formatting Types](formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f334-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1f334-109">In This Section</span></span>  
 [<span data-ttu-id="1f334-110">Analizowanie ciągów liczbowych</span><span class="sxs-lookup"><span data-stu-id="1f334-110">Parsing Numeric Strings</span></span>](parsing-numeric.md)  
 <span data-ttu-id="1f334-111">Opisuje sposób konwersji ciągów na typy liczbowe platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="1f334-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="1f334-112">Analizowanie ciągów daty i godziny</span><span class="sxs-lookup"><span data-stu-id="1f334-112">Parsing Date and Time Strings</span></span>](parsing-datetime.md)  
 <span data-ttu-id="1f334-113">Opisuje sposób konwertowania ciągów na typy **datetimes** platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="1f334-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="1f334-114">Analiza składniowa innych ciągów</span><span class="sxs-lookup"><span data-stu-id="1f334-114">Parsing Other Strings</span></span>](parsing-other.md)  
 <span data-ttu-id="1f334-115">Opisuje sposób konwersji ciągów na typy **znaków**, **wartości logicznych**i typów **wyliczeniowych** .</span><span class="sxs-lookup"><span data-stu-id="1f334-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1f334-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="1f334-116">Related Sections</span></span>  
 [<span data-ttu-id="1f334-117">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="1f334-117">Formatting Types</span></span>](formatting-types.md)  
 <span data-ttu-id="1f334-118">Opisuje podstawowe pojęcia dotyczące formatowania, takie jak specyfikatory formatu i dostawcy formatowania.</span><span class="sxs-lookup"><span data-stu-id="1f334-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="1f334-119">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="1f334-119">Type Conversion in .NET</span></span>](type-conversion.md)  
 <span data-ttu-id="1f334-120">Opisuje sposób konwersji typów.</span><span class="sxs-lookup"><span data-stu-id="1f334-120">Describes how to convert types.</span></span>
