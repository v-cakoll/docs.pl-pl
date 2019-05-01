---
title: 'Instrukcje: Przekształcanie fragmentu węzła'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fabf7983a1887fb318bfb8d111b3911f4d90c545
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62027202"
---
# <a name="how-to-transform-a-node-fragment"></a>Instrukcje: Przekształcanie fragmentu węzła
Kiedy przekształcasz dane zawarte w <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument> obiektu przekształcenia XSLT dotyczą dokumentu jako całości. Innymi słowy Jeśli przekażesz w węźle innym niż węzeł główny dokument, to nie uniemożliwia proces przekształcania uzyskiwania dostępu do wszystkich węzłów w dokumencie załadowane. Aby Przekształcanie fragmentu węzła, należy utworzyć oddzielny obiekt zawierający tylko fragmentu węzła i przekazać ten obiekt do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-transform-a-node-fragment"></a>Aby Przekształcanie fragmentu węzła  
  
1. Utwórz obiekt zawierający dokumentu źródłowego.  
  
2. Znajdź fragment węzeł, który chcesz przekształcić.  
  
3. Utwórz oddzielne obiekty z tylko fragmentu węzła.  
  
4. Przekazywanie fragmentu węzła do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przekształca fragmentu węzła i generuje wyjściowe wyniki do konsoli.  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>Dane wejściowe  
  
##### <a name="booksxml"></a>Books.XML  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>Single.xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Dane wyjściowe  
 Tytuł książki jest Man. ufności  
  
## <a name="see-also"></a>Zobacz także

- [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
