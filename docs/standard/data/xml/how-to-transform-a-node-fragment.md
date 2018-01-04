---
title: "Porady: Przekształcanie fragmentu węzła"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2b85bcbf537f5306b0b4c30630523eaf511dd3d9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-transform-a-node-fragment"></a>Porady: Przekształcanie fragmentu węzła
Gdy przekształcenie danych zawartych w <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument> obiektów przekształceń XSLT stosowane do całego dokumentu. Innymi słowy w przypadku przekazania w węźle innym niż węzeł główny dokumentu, to nie zapobiega proces przekształcania podczas uzyskiwania dostępu do wszystkich węzłów w załadowanego dokumentu. Aby przekształcić fragmentu węzła, należy utworzyć oddzielny obiekt zawierający tylko fragmentu węzeł i przekazać do obiektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-transform-a-node-fragment"></a>Aby przekształcić fragmentu węzła  
  
1.  Utwórz obiekt zawierający dokumentu źródłowego.  
  
2.  Zlokalizuj fragmentu węzła, który ma zostać transformacji.  
  
3.  Należy utworzyć oddzielny obiekt z właśnie fragmentu węzła.  
  
4.  Fragment węzła do przekazania <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przekształca fragmentu węzła i umieszcza wyniki w konsoli.  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>Dane wejściowe  
  
##### <a name="booksxml"></a>Books.XML  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>Single.xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Dane wyjściowe  
 Tytuł książki jest Man. zaufania  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
