---
title: Analizowanie ciągów w .NET
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084312"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="e1065-102">Analizowanie ciągów w .NET</span><span class="sxs-lookup"><span data-stu-id="e1065-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="e1065-103">Operacja analizy konwertuje ciąg reprezentujący typ podstawowy .NET na ten typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="e1065-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="e1065-104">Na przykład operacja analizy służy do konwertowania ciągu na liczbę zmiennoprzecinkową lub na wartość daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="e1065-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="e1065-105">Metoda najczęściej używana do wykonywania operacji analizy `Parse` jest metodą.</span><span class="sxs-lookup"><span data-stu-id="e1065-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="e1065-106">Ponieważ analizowanie jest odwrotną operacją formatowania (która polega na konwertowaniu typu podstawowego na reprezentację ciągu), stosuje się wiele tych samych reguł i konwencji.</span><span class="sxs-lookup"><span data-stu-id="e1065-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="e1065-107">Podobnie jak formatowanie używa obiektu, <xref:System.IFormatProvider> który implementuje interfejs, aby zapewnić informacje o formatowaniu poufnych <xref:System.IFormatProvider> dla kultury, analizowanie używa również obiektu, który implementuje interfejs, aby określić sposób interpretowania reprezentacji ciągów.</span><span class="sxs-lookup"><span data-stu-id="e1065-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="e1065-108">Aby uzyskać więcej informacji, zobacz [Typy formatowania](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="e1065-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1065-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e1065-109">In This Section</span></span>  
 [<span data-ttu-id="e1065-110">Analizowanie ciągów numerycznych</span><span class="sxs-lookup"><span data-stu-id="e1065-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="e1065-111">W tym artykule opisano sposób konwertowania ciągów na typy liczbowe .NET.</span><span class="sxs-lookup"><span data-stu-id="e1065-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="e1065-112">Analiza składniowa ciągów daty i godziny</span><span class="sxs-lookup"><span data-stu-id="e1065-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="e1065-113">W tym artykule opisano sposób konwertowania ciągów na typy **.NET DateTime.**</span><span class="sxs-lookup"><span data-stu-id="e1065-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="e1065-114">Analizowanie innych typów ciągów</span><span class="sxs-lookup"><span data-stu-id="e1065-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="e1065-115">Opisuje sposób konwertowania ciągów na typy **Char,** **Boolean**i **Enum.**</span><span class="sxs-lookup"><span data-stu-id="e1065-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e1065-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e1065-116">Related Sections</span></span>  
 [<span data-ttu-id="e1065-117">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="e1065-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="e1065-118">W tym artykule opisano podstawowe pojęcia dotyczące formatowania, takie jak specyfikatory formatów i dostawcy formatów.</span><span class="sxs-lookup"><span data-stu-id="e1065-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="e1065-119">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="e1065-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="e1065-120">Opisuje sposób konwertowania typów.</span><span class="sxs-lookup"><span data-stu-id="e1065-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="e1065-121">Typy podstawowe</span><span class="sxs-lookup"><span data-stu-id="e1065-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="e1065-122">W tym artykule opisano typowe operacje, które można wykonać na typach podstawowych .NET.</span><span class="sxs-lookup"><span data-stu-id="e1065-122">Describes common operations that you can perform on .NET base types.</span></span>
