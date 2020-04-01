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
ms.openlocfilehash: 717022e5d2e292c1624e6155bd7571e4daa997b9
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523805"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="7d5a8-102">Analizowanie ciągów w .NET</span><span class="sxs-lookup"><span data-stu-id="7d5a8-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="7d5a8-103">Operacja analizowania konwertuje ciąg reprezentujący typ podstawowy platformy .NET na ten typ podstawowy.</span><span class="sxs-lookup"><span data-stu-id="7d5a8-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="7d5a8-104">Na przykład operacja analizowania służy do konwertowania ciągu na liczbę zmiennoprzecinkową lub na wartość daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="7d5a8-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="7d5a8-105">Metoda najczęściej używana do wykonywania operacji analizy jest `Parse` metoda.</span><span class="sxs-lookup"><span data-stu-id="7d5a8-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="7d5a8-106">Ponieważ analizowanie jest odwrotną operacją formatowania (która polega na konwersji typu podstawowego na jego reprezentację ciągu), stosuje się wiele tych samych reguł i konwencji.</span><span class="sxs-lookup"><span data-stu-id="7d5a8-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="7d5a8-107">Podobnie jak formatowanie używa obiektu, <xref:System.IFormatProvider> który implementuje interfejs, aby zapewnić informacje o formatowaniu zależne <xref:System.IFormatProvider> od kultury, analizowanie używa również obiektu, który implementuje interfejs, aby określić sposób interpretowania reprezentacji ciągów.</span><span class="sxs-lookup"><span data-stu-id="7d5a8-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="7d5a8-108">Aby uzyskać więcej informacji, zobacz [Typy formatowania](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="7d5a8-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d5a8-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7d5a8-109">In This Section</span></span>  
 [<span data-ttu-id="7d5a8-110">Analizowanie ciągów liczbowych</span><span class="sxs-lookup"><span data-stu-id="7d5a8-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="7d5a8-111">W tym artykule opisano sposób konwertowania ciągów na typy liczbowe .NET.</span><span class="sxs-lookup"><span data-stu-id="7d5a8-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="7d5a8-112">Analizowanie ciągów daty i godziny</span><span class="sxs-lookup"><span data-stu-id="7d5a8-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="7d5a8-113">W tym artykule opisano sposób konwertowania ciągów na typy **.NET DateTime.**</span><span class="sxs-lookup"><span data-stu-id="7d5a8-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="7d5a8-114">Analiza składniowa innych ciągów</span><span class="sxs-lookup"><span data-stu-id="7d5a8-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="7d5a8-115">W tym artykule opisano sposób konwertowania ciągów na typy **Char,** **Boolean**i **Enum.**</span><span class="sxs-lookup"><span data-stu-id="7d5a8-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7d5a8-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7d5a8-116">Related Sections</span></span>  
 [<span data-ttu-id="7d5a8-117">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="7d5a8-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="7d5a8-118">Zawiera opis podstawowych pojęć formatowania, takich jak specyfikatory formatów i dostawcy formatów.</span><span class="sxs-lookup"><span data-stu-id="7d5a8-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="7d5a8-119">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="7d5a8-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="7d5a8-120">W tym artykule opisano sposób konwertowania typów.</span><span class="sxs-lookup"><span data-stu-id="7d5a8-120">Describes how to convert types.</span></span>
