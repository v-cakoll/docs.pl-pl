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
ms.openlocfilehash: 5ef489498cdc8716f7599124138f9ecf8945ac9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564776"
---
# <a name="xml-character-entities-and-xaml"></a>Jednostki znaków XML i XAML
XAML używa jednostki znaków zdefiniowane w pliku XML dla znaków specjalnych. W tym temacie opisano niektóre jednostki określonych znaków i Ogólne zagadnienia dotyczące innych koncepcji XML w języku XAML.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Jednostki znaków i anulowanie problemy, które są unikatowe dla XAML  
 Kod znaczników XAML zwykle korzysta z tej samej jednostki znaków i sekwencji unikowych, które są zdefiniowane w pliku XML.  
  
 Głównego wyjątek to, że nawiasy klamrowe ({i}) ma znaczenie w języku XAML, ponieważ te znaki informuje procesora XAML, czy sekwencja znaków w nawiasach klamrowych musi być interpretowane jako rozszerzenie znaczników. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników dla przeglądu XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
 Jednakże nadal można wyświetlić nawiasy klamrowe jako literały przy użyciu sekwencji unikowej specyficznych dla języka XAML, a nie XML. Aby uzyskać więcej informacji, zobacz [ {} sekwencja ucieczki — rozszerzenie znaczników](escape-sequence-markup-extension.md).  
  
 Należy pamiętać, że ukośnik odwrotny (\\) nie wymaga sekwencji unikowej, gdy jest on traktowany jako ciąg.  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>Jednostki znaków XML  
 Jak wspomniano wcześniej, większość jednostki znaków i sekwencji unikowych, które są zazwyczaj używane do zapisania znaczników XAML są definiowane przez XML. Ten temat nie zawiera pełną listę tych jednostek; szczegółowe odwołania dla jednostek znajduje się w dokumentacji zewnętrznych, takich jak w specyfikacji XML. Jednak dla wygody, w tym temacie przedstawiono określonej jednostki znaków XML, które są zazwyczaj używane w kodzie XAML.  
  
|Znak|Jednostka|Uwagi|  
|---------------|------------|-----------|  
|& (znak handlowe „i”)|\&amp;|Musi być używany dla wartości atrybutów i zawartości elementu.|  
|> (większe-niż znak)|\&gt;|Dla wartości atrybutu muszą być używane, ale > jest akceptowany w zawartości elementu tak długo, jak < nie poprzedza.|  
|< (mniej-niż znak)|\&lt;|Dla wartości atrybutu muszą być używane, ale \< jest akceptowany w zawartości elementu tak długo, jak > nie jest zgodna.|  
|"(proste cudzysłów)|\&quot;|Dla wartości atrybutu muszą być używane, ale proste znak cudzysłowu (") jest akceptowany w zawartości elementu. Należy pamiętać, że wartości atrybutu może być ujęte proste znak pojedynczego cudzysłowu (') lub proste znak cudzysłowu ("); występuje jako pierwszy znak niezależnie od definiuje obudowa wartość atrybutu i alternatywne oferty mogą następnie służyć jako literał w wartości.|  
|"(proste cudzysłów pojedynczy)|\&APOS;|Dla wartości atrybutu muszą być używane, ale proste znak pojedynczego cudzysłowu (') jest akceptowany w zawartości elementu. Należy pamiętać, że wartości atrybutu może być ujęte proste znak pojedynczego cudzysłowu (') lub proste znak cudzysłowu ("); występuje jako pierwszy znak niezależnie od definiuje obudowa wartość atrybutu i alternatywne oferty mogą następnie służyć jako literał w wartości.|  
|(znaku numerycznego mapowania)|&#*[liczba całkowita]* ; lub & #x *[szesnastkowych]*;|XAML obsługuje mapowania znaku numerycznego do kodowania, które jest aktywny.|  
|(nierozdzielających miejsca)|&\#160; (przy założeniu, kodowania UTF-8)|Dla elementów dokumentu przepływu i elementy, które tekstu, takich jak WPF <xref:System.Windows.Controls.TextBox>, spacji nierozdzielających nie są znormalizować poza znaczników, nawet w przypadku `xml:space="default"`. (Aby uzyskać więcej informacji, zobacz [przetwarzanie spacji w XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>Format komentarza XML  
 XAML używa formatu komentarza XML: uruchomienia komentarza to `<!--`, jest końca komentarza `-->,` oraz sekwencję `--` nie mogą występować w komentarz.  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>Instrukcji przetwarzania XML  
 XAML obsługuje instrukcji przetwarzania XML zgodnie ze specyfikacją określoną XML, co oznacza, że instrukcje muszą być przekazywane za pośrednictwem. Przetwarzanie w usługi XAML .NET Framework XAML nie używa żadnych instrukcji przetwarzania. Innych istniejących struktur, korzystających z języka XAML również należy używać instrukcji przetwarzania XAML.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [XamlName, gramatyka](../../../docs/framework/xaml-services/xamlname-grammar.md)  
 [Przetwarzanie spacji w XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
