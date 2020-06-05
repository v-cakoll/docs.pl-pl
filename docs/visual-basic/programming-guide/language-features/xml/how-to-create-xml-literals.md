---
title: 'Porady: tworzenie literałów XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 61b138c0851c747ed30eedc10cb882cc3b03c4d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392613"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Porady: tworzenie literałów XML (Visual Basic)
Można utworzyć dokument XML, fragment lub element bezpośrednio w kodzie przy użyciu literału XML. W przykładach w tym temacie pokazano, jak utworzyć element XML z trzema elementami podrzędnymi i jak utworzyć dokument XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Do tworzenia obiektów można także używać interfejsów API [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [XML](index.md)
- [Tworzenie XML w Visual Basic](creating-xml.md)
- [Literał elementu XML](../../../language-reference/xml-literals/xml-element-literal.md)
- [Literał dokumentu XML](../../../language-reference/xml-literals/xml-document-literal.md)
