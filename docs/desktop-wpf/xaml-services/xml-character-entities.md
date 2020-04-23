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
ms.openlocfilehash: aff96c5d0ee6bbf2bbe2f9e3b3ae091caa781f7a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071459"
---
# <a name="xml-character-entities-and-xaml"></a>Jednostki znaków XML i XAML

XAML używa jednostek znaków zdefiniowanych w języku XML dla znaków specjalnych. W tym temacie opisano niektóre określone jednostki znaków i ogólne zagadnienia dotyczące innych pojęć XML w języku XAML.

## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Jednostki znaków i problemy ucieczki, które są unikatowe dla XAML

Znaczniki XAML zazwyczaj używają tych samych jednostek znaków i sekwencji unikowych, które są zdefiniowane w języku XML.

Głównym wyjątkiem jest to, że nawiasy klamrowe ({ i }) mają znaczenie w języku XAML, ponieważ znaki te informują procesor XAML, że sekwencja znaków ujęta w nawiasy klamrowe musi być interpretowana jako rozszerzenie znaczników. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [Rozszerzenia znaczników dla XAML Overview](markup-extensions-overview.md).

Jednak nadal można wyświetlać nawiasy klamrowe jako znaki dosłowne przy użyciu sekwencji unikowej, która jest określona dla XAML zamiast XML. Aby uzyskać więcej informacji, zobacz [ {} Sekwencja ucieczki - Rozszerzenie znaczników](escape-sequence-markup-extension.md).

Należy zauważyć, że\\ukośnik odwrotny ( ) nie wymaga sekwencji ucieczki, gdy jest obsługiwany jako ciąg.

## <a name="xml-character-entities"></a>Jednostki znaków XML

Jak wspomniano wcześniej, większość jednostek znaków i sekwencji ucieczki, które są zwykle używane do pisania znaczników XAML są definiowane przez XML. Ten temat nie zawiera pełnej listy tych jednostek; szczegółowe informacje na temat jednostek można znaleźć w dokumentacji zewnętrznej, takiej jak specyfikacje XML. Jednak dla wygody w tym temacie wymieniono niektóre określone jednostki znaków XML, które są zwykle używane w znacznikach XAML.

|Znak|Jednostka|Uwagi|
|---------------|------------|-----------|
|& (znak)|\&wzmacniacz;|Musi być używany zarówno dla wartości atrybutów, jak i dla zawartości elementu.|
|> (więcej niż znak)|\&gt;|Musi być używany dla wartości atrybutu, ale > jest dopuszczalne, jak zawartość elementu, o ile < nie poprzedza go.|
|< (mniej niż znak)|\&lt;|Musi być używany dla wartości \< atrybutu, ale jest dopuszczalne, jak zawartość elementu, tak długo, jak > nie jest zgodna z nim.|
|" (prosty cudzysłów)|\&quot;|Musi być używany dla wartości atrybutu, ale prosty cudzysłów (") jest dopuszczalne jako zawartość elementu. Należy zauważyć, że wartości atrybutów mogą być ujęte w pojedynczy prosty cudzysłów (') lub przez prosty cudzysłów ("); Niezależnie od tego, który znak pojawia się najpierw definiuje obudowy wartości atrybutu, a alternatywny cudzysłów może być następnie używany jako literał w wartości.|
|' (pojedynczy prosty cudzysłów)|\&apos;|Musi być używany dla wartości atrybutu, ale pojedynczy prosty cudzysłów (') jest dopuszczalne jako zawartość elementu. Należy zauważyć, że wartości atrybutów mogą być ujęte w pojedynczy prosty cudzysłów (') lub przez prosty cudzysłów ("); Niezależnie od tego, który znak pojawia się najpierw definiuje obudowy wartości atrybutu, a alternatywny cudzysłów może być następnie używany jako literał w wartości.|
|(mapowania znaków liczbowych)|&#*[całkowita]*; lub &#x *[hex]*;|XAML obsługuje mapowania znaków numerycznych do kodowania, który jest aktywny.|
|(przestrzeń nierozdzielająca)|&\#160; (przy założeniu, że kodowanie UTF-8)|W przypadku elementów dokumentu przepływu lub elementów, które przyjmują tekst, takich jak <xref:System.Windows.Controls.TextBox>WPF, `xml:space="default"`spacje nierozdzielające nie są znormalizowane z znaczników, nawet dla . (Aby uzyskać więcej informacji, zobacz [Przetwarzanie odstępów w języku XAML.)](white-space-processing.md)|

## <a name="xml-comment-format"></a>Format komentarza XML

XAML używa formatu komentarza XML: początek `<!--`komentarza jest , `-->,` koniec komentarza `--` jest i sekwencji nie może wystąpić w komentarzu.

## <a name="xml-processing-instructions"></a>Instrukcje przetwarzania XML

XAML obsługuje instrukcje przetwarzania XML zgodnie ze specyfikacjami XML, które określają, że instrukcje muszą być przekazywane. Przetwarzanie XAML w usługach .NET XAML nie korzysta z żadnych instrukcji przetwarzania. Inne istniejące struktury, które używają XAML również nie używać instrukcji przetwarzania z XAML.

## <a name="see-also"></a>Zobacz też

- [Omówienie XAML (WPF)](../fundamentals/xaml.md)
- [Rozszerzenia znacznikowania i WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [XamlName — Gramatyka](xamlname-grammar.md)
- [Przetwarzanie spacji w XAML](white-space-processing.md)
