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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6e0e7e69affd93320ec3f3d73e6254befaf6ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766002"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="55fa8-102">Analizowanie ciągów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="55fa8-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="55fa8-103">Operacji analizowania konwertuje ciąg reprezentujący typ podstawowy .NET do tego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="55fa8-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="55fa8-104">Na przykład operacji analizowania służy do przekonwertowania ciągu na liczbę zmiennoprzecinkową lub wartości daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="55fa8-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="55fa8-105">Metoda najczęściej używany do wykonywania operacji analizowania `Parse` metody.</span><span class="sxs-lookup"><span data-stu-id="55fa8-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="55fa8-106">Ponieważ analiza jest odwrotna operacją formatowania (co wymaga konwersji typu podstawowego na jego reprezentację ciągu), wiele tych samych reguł i Konwencji zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="55fa8-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="55fa8-107">Podobnie jak formatowanie używa obiekt, który implementuje <xref:System.IFormatProvider> interfejsu, aby zapewnić kultury informacje o formatowaniu, analizowania również używa obiekt, który implementuje <xref:System.IFormatProvider> interfejsu, aby określić sposób interpretowania reprezentację ciągu znaków .</span><span class="sxs-lookup"><span data-stu-id="55fa8-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="55fa8-108">Aby uzyskać więcej informacji, zobacz [typy formatowania](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="55fa8-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55fa8-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="55fa8-109">In This Section</span></span>  
 [<span data-ttu-id="55fa8-110">Analizowanie ciągów liczbowych</span><span class="sxs-lookup"><span data-stu-id="55fa8-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="55fa8-111">W tym artykule opisano sposób konwertowania ciągów na typy liczbowe .NET.</span><span class="sxs-lookup"><span data-stu-id="55fa8-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="55fa8-112">Analizowanie ciągów daty i godziny</span><span class="sxs-lookup"><span data-stu-id="55fa8-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="55fa8-113">W tym artykule opisano sposób konwertowania ciągów w środowisku .NET **daty/godziny** typów.</span><span class="sxs-lookup"><span data-stu-id="55fa8-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="55fa8-114">Analizowanie innych typów ciągów</span><span class="sxs-lookup"><span data-stu-id="55fa8-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="55fa8-115">W tym artykule opisano sposób konwertowania ciągów do **Char**, **logiczna**, i **wyliczenia** typów.</span><span class="sxs-lookup"><span data-stu-id="55fa8-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="55fa8-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="55fa8-116">Related Sections</span></span>  
 [<span data-ttu-id="55fa8-117">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="55fa8-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="55fa8-118">W tym artykule opisano podstawowe pojęcia formatowania, takich jak specyfikatorów formatu i format dostawców.</span><span class="sxs-lookup"><span data-stu-id="55fa8-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="55fa8-119">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="55fa8-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="55fa8-120">W tym artykule opisano sposób konwertowania typów.</span><span class="sxs-lookup"><span data-stu-id="55fa8-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="55fa8-121">Typy podstawowe</span><span class="sxs-lookup"><span data-stu-id="55fa8-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="55fa8-122">W tym artykule opisano typowe operacje, które można wykonywać na typy podstawowe dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="55fa8-122">Describes common operations that you can perform on .NET base types.</span></span>
