---
title: 'Instrukcje: Ładowanie kodu XML z pliku, ciągu lub Stream (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 36a7f23eed7f47e8c33958f96e8e3694fb958d11
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977698"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Instrukcje: Ładowanie kodu XML z pliku, ciągu lub Stream (Visual Basic)
Możesz utworzyć [literałów XML](../../../../visual-basic/language-reference/xml-literals/index.md) i wypełnić je przy użyciu zawartości ze źródła zewnętrznego pliku, ciągu lub strumienia za pomocą kilku metod. W poniższych przykładach przedstawiono te metody.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a>Aby załadować XML z pliku  
  
-   Aby wypełnić literał, takich jak XML <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt z pliku, użyj `Load` metody. Ta metoda może potrwać ścieżka do pliku, strumienia tekstu lub strumienia XML jako dane wejściowe.  
  
     Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metodę, aby wypełnić <xref:System.Xml.Linq.XDocument> obiektu z danymi XML z pliku tekstowego.  
  
     [!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]  
  
### <a name="to-load-xml-from-a-string"></a>Aby załadować XML z ciągu  
  
-   Aby wypełnić literał, takich jak XML <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt z ciągu, można użyć `Parse` metody.  
  
     Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metodę, aby wypełnić <xref:System.Xml.Linq.XDocument> obiektu z danymi XML z ciągu.  
  
     [!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]  
  
### <a name="to-load-xml-from-a-stream"></a>Aby załadować XML ze strumienia  
  
-   Do wypełniania literał, takich jak XML <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektów ze strumienia, możesz użyć `Load` metody lub <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> metody.  
  
 Poniższy przykład kodu pokazuje użycie <xref:System.Xml.Linq.XNode.ReadFrom%2A> metodę, aby wypełnić <xref:System.Xml.Linq.XDocument> obiektu z danymi XML ze strumienia XML.  
  
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
