---
title: "Analizowanie ciągów w .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 811db42e04e73d7acbc03e303297b19fdf643384
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="2f308-102">Analizowanie ciągów w .NET</span><span class="sxs-lookup"><span data-stu-id="2f308-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="2f308-103">Operacja związana konwertuje ciąg reprezentujący typ podstawowy .NET do tego typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="2f308-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="2f308-104">Na przykład operacji analizy służy do przekonwertowania ciągu liczba zmiennoprzecinkowa lub wartości daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="2f308-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="2f308-105">Metoda najczęściej używane do wykonywania operacji przetwarzania jest `Parse` metody.</span><span class="sxs-lookup"><span data-stu-id="2f308-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="2f308-106">Ponieważ analiza jest odwrotnej operacji formatowania (co wymaga konwersji typu podstawowego do reprezentacji ciągu), wiele tych samych reguł i konwencje zastosowania.</span><span class="sxs-lookup"><span data-stu-id="2f308-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="2f308-107">Tylko jako formatowania używa obiektu implementującego <xref:System.IFormatProvider> informacje zależne od kultury formatowania, analizowania również używa obiektu implementującego interfejs <xref:System.IFormatProvider> interfejsu, aby określić sposób interpretowania reprezentacji w postaci ciągu .</span><span class="sxs-lookup"><span data-stu-id="2f308-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="2f308-108">Aby uzyskać więcej informacji, zobacz [typy formatowania](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="2f308-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f308-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2f308-109">In This Section</span></span>  
 [<span data-ttu-id="2f308-110">Analizowanie ciągów liczbowych</span><span class="sxs-lookup"><span data-stu-id="2f308-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="2f308-111">Opisuje sposób konwertowania ciągów na typy liczbowe .NET.</span><span class="sxs-lookup"><span data-stu-id="2f308-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="2f308-112">Analizowanie ciągów daty i godziny</span><span class="sxs-lookup"><span data-stu-id="2f308-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="2f308-113">Opisuje sposób konwertowania ciągów na .NET **DateTime** typów.</span><span class="sxs-lookup"><span data-stu-id="2f308-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="2f308-114">Analizowanie innych ciągów</span><span class="sxs-lookup"><span data-stu-id="2f308-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="2f308-115">Opisuje sposób konwertowania ciągów do **Char**, **logiczna**, i **wyliczenia** typów.</span><span class="sxs-lookup"><span data-stu-id="2f308-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2f308-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2f308-116">Related Sections</span></span>  
 [<span data-ttu-id="2f308-117">Formatowanie tekstu</span><span class="sxs-lookup"><span data-stu-id="2f308-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="2f308-118">W tym artykule opisano podstawowe pojęcia dotyczące formatowania, takich jak specyfikatory formatu i dostawców formatu.</span><span class="sxs-lookup"><span data-stu-id="2f308-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="2f308-119">Konwersja typów w .NET</span><span class="sxs-lookup"><span data-stu-id="2f308-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="2f308-120">Opisuje sposób konwertowania typów.</span><span class="sxs-lookup"><span data-stu-id="2f308-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="2f308-121">Typy podstawowe</span><span class="sxs-lookup"><span data-stu-id="2f308-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="2f308-122">W tym artykule opisano typowe operacje, które można wykonywać na typy podstawowe .NET.</span><span class="sxs-lookup"><span data-stu-id="2f308-122">Describes common operations that you can perform on .NET base types.</span></span>
