---
title: 'Porady: osadzanie wyrażeń w literałach XML'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 59ba03be6e132203523427d3b7af5a163b6f05ac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392317"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Porady: osadzanie wyrażeń w literałach XML (Visual Basic)
Literały XML można łączyć z osadzonymi wyrażeniami w celu utworzenia dokumentu XML, fragmentu lub elementu zawierającego zawartość utworzoną w czasie wykonywania. W poniższych przykładach pokazano, jak używać osadzonych wyrażeń do wypełniania zawartości elementu, atrybutów i nazw elementów w czasie wykonywania.  
  
 Składnia wyrażenia osadzonego ma tę `<%=` `exp` `%>` samą składnię, która ASP.NET używa. Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](embedded-expressions-in-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Do tworzenia obiektów można także używać interfejsów API [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-insert-text-as-element-content"></a>Aby wstawić tekst jako zawartość elementu  
  
- Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w `contactName` zmiennej między otwierającą i zamykającą nazwą.  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     Ten przykład generuje następujące wyniki:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Aby wstawić tekst jako wartość atrybutu  
  
- Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w `phoneType` zmiennej jako wartość `type` atrybutu.  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     Ten przykład generuje następujące wyniki:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Aby wstawić tekst dla nazwy elementu  
  
- Poniższy przykład pokazuje, jak wstawić tekst, który jest zawarty w `elementName` zmiennej jako nazwę elementu.  
  
     Podczas tworzenia elementów za pomocą tej techniki należy zamknąć je za pomocą \</> znacznika.  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     Ten przykład generuje następujące wyniki:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie literałów XML](how-to-create-xml-literals.md)
- [Wyrażenia osadzone w XML](embedded-expressions-in-xml.md)
- [Tworzenie XML w Visual Basic](creating-xml.md)
- [XML](index.md)
