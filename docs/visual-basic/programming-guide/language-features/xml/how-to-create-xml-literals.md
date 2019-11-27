---
title: 'Porady: tworzenie literałów XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: e3af5185d2c2106e6a696a6569ef59897d0f1fe1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333001"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Porady: tworzenie literałów XML (Visual Basic)
Można utworzyć dokument XML, fragment lub element bezpośrednio w kodzie przy użyciu literału XML. W przykładach w tym temacie pokazano, jak utworzyć element XML z trzema elementami podrzędnymi i jak utworzyć dokument XML.  
  
 Można również użyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsów API do tworzenia obiektów [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Aby uzyskać więcej informacji, zobacz temat <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>Aby utworzyć element XML  
  
- Utwórz kod XML w tekście przy użyciu składni literału XML, która jest taka sama jak rzeczywista składnia XML.  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     Uruchom kod. Dane wyjściowe tego kodu są następujące:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Aby utworzyć dokument XML  
  
- Utwórz wiersz dokumentu XML. Poniższy kod tworzy dokument XML, który ma składnię literału, deklarację XML, instrukcję przetwarzania, komentarz i element, który zawiera inny element.  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     Uruchom kod. Dane wyjściowe tego kodu są następujące:  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Zobacz także

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Tworzenie kodu XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
