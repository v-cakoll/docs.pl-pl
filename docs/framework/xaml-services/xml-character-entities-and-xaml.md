---
title: "Jednostki znaków XML i XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
caps.latest.revision: "23"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5973c67b26e07bba69383cc625ff34493d825a41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xml-character-entities-and-xaml"></a><span data-ttu-id="541ff-102">Jednostki znaków XML i XAML</span><span class="sxs-lookup"><span data-stu-id="541ff-102">XML Character Entities and XAML</span></span>
<span data-ttu-id="541ff-103">XAML używa jednostki znaków zdefiniowane w pliku XML dla znaków specjalnych.</span><span class="sxs-lookup"><span data-stu-id="541ff-103">XAML uses character entities defined in XML for special characters.</span></span> <span data-ttu-id="541ff-104">W tym temacie opisano niektóre jednostki określonych znaków i Ogólne zagadnienia dotyczące innych koncepcji XML w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="541ff-104">This topic describes some specific character entities and general considerations for other XML concepts in XAML.</span></span>  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a><span data-ttu-id="541ff-105">Jednostki znaków i anulowanie problemy, które są unikatowe dla XAML</span><span class="sxs-lookup"><span data-stu-id="541ff-105">Character Entities and Escaping Issues That Are Unique to XAML</span></span>  
 <span data-ttu-id="541ff-106">Kod znaczników XAML zwykle korzysta z tej samej jednostki znaków i sekwencji unikowych, które są zdefiniowane w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="541ff-106">XAML markup typically uses the same character entities and escape sequences that are defined in XML.</span></span>  
  
 <span data-ttu-id="541ff-107">Głównego wyjątek to, że nawiasy klamrowe ({i}) ma znaczenie w języku XAML, ponieważ te znaki informuje procesora XAML, czy sekwencja znaków w nawiasach klamrowych musi być interpretowane jako rozszerzenie znaczników.</span><span class="sxs-lookup"><span data-stu-id="541ff-107">The main exception is that braces ({ and }) have significance in XAML because these characters inform a XAML processor that a character sequence enclosed by braces must be interpreted as a markup extension.</span></span> <span data-ttu-id="541ff-108">Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników dla przeglądu XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="541ff-108">For more information about markup extensions, see [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span></span>  
  
 <span data-ttu-id="541ff-109">Jednakże nadal można wyświetlić nawiasy klamrowe jako literały przy użyciu sekwencji unikowej specyficznych dla języka XAML, a nie XML.</span><span class="sxs-lookup"><span data-stu-id="541ff-109">However, you can still display the braces as literal characters by using an escape sequence that is particular to XAML instead of XML.</span></span> <span data-ttu-id="541ff-110">Aby uzyskać więcej informacji, zobacz [{} sekwencja ucieczki — rozszerzenie znaczników](escape-sequence-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="541ff-110">For more information, see [{} Escape Sequence - Markup Extension](escape-sequence-markup-extension.md).</span></span>  
  
 <span data-ttu-id="541ff-111">Należy pamiętać, że ukośnik odwrotny (\\) nie wymaga sekwencji unikowej, gdy jest on traktowany jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="541ff-111">Note that a backslash (\\) does not require an escape sequence when it is handled as a string.</span></span>  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a><span data-ttu-id="541ff-112">Jednostki znaków XML</span><span class="sxs-lookup"><span data-stu-id="541ff-112">XML Character Entities</span></span>  
 <span data-ttu-id="541ff-113">Jak wspomniano wcześniej, większość jednostki znaków i sekwencji unikowych, które są zazwyczaj używane do zapisania znaczników XAML są definiowane przez XML.</span><span class="sxs-lookup"><span data-stu-id="541ff-113">As mentioned previously, most character entities and escape sequences that are typically used to write XAML markup are defined by XML.</span></span> <span data-ttu-id="541ff-114">Ten temat nie zawiera pełną listę tych jednostek; szczegółowe odwołania dla jednostek znajduje się w dokumentacji zewnętrznych, takich jak w specyfikacji XML.</span><span class="sxs-lookup"><span data-stu-id="541ff-114">This topic does not provide the complete list of these entities; a detailed reference for the entities can be found in external documentation, such as in XML specifications.</span></span> <span data-ttu-id="541ff-115">Jednak dla wygody, w tym temacie przedstawiono określonej jednostki znaków XML, które są zazwyczaj używane w kodzie XAML.</span><span class="sxs-lookup"><span data-stu-id="541ff-115">However, for convenience, this topic lists some of the specific XML character entities that are typically used in XAML markup.</span></span>  
  
|<span data-ttu-id="541ff-116">Znak</span><span class="sxs-lookup"><span data-stu-id="541ff-116">Character</span></span>|<span data-ttu-id="541ff-117">Jednostka</span><span class="sxs-lookup"><span data-stu-id="541ff-117">Entity</span></span>|<span data-ttu-id="541ff-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="541ff-118">Notes</span></span>|  
|---------------|------------|-----------|  
|<span data-ttu-id="541ff-119">& (znak handlowe „i”)</span><span class="sxs-lookup"><span data-stu-id="541ff-119">& (ampersand)</span></span>|&amp;|<span data-ttu-id="541ff-120">Musi być używany dla wartości atrybutów i zawartości elementu.</span><span class="sxs-lookup"><span data-stu-id="541ff-120">Must be used both for attribute values and for content of an element.</span></span>|  
|<span data-ttu-id="541ff-121">> (większe-niż znak)</span><span class="sxs-lookup"><span data-stu-id="541ff-121">> (greater-than character)</span></span>|&gt;|<span data-ttu-id="541ff-122">Dla wartości atrybutu muszą być używane, ale > jest akceptowany w zawartości elementu tak długo, jak < nie poprzedza.</span><span class="sxs-lookup"><span data-stu-id="541ff-122">Must be used for an attribute value, but > is acceptable as the content of an element as long as < does not precede it.</span></span>|  
|<span data-ttu-id="541ff-123">< (mniej-niż znak)</span><span class="sxs-lookup"><span data-stu-id="541ff-123">< (less-than character)</span></span>|&lt;|<span data-ttu-id="541ff-124">Dla wartości atrybutu muszą być używane, ale \< jest akceptowany w zawartości elementu tak długo, jak > nie jest zgodna.</span><span class="sxs-lookup"><span data-stu-id="541ff-124">Must be used for an attribute value, but \< is acceptable as the content of an element as long as > does not follow it.</span></span>|  
|<span data-ttu-id="541ff-125">"(proste cudzysłów)</span><span class="sxs-lookup"><span data-stu-id="541ff-125">" (straight quotation mark)</span></span>|&quot;|<span data-ttu-id="541ff-126">Dla wartości atrybutu muszą być używane, ale proste znak cudzysłowu (") jest akceptowany w zawartości elementu.</span><span class="sxs-lookup"><span data-stu-id="541ff-126">Must be used for an attribute value, but a straight quotation mark (") is acceptable as the content of an element.</span></span> <span data-ttu-id="541ff-127">Należy pamiętać, że wartości atrybutu może być ujęte proste znak pojedynczego cudzysłowu (') lub proste znak cudzysłowu ("); występuje jako pierwszy znak niezależnie od definiuje obudowa wartość atrybutu i alternatywne oferty mogą następnie służyć jako literał w wartości.</span><span class="sxs-lookup"><span data-stu-id="541ff-127">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="541ff-128">"(proste cudzysłów pojedynczy)</span><span class="sxs-lookup"><span data-stu-id="541ff-128">' (single straight quotation mark)</span></span>|&apos;|<span data-ttu-id="541ff-129">Dla wartości atrybutu muszą być używane, ale proste znak pojedynczego cudzysłowu (') jest akceptowany w zawartości elementu.</span><span class="sxs-lookup"><span data-stu-id="541ff-129">Must be used for an attribute value, but a single straight quotation mark (') is acceptable as the content of an element.</span></span> <span data-ttu-id="541ff-130">Należy pamiętać, że wartości atrybutu może być ujęte proste znak pojedynczego cudzysłowu (') lub proste znak cudzysłowu ("); występuje jako pierwszy znak niezależnie od definiuje obudowa wartość atrybutu i alternatywne oferty mogą następnie służyć jako literał w wartości.</span><span class="sxs-lookup"><span data-stu-id="541ff-130">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="541ff-131">(znaku numerycznego mapowania)</span><span class="sxs-lookup"><span data-stu-id="541ff-131">(numeric character mappings)</span></span>|<span data-ttu-id="541ff-132">&#*[liczba całkowita]* ; lub & #x*[szesnastkowych]*;</span><span class="sxs-lookup"><span data-stu-id="541ff-132">&#*[integer]*; or &#x*[hex]*;</span></span>|<span data-ttu-id="541ff-133">XAML obsługuje mapowania znaku numerycznego do kodowania, które jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="541ff-133">XAML supports numeric character mappings into the encoding that is active.</span></span>|  
|<span data-ttu-id="541ff-134">(nierozdzielających miejsca)</span><span class="sxs-lookup"><span data-stu-id="541ff-134">(nonbreaking space)</span></span>|<span data-ttu-id="541ff-135">&\#160; (przy założeniu, kodowania UTF-8)</span><span class="sxs-lookup"><span data-stu-id="541ff-135">&\#160; (assuming UTF-8 encoding)</span></span>|<span data-ttu-id="541ff-136">Dla elementów dokumentu przepływu i elementy, które tekstu, takich jak WPF <xref:System.Windows.Controls.TextBox>, spacji nierozdzielających nie są znormalizować poza znaczników, nawet w przypadku `xml:space="default"`.</span><span class="sxs-lookup"><span data-stu-id="541ff-136">For flow document elements, or elements that take text such as the WPF <xref:System.Windows.Controls.TextBox>, nonbreaking spaces are not normalized out of the markup, even for `xml:space="default"`.</span></span> <span data-ttu-id="541ff-137">(Aby uzyskać więcej informacji, zobacz [przetwarzanie spacji w XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)</span><span class="sxs-lookup"><span data-stu-id="541ff-137">(For more information, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)</span></span>|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a><span data-ttu-id="541ff-138">Format komentarza XML</span><span class="sxs-lookup"><span data-stu-id="541ff-138">XML Comment Format</span></span>  
 <span data-ttu-id="541ff-139">XAML używa formatu komentarza XML: uruchomienia komentarza to `<!--`, jest końca komentarza `-->,` oraz sekwencję `--` nie mogą występować w komentarz.</span><span class="sxs-lookup"><span data-stu-id="541ff-139">XAML uses the XML comment format: the start of the comment is `<!--`, the end of comment is `-->,` and the sequence `--` must not occur within the comment.</span></span>  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a><span data-ttu-id="541ff-140">Instrukcji przetwarzania XML</span><span class="sxs-lookup"><span data-stu-id="541ff-140">XML Processing Instructions</span></span>  
 <span data-ttu-id="541ff-141">XAML obsługuje instrukcji przetwarzania XML zgodnie ze specyfikacją określoną XML, co oznacza, że instrukcje muszą być przekazywane za pośrednictwem.</span><span class="sxs-lookup"><span data-stu-id="541ff-141">XAML handles XML processing instructions according to XML specifications, which state that the instructions must be passed through.</span></span> <span data-ttu-id="541ff-142">Przetwarzanie w usługi XAML .NET Framework XAML nie używa żadnych instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="541ff-142">XAML processing in .NET Framework XAML Services  does not use any processing instructions.</span></span> <span data-ttu-id="541ff-143">Innych istniejących struktur, korzystających z języka XAML również należy używać instrukcji przetwarzania XAML.</span><span class="sxs-lookup"><span data-stu-id="541ff-143">Other existing frameworks that use XAML also do not use processing instructions from XAML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="541ff-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="541ff-144">See Also</span></span>  
 [<span data-ttu-id="541ff-145">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="541ff-145">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="541ff-146">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="541ff-146">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="541ff-147">Xamlname — gramatyka</span><span class="sxs-lookup"><span data-stu-id="541ff-147">XamlName Grammar</span></span>](../../../docs/framework/xaml-services/xamlname-grammar.md)  
 [<span data-ttu-id="541ff-148">Przetwarzanie spacji w XAML</span><span class="sxs-lookup"><span data-stu-id="541ff-148">Whitespace Processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
