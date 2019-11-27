---
title: 'Porady: osadzanie wyrażeń w literałach XML'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 2e8dd10b334b0271e3c9de11ed155c9d5d7aae48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332940"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Porady: osadzanie wyrażeń w literałach XML (Visual Basic)
Literały XML można łączyć z osadzonymi wyrażeniami w celu utworzenia dokumentu XML, fragmentu lub elementu zawierającego zawartość utworzoną w czasie wykonywania. W poniższych przykładach pokazano, jak używać osadzonych wyrażeń do wypełniania zawartości elementu, atrybutów i nazw elementów w czasie wykonywania.  
  
 Składnia wyrażenia osadzonego jest `<%=` `exp` `%>`, która jest tą samą składnią, która ASP.NET używa. Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Można również użyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsów API do tworzenia obiektów [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-insert-text-as-element-content"></a>Aby wstawić tekst jako zawartość elementu  
  
- Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w zmiennej `contactName` między otwierającymi i zamykającymi elementami nazw.  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     Ten przykład generuje następujące wyniki:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Aby wstawić tekst jako wartość atrybutu  
  
- Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w zmiennej `phoneType` jako wartość atrybutu `type`.  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     Ten przykład generuje następujące wyniki:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Aby wstawić tekst dla nazwy elementu  
  
- Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w zmiennej `elementName` jako nazwę elementu.  
  
     Podczas tworzenia elementów za pomocą tej techniki należy zamknąć je za pomocą tagu \</>.  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     Ten przykład generuje następujące wyniki:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: tworzenie literałów XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [Wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Tworzenie kodu XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
