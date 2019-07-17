---
title: Jednostki znaków XML i XAML
ms.date: 03/30/2017
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
ms.openlocfilehash: b4621da21200e6c9e2b174a0e2ba508a4f6bab92
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938713"
---
# <a name="xml-character-entities-and-xaml"></a>Jednostki znaków XML i XAML
XAML używa encje znaków zdefiniowanych w pliku XML dla znaków specjalnych. W tym temacie opisano niektóre jednostki określonych znaków i ogólne uwagi dotyczące innych pojęć XML w XAML.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Jednostki znaków i anulowania zapewnianego element problemy, które są unikatowe dla XAML  
 XAML znaczników są zazwyczaj używa tej samej jednostki znaków i sekwencje unikowe, które są zdefiniowane w pliku XML.  
  
 Najważniejszym wyjątkiem jest, że nawiasy klamrowe ({i}) ma znaczenie w XAML, ponieważ te znaki informuje procesora XAML, że sekwencji znaków w nawiasach klamrowych musi być interpretowany jako rozszerzenie znaczników. Aby uzyskać więcej informacji na temat rozszerzenia znaczników, zobacz [rozszerzenia znaczników dla przeglądu XAML](markup-extensions-for-xaml-overview.md).  
  
 Jednak nadal można wyświetlić nawiasy klamrowe jako znaki literału przy użyciu sekwencji unikowej specyficznych dla XAML, a nie XML. Aby uzyskać więcej informacji, zobacz [ {} sekwencja ucieczki — rozszerzenie znaczników](escape-sequence-markup-extension.md).  
  
 Należy pamiętać, że ukośnik odwrotny (\\) nie wymaga sekwencji ucieczki, gdy jest on traktowany jako ciąg.  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>Jednostki znaków XML  
 Jak już wspomniano, większość encje znaków i sekwencje unikowe, które są zazwyczaj używane do pisania XAML znaczników są definiowane przez XML. Ten temat nie zawiera pełną listę tych jednostek; szczegółową dokumentację dla jednostek można znaleźć w dokumentacji zewnętrznych, takich jak, w specyfikacji XML. Jednak dla wygody w tym temacie przedstawiono niektóre określone jednostki znaków XML, które są zwykle używane w znaczniku XAML.  
  
|Znak|Jednostka|Uwagi|  
|---------------|------------|-----------|  
|& (znak)|\&amp;|Należy użyć wartości atrybutów i zawartości elementu.|  
|> (większą-niż znak)|\&gt;|Musi być używany dla wartości atrybutu, ale > jest akceptowany w zawartości elementu tak długo, jak < nie należy poprzedzić go.|  
|< (mniej-niż znak)|\&lt;|Musi być używany dla wartości atrybutu, ale \< jest akceptowany w zawartości elementu tak długo, jak > nie wykonać.|  
|"(prosty cudzysłów)|\&quot;|Musi być używany dla wartości atrybutu, ale prosty cudzysłów (") jest akceptowany w zawartości elementu. Należy pamiętać, że wartości atrybutu mogą być ujęte w prostej znak pojedynczego cudzysłowu (') lub bezpośrednio znak cudzysłowu ("); niezależnie od znaku występuje jako pierwszy definiuje obudowy wartość atrybutu i alternatywne oferty mogą posłużyć jako literał w wartości.|  
|"(prosty cudzysłów pojedynczy)|\&APOS;|Musi być używany dla wartości atrybutu, ale proste znak pojedynczego cudzysłowu (') jest akceptowany w zawartości elementu. Należy pamiętać, że wartości atrybutu mogą być ujęte w prostej znak pojedynczego cudzysłowu (') lub bezpośrednio znak cudzysłowu ("); niezależnie od znaku występuje jako pierwszy definiuje obudowy wartość atrybutu i alternatywne oferty mogą posłużyć jako literał w wartości.|  
|(znak numeryczny mapowania)|&# *[liczba całkowita]* ; lub &#x *[szesnastkowy]* ;|XAML obsługuje mapowania cyfrę do kodowania, które jest aktywny.|  
|(spacja nierozdzielająca)|&\#160; (przy założeniu, kodowanie UTF-8)|Dla elementów dokumentu przepływu lub elementy, które przyjmują tekstu, takich jak WPF <xref:System.Windows.Controls.TextBox>, spacji nierozdzielających nie są znormalizowane poza znaczników, nawet w przypadku `xml:space="default"`. (Aby uzyskać więcej informacji, zobacz [spacji w XAML na przetworzenie](whitespace-processing-in-xaml.md).)|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>Format komentarza XML  
 XAML w formacie XML komentarz: Początek komentarza jest `<!--`, koniec komentarza jest `-->,` i sekwencji `--` nie może wystąpić w komentarzu.  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>Instrukcje przetwarzania XML  
 XAML obsługuje instrukcji przetwarzania XML według specyfikacji XML, co oznacza, że instrukcje muszą być przekazywane za pośrednictwem. Przetwarzanie w .NET Framework XAML Services XAML nie korzysta z żadnych instrukcji przetwarzania. Inne istniejącymi strukturami, które używają XAML również należy używać instrukcji przetwarzania z XAML.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Rozszerzenia znaczników i WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [XamlName, gramatyka](xamlname-grammar.md)
- [Znak odstępu przetwarzanie w XAML](whitespace-processing-in-xaml.md)
