---
title: 'Instrukcje: Osadzanie wyrażeń w literałach XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 9d0fd1e3713dc5b81cfca0ce54b571b38e648f87
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879109"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Instrukcje: Osadzanie wyrażeń w literałach XML (Visual Basic)
Literały XML można połączyć z wyrażenia osadzone, aby utworzyć dokumentu XML, fragment lub element, który zawiera zawartość tworzony w czasie wykonywania. W poniższych przykładach pokazano sposób użycia wyrażenia osadzone w celu wypełnienia zawartości elementu i atrybuty nazwy elementów w czasie wykonywania.  
  
 Składnia wyrażenia osadzone jest `<%=` `exp` `%>`, który jest w tej samej składni, która korzysta z platformy ASP.NET. Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Można również użyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsów API, aby utworzyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-insert-text-as-element-content"></a>Aby wstawić tekst jako element zawartości  
  
- Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w `contactName` zmiennej między elementami nazwa otwierający i zamykający.  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     Ten przykład generuje następujące wyniki:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Aby wstawić tekst jako wartość atrybutu  
  
- Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w `phoneType` zmiennej jako wartości `type` atrybutu.  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     Ten przykład generuje następujące wyniki:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Aby wstawić tekst dla nazwy elementu  
  
- Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w `elementName` zmiennej jako nazwę elementu.  
  
     Podczas tworzenia elementów za pomocą tej techniki, należy zamknąć je za pomocą \</ > tag.  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     Ten przykład generuje następujące wyniki:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie literałów XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [Wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
