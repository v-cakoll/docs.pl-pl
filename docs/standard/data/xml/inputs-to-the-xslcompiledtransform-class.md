---
title: Dane wejściowe do klasy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc909b666b90d8c8825e7dbef33e48b6126bd7c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>Dane wejściowe do klasy XslCompiledTransform
<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Metoda przyjmuje trzech typów dla dokumentu źródłowego wejściowych: obiekt, który implementuje <xref:System.Xml.XPath.IXPathNavigable> interfejsu <xref:System.Xml.XmlReader> obiekt, który odczytuje dokument źródłowy lub ciąg identyfikatora URI.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslCompiledTransform> Klasy zachowuje biały znak domyślnie. Jest to zgodne z sekcji 3.4 zalecenie W3C XSLT 1.0 (sekcja 3.4, http://www.w3.org/TR/xslt.html#strip).  
  
## <a name="ixpathnavigable-interface"></a>Interfejs IXPathNavigable  
 <xref:System.Xml.XPath.IXPathNavigable> Interfejs jest wdrażany w <xref:System.Xml.XmlNode> i <xref:System.Xml.XPath.XPathDocument> klasy. Te klasy reprezentują w pamięci podręcznej danych XML.  
  
-   <xref:System.Xml.XmlNode> Klasy jest oparta na W3C modelu DOM (Document Object) i obejmuje możliwości edycji.  
  
-   <xref:System.Xml.XPath.XPathDocument> Klasy jest oparte na modelu danych XPath magazyn danych tylko do odczytu. <xref:System.Xml.XPath.XPathDocument> Klasa zalecane dla XSLT jest przetwarzanie. Zapewnia większą wydajność w porównaniu z <xref:System.Xml.XmlNode> klasy.  
  
> [!NOTE]
>  Przekształcenia mają zastosowanie do dokumentu jako całość. Innymi słowy w przypadku przekazania w węźle innym niż węzeł główny dokumentu, to nie zapobiega proces przekształcania podczas uzyskiwania dostępu do wszystkich węzłów w załadowanego dokumentu. Aby przekształcić fragmentu węzła, należy utworzyć obiekt zawierający tylko fragmentu węzeł i przekazać do obiektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Aby uzyskać więcej informacji, zobacz [porady: Przekształcanie fragmentu węzła](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md).  
  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metodę, aby przekształcić plik books.xml pliku books.html, za pomocą transform.xsl arkusza stylów. W tym temacie można znaleźć plików books.xml i transform.xsl: [porady: przekształcenie XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>Obiekt XmlReader  
 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Metody ładuje z bieżącego węzła <xref:System.Xml.XmlReader> przez wszystkie elementy podrzędne. Pozwala na użycie części dokumentu jako dokument kontekstu. Po <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> zwraca metoda <xref:System.Xml.XmlReader> znajduje się w węźle dalej na końcu dokumentu kontekstu. Jeśli zostanie osiągnięty koniec dokumentu, <xref:System.Xml.XmlReader> znajduje się na końcu pliku (EOF).  
  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metodę, aby przekształcić plik books.xml pliku books.html, za pomocą transform.xsl arkusza stylów. W tym temacie można znaleźć plików books.xml i transform.xsl: [porady: przekształcenie XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Ciąg identyfikatora URI  
 Można również określić identyfikator URI dokumentu źródłowego jako Twoje XSLT danych wejściowych. <xref:System.Xml.XmlResolver> Jest używany do rozpoznawania identyfikatora URI. Można określić <xref:System.Xml.XmlResolver> do użycia, przekazując go do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Jeśli <xref:System.Xml.XmlResolver> nie zostanie określony, <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> — metoda korzysta z domyślnego <xref:System.Xml.XmlUrlResolver> bez poświadczeń.  
  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metodę, aby przekształcić plik books.xml pliku books.html, za pomocą transform.xsl arkusza stylów. W tym temacie można znaleźć plików books.xml i transform.xsl: [porady: przekształcenie XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Aby uzyskać więcej informacji, zobacz [Rozpoznawanie zewnętrznych zasobów podczas XSLT przetwarzania](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
