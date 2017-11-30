---
title: "Porady: ładowanie XML z pliku, ciągu lub strumienia (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 572e34b1cd4813fad35e6afaf2ec3d0d9dac470a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a>Porady: ładowanie XML z pliku, ciągu lub strumienia (Visual Basic)
Można utworzyć [literałów XML](../../../../visual-basic/language-reference/xml-literals/index.md) i wypełnić je przy użyciu zawartości ze źródła zewnętrznego, takich jak pliku, ciągu lub strumienia za pomocą kilku metod. W poniższych przykładach przedstawiono tych metod.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a>Aby załadować z pliku XML  
  
-   Aby wypełnić literału, takich jak XML <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt z pliku, użyj `Load` metody. Ta metoda może zająć ścieżka do pliku, strumienia tekstu lub strumień XML jako dane wejściowe.  
  
     W poniższym przykładzie pokazano sposób użycia <xref:System.Xml.Linq.XDocument.Load%28System.String%29> metodę, aby wypełnić <xref:System.Xml.Linq.XDocument> obiektu XML z pliku tekstowego.  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a>Ładowanie XML z ciągu  
  
-   Aby wypełnić literału, takich jak XML <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt z ciągu, można użyć `Parse` metody.  
  
     W poniższym przykładzie pokazano sposób użycia <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> metodę, aby wypełnić <xref:System.Xml.Linq.XDocument> obiektu XML z ciągu.  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a>Aby załadować XML ze strumienia  
  
-   Aby wypełnić literału, takich jak XML <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektu strumienia, można użyć `Load` — metoda lub <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> — metoda.  
  
 W poniższym przykładzie pokazano sposób użycia <xref:System.Xml.Linq.XNode.ReadFrom%2A> metodę, aby wypełnić <xref:System.Xml.Linq.XDocument> obiektu XML ze strumienia XML.  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>  
 [Literały XML](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
