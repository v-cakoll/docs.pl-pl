---
title: "Porady: osadzanie wyrażeń w literałach XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bef4662d69ca7ceddeb2641cbe265d93712c5d16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Porady: osadzanie wyrażeń w literałach XML (Visual Basic)
Literały XML można łączyć z wyrażenia osadzone, aby utworzyć dokumentu XML, fragment lub element zawartości utworzona w czasie wykonywania. W poniższych przykładach pokazano, jak używać wyrażenia osadzone do wypełniania elementu zawartości, atrybuty i nazwy elementów w czasie wykonywania.  
  
 Składnia wyrażenia osadzonego jest `<%=` `exp` `%>`, która jest taka sama składnia który [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] używa. Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Można również użyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsów API, aby utworzyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-insert-text-as-element-content"></a>Aby wstawić tekst jako element zawartości  
  
-   Poniższy przykład przedstawia sposób wstawić tekst, który jest zawarty w `contactName` zmiennej między elementami nazwa otwierający i zamykający.  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     Ten przykład generuje następujące wyniki:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Aby wstawić tekst jako wartość atrybutu  
  
-   Poniższy przykład przedstawia sposób wstawić tekst, który znajduje się w `phoneType` zmiennej jako wartości `type` atrybutu.  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     Ten przykład generuje następujące wyniki:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Aby wstawić tekst dla nazwy elementu  
  
-   Poniższy przykład przedstawia sposób wstawić tekst, który jest zawarty w `elementName` zmiennej jako nazwa elementu.  
  
     Podczas tworzenia elementów za pomocą tej metody, należy zamknąć je za pomocą \</ > tagu.  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     Ten przykład generuje następujące wyniki:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: tworzenie literałów XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)  
 [Wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
