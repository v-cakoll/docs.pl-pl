---
title: 'Porady: ładowanie XML z pliku, ciągu lub strumienia'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7a2a0513a066ae8ea8a70f7a5ae340ab29de7d25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330959"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Porady: ładowanie XML z pliku, ciągu lub strumienia (Visual Basic)

Można tworzyć [literały XML](../../../../visual-basic/language-reference/xml-literals/index.md) i wypełniać je zawartością z zewnętrznego źródła, takiego jak plik, ciąg lub strumień, przy użyciu kilku metod. Te metody przedstawiono w poniższych przykładach.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>Aby załadować plik XML z pliku

Aby wypełnić literał XML, taki jak obiekt <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> z pliku, należy użyć metody `Load`. Ta metoda może przyjmować ścieżkę pliku, strumień tekstowy lub strumień XML jako dane wejściowe.

Poniższy przykład kodu pokazuje użycie metody <xref:System.Xml.Linq.XDocument.Load%28System.String%29> do wypełnienia obiektu <xref:System.Xml.Linq.XDocument> z XML z pliku tekstowego.

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>Aby załadować XML z ciągu

Aby wypełnić literał XML, taki jak obiekt <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> z ciągu, można użyć metody `Parse`.

Poniższy przykład kodu pokazuje użycie metody <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType>, aby wypełnić obiekt <xref:System.Xml.Linq.XDocument> z XML z ciągu.

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>Aby załadować plik XML ze strumienia

Aby wypełnić literał XML, taki jak obiekt <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> ze strumienia, można użyć metody `Load` lub metody <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>.

Poniższy przykład kodu pokazuje użycie metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> do wypełnienia obiektu <xref:System.Xml.Linq.XDocument> z XML ze strumienia XML.

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
