---
title: 'Instrukcje: Ładowanie XML z pliku, ciągu lub strumienia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: ba88ae19abc216a318d6c2069ab0846d5db8a346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054165"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Instrukcje: Ładowanie XML z pliku, ciągu lub strumienia (Visual Basic)

Można tworzyć [literały XML](../../../../visual-basic/language-reference/xml-literals/index.md) i wypełniać je zawartością z zewnętrznego źródła, takiego jak plik, ciąg lub strumień, przy użyciu kilku metod. Te metody przedstawiono w poniższych przykładach.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>Aby załadować plik XML z pliku

Aby wypełnić literał XML, taki jak <xref:System.Xml.Linq.XElement> obiekt lub <xref:System.Xml.Linq.XDocument> z pliku, należy użyć `Load` metody. Ta metoda może przyjmować ścieżkę pliku, strumień tekstowy lub strumień XML jako dane wejściowe.

Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metody do <xref:System.Xml.Linq.XDocument> wypełniania obiektu atrybutem XML z pliku tekstowego.

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>Aby załadować XML z ciągu

Aby wypełnić literał XML <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> , taki jak obiekt lub z ciągu, można użyć metody.`Parse`

Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metody do <xref:System.Xml.Linq.XDocument> wypełniania obiektu atrybutem XML z ciągu.

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>Aby załadować plik XML ze strumienia

<xref:System.Xml.Linq.XElement> Aby wypełnić literał XML <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> , taki jak lub obiekt ze strumienia, można użyć metodylubmetody.`Load`

Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody do <xref:System.Xml.Linq.XDocument> wypełnienia obiektu z XML ze strumienia XML.

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [Literały XML](../../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
