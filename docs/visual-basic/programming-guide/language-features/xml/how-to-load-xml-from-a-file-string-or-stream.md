---
title: 'Porady: ładowanie XML z pliku, ciągu lub strumienia'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 7f2a961ebb7ecd4fc0512e141b4a437be87bec0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392291"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Porady: ładowanie XML z pliku, ciągu lub strumienia (Visual Basic)

Można tworzyć [literały XML](../../../language-reference/xml-literals/index.md) i wypełniać je zawartością z zewnętrznego źródła, takiego jak plik, ciąg lub strumień, przy użyciu kilku metod. Te metody przedstawiono w poniższych przykładach.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a>Aby załadować plik XML z pliku

Aby wypełnić literał XML, taki jak <xref:System.Xml.Linq.XElement> obiekt lub <xref:System.Xml.Linq.XDocument> z pliku, należy użyć `Load` metody. Ta metoda może przyjmować ścieżkę pliku, strumień tekstowy lub strumień XML jako dane wejściowe.

Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metody do wypełniania <xref:System.Xml.Linq.XDocument> obiektu atrybutem XML z pliku tekstowego.

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a>Aby załadować XML z ciągu

Aby wypełnić literał XML, taki jak <xref:System.Xml.Linq.XElement> obiekt lub <xref:System.Xml.Linq.XDocument> z ciągu, można użyć `Parse` metody.

Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metody do wypełniania <xref:System.Xml.Linq.XDocument> obiektu atrybutem XML z ciągu.

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a>Aby załadować plik XML ze strumienia

Aby wypełnić literał XML, taki jak <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt ze strumienia, można użyć `Load` metody lub <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> metody.

Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody do wypełnienia <xref:System.Xml.Linq.XDocument> obiektu z XML ze strumienia XML.

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [Literały XML](../../../language-reference/xml-literals/index.md)
- [XML](index.md)
- [Manipulowanie XML w Visual Basic](manipulating-xml.md)
