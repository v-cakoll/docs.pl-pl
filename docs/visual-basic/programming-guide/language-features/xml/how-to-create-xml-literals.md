---
title: 'Instrukcje: Tworzenie literałów XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: c79b607f9ce5c779539b7700feafb7d4e3d67d24
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974253"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Instrukcje: Tworzenie literałów XML (Visual Basic)
Można utworzyć dokumentu XML, fragment lub element bezpośrednio w kodzie za pomocą literał XML. Przykłady w tym temacie pokazują, jak utworzyć element XML, który ma trzy elementy podrzędne i tworzenie dokumentu XML.  
  
 Można również użyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsów API, aby utworzyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>Aby utworzyć XML element  
  
-   Utwórz w tekście XML przy użyciu składni literał XML, która jest taka sama jak rzeczywista składni XML.  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     Uruchom kod. Wynik tego kodu jest:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Aby utworzyć dokumentu XML  
  
-   Utwórz w tekście dokumentu XML. Poniższy kod tworzy dokument XML, który ma składni literału, deklaracja XML, instrukcję przetwarzania, komentarz i element, który zawiera inny element.  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     Uruchom kod. Wynik tego kodu jest:  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Zobacz także
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
