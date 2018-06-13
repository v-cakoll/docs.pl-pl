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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6e0e7e69affd93320ec3f3d73e6254befaf6ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567747"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="d2e85-102">Analizowanie ciągów w .NET</span><span class="sxs-lookup"><span data-stu-id="d2e85-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="d2e85-103">Operacja związana konwertuje ciąg reprezentujący typ podstawowy .NET do tego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="d2e85-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="d2e85-104">Na przykład operacji analizy służy do przekonwertowania ciągu liczba zmiennoprzecinkowa lub wartości daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="d2e85-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="d2e85-105">Metoda najczęściej używane do wykonywania operacji przetwarzania jest `Parse` metody.</span><span class="sxs-lookup"><span data-stu-id="d2e85-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="d2e85-106">Ponieważ analiza jest odwrotnej operacji formatowania (co wymaga konwersji typu podstawowego do reprezentacji ciągu), wiele tych samych reguł i konwencje zastosowania.</span><span class="sxs-lookup"><span data-stu-id="d2e85-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="d2e85-107">Tylko jako formatowania używa obiektu implementującego <xref:System.IFormatProvider> informacje zależne od kultury formatowania, analizowania również używa obiektu implementującego interfejs <xref:System.IFormatProvider> interfejsu, aby określić sposób interpretowania reprezentacji w postaci ciągu .</span><span class="sxs-lookup"><span data-stu-id="d2e85-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="d2e85-108">Aby uzyskać więcej informacji, zobacz [typy formatowania](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="d2e85-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d2e85-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d2e85-109">In This Section</span></span>  
 [<span data-ttu-id="d2e85-110">Analizowanie ciągów liczbowych</span><span class="sxs-lookup"><span data-stu-id="d2e85-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="d2e85-111">Opisuje sposób konwertowania ciągów na typy liczbowe .NET.</span><span class="sxs-lookup"><span data-stu-id="d2e85-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="d2e85-112">Analizowanie ciągów daty i godziny</span><span class="sxs-lookup"><span data-stu-id="d2e85-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="d2e85-113">Opisuje sposób konwertowania ciągów na .NET **DateTime** typów.</span><span class="sxs-lookup"><span data-stu-id="d2e85-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="d2e85-114">Analizowanie innych typów ciągów</span><span class="sxs-lookup"><span data-stu-id="d2e85-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="d2e85-115">Opisuje sposób konwertowania ciągów do **Char**, **logiczna**, i **wyliczenia** typów.</span><span class="sxs-lookup"><span data-stu-id="d2e85-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d2e85-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d2e85-116">Related Sections</span></span>  
 [<span data-ttu-id="d2e85-117">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="d2e85-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="d2e85-118">W tym artykule opisano podstawowe pojęcia dotyczące formatowania, takich jak specyfikatory formatu i dostawców formatu.</span><span class="sxs-lookup"><span data-stu-id="d2e85-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="d2e85-119">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="d2e85-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="d2e85-120">Opisuje sposób konwertowania typów.</span><span class="sxs-lookup"><span data-stu-id="d2e85-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="d2e85-121">Typy podstawowe</span><span class="sxs-lookup"><span data-stu-id="d2e85-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="d2e85-122">W tym artykule opisano typowe operacje, które można wykonywać na typy podstawowe .NET.</span><span class="sxs-lookup"><span data-stu-id="d2e85-122">Describes common operations that you can perform on .NET base types.</span></span>
