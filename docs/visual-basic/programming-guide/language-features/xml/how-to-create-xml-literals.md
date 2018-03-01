---
title: "Porady: tworzenie literałów XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce1bf763529b436158c2d74811c4938182166f92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Porady: tworzenie literałów XML (Visual Basic)
Można utworzyć dokumentu XML, fragment lub element bezpośrednio w kodzie za pomocą literału XML. Przykłady w tym temacie przedstawiają, jak utworzyć element XML, który ma trzy elementy podrzędne oraz sposobu tworzenia dokumentu XML.  
  
 Można również użyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsów API, aby utworzyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>Aby utworzyć XML element  
  
-   Utwórz tekście XML przy użyciu składni literału XML, która jest taka sama jak rzeczywista składni XML.  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     Uruchom kod. Wynik tego kodu jest:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Aby utworzyć dokumentu XML  
  
-   Utworzyć wbudowane dokumentu XML. Poniższy kod tworzy składni literału, deklaracja XML, instrukcji przetwarzania, komentarz i element, który zawiera inny element dokumentu XML.  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     Uruchom kod. Wynik tego kodu jest:  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Zobacz też  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
