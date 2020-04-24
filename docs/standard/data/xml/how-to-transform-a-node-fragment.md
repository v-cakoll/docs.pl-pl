---
title: 'Instrukcje: Przekształcanie fragmentu węzła'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: 56e9ef6031a5736acfa066ed6c068f954bd5af8d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710820"
---
# <a name="how-to-transform-a-node-fragment"></a>Instrukcje: Przekształcanie fragmentu węzła
Gdy przekształcasz dane zawarte w obiekcie <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument> , przekształcenia XSLT mają zastosowanie do dokumentu jako całości. Innymi słowy, jeśli przejdziesz do węzła innego niż węzeł główny dokumentu, nie uniemożliwi to proces przekształcania uzyskuje dostęp do wszystkich węzłów w załadowanym dokumencie. Aby przekształcić fragment węzła, należy utworzyć oddzielny obiekt zawierający tylko fragment węzła i przekazać ten obiekt do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-transform-a-node-fragment"></a>Aby przekształcić fragment węzła  
  
1. Utwórz obiekt zawierający dokument źródłowy.  
  
2. Znajdź fragment węzła, który chcesz przekształcić.  
  
3. Utwórz oddzielny obiekt za pomocą tylko fragmentu węzła.  
  
4. Przekaż fragment węzła do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przekształca fragment węzła i wyświetla wyniki w konsoli programu.  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>Dane wejściowe  
  
##### <a name="booksxml"></a>Books. XML  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>Single. xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Dane wyjściowe  
 Tytuł książki to człowiek z zaufaniem.  
  
## <a name="see-also"></a>Zobacz też

- [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
