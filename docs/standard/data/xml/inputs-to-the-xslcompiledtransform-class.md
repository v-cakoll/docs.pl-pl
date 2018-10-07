---
title: Dane wejściowe klasy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: beb351ac365694ac909b793bf19adb9fbb8c0274
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48835977"
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>Dane wejściowe klasy XslCompiledTransform
<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Metoda przyjmuje trzy typy dla dokumentu źródłowego w danych wejściowych: obiekt, który implementuje <xref:System.Xml.XPath.IXPathNavigable> interfejsu <xref:System.Xml.XmlReader> obiekt, który odczytuje dokument źródłowy lub ciąg identyfikatora URI.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslCompiledTransform> Klasy zachowuje białe miejsca domyślnie. Jest to zgodne z [sekcji 3.4 zalecenia W3C specyfikacji XSLT 1.0](https://www.w3.org/TR/xslt.html#strip).  
  
## <a name="ixpathnavigable-interface"></a>Interfejs IXPathNavigable  
 <xref:System.Xml.XPath.IXPathNavigable> Interfejs jest implementowany w <xref:System.Xml.XmlNode> i <xref:System.Xml.XPath.XPathDocument> klasy. Te klasy reprezentują wewnątrzpamięciowa pamięć podręczna danych XML.  
  
-   <xref:System.Xml.XmlNode> Klasy opiera się na W3C Document Object Model (DOM) i obejmuje możliwość edycji.  
  
-   <xref:System.Xml.XPath.XPathDocument> Klasy jest magazynem danych tylko do odczytu, na podstawie modelu danych XPath. <xref:System.Xml.XPath.XPathDocument> zalecane klasy dla XSLT jest przetwarzanie. Umożliwia, aby zwiększyć wydajność w porównaniu do <xref:System.Xml.XmlNode> klasy.  
  
> [!NOTE]
>  Przekształcenia mają zastosowanie do dokumentu jako całości. Innymi słowy Jeśli przekażesz w węźle innym niż węzeł główny dokument, to nie uniemożliwia proces przekształcania uzyskiwania dostępu do wszystkich węzłów w dokumencie załadowane. Aby Przekształcanie fragmentu węzła, należy utworzyć obiekt zawierający tylko fragmentu węzła i przekazać ten obiekt do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Aby uzyskać więcej informacji, zobacz [instrukcje: Przekształcanie fragmentu węzła](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md).  
  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metodę, aby przekształcić pliku books.xml pliku books.html, za pomocą transform.xsl arkusza stylów. W tym temacie można znaleźć plików books.xml i transform.xsl: [porady: wykonywanie przekształcenia XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>Obiekt XmlReader  
 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Metoda ładuje z bieżącego węzła <xref:System.Xml.XmlReader> za pośrednictwem jego elementów podrzędnych. Dzięki temu można używać części dokumentu jako dokument kontekstu. Po <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda zwraca <xref:System.Xml.XmlReader> jest ustawiony na następny węzeł po zakończeniu dokumentu kontekstu. Jeśli osiągnięty zostanie koniec dokumentu, <xref:System.Xml.XmlReader> jest umieszczony na końcu pliku (EOF).  
  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metodę, aby przekształcić pliku books.xml pliku books.html, za pomocą transform.xsl arkusza stylów. W tym temacie można znaleźć plików books.xml i transform.xsl: [porady: wykonywanie przekształcenia XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Ciąg identyfikatora URI  
 Można również określić dokument źródłowy identyfikatora URI jako XSLT, Twoje dane wejściowe. <xref:System.Xml.XmlResolver> Jest używany do rozpoznawania identyfikatora URI. Można określić <xref:System.Xml.XmlResolver> do użycia przez przekazanie jej do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Jeśli <xref:System.Xml.XmlResolver> nie zostanie określony, <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda używa domyślnego <xref:System.Xml.XmlUrlResolver> bez poświadczeń.  
  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metodę, aby przekształcić pliku books.xml pliku books.html, za pomocą transform.xsl arkusza stylów. W tym temacie można znaleźć plików books.xml i transform.xsl: [porady: wykonywanie przekształcenia XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Aby uzyskać więcej informacji, zobacz [Rozpoznawanie zewnętrznych zasobów podczas XSLT przetwarzania](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
