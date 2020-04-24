---
title: Dane wejściowe klasy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
ms.openlocfilehash: 9aae85aa4516dc0555e959358ba1b7db3002145d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710742"
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>Dane wejściowe klasy XslCompiledTransform
<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Metoda akceptuje trzy typy danych wejściowych dla dokumentu źródłowego: obiekt implementujący <xref:System.Xml.XPath.IXPathNavigable> interfejs, <xref:System.Xml.XmlReader> obiekt, który odczytuje dokument źródłowy lub ciąg URI.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslCompiledTransform> Klasa zachowuje domyślnie biały znak. Jest to zgodne z [sekcją 3,4 zalecenia W3C XSLT 1,0](https://www.w3.org/TR/xslt.html#strip).  
  
## <a name="ixpathnavigable-interface"></a>IXPathNavigable, interfejs  
 <xref:System.Xml.XPath.IXPathNavigable> Interfejs jest implementowany w klasach <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlNode> i. Klasy te reprezentują pamięć podręczną danych XML.  
  
- <xref:System.Xml.XmlNode> Klasa jest oparta na Document Object Model W3C (dom) i oferuje możliwości edycji.  
  
- <xref:System.Xml.XPath.XPathDocument> Klasa to magazyn danych tylko do odczytu oparty na modelu danych XPath. <xref:System.Xml.XPath.XPathDocument>jest zalecaną klasą przetwarzania XSLT. Zapewnia większą wydajność w porównaniu z <xref:System.Xml.XmlNode> klasą.  
  
> [!NOTE]
> Przekształcenia są stosowane do dokumentu jako całości. Innymi słowy, jeśli przejdziesz do węzła innego niż węzeł główny dokumentu, nie uniemożliwi to proces przekształcania uzyskuje dostęp do wszystkich węzłów w załadowanym dokumencie. Aby przekształcić fragment węzła, należy utworzyć obiekt zawierający tylko fragment węzła i przekazać go do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Aby uzyskać więcej informacji, zobacz [jak: przekształcanie fragmentu węzła](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md).  
  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metody do przekształcenia pliku Books. XML do pliku Books. html przy użyciu arkusza stylów Transform. xsl. Pliki Books. XML i Transform. xsl można znaleźć w tym temacie: [instrukcje: wykonywanie transformacji XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>XmlReader — obiekt  
 Metoda <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> jest ładowana z bieżącego węzła <xref:System.Xml.XmlReader> przez wszystkie jego elementy podrzędne. Dzięki temu można użyć części dokumentu jako dokumentu kontekstowego. Po powrocie <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody element <xref:System.Xml.XmlReader> jest ustawiany w następnym węźle po zakończeniu dokumentu kontekstowego. Jeśli koniec dokumentu zostanie osiągnięty, <xref:System.Xml.XmlReader> zostanie umieszczony na końcu pliku (EOF).  
  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metody do przekształcenia pliku Books. XML do pliku Books. html przy użyciu arkusza stylów Transform. xsl. Pliki Books. XML i Transform. xsl można znaleźć w tym temacie: [instrukcje: wykonywanie transformacji XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Identyfikator URI ciągu  
 Możesz również określić identyfikator URI dokumentu źródłowego jako dane wejściowe XSLT. <xref:System.Xml.XmlResolver> Służy do rozpoznawania identyfikatora URI. Możesz określić, <xref:System.Xml.XmlResolver> aby użyć, przechodząc do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Jeśli nie <xref:System.Xml.XmlResolver> jest określony, <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Metoda używa domyślnego ustawienia <xref:System.Xml.XmlUrlResolver> bez poświadczeń.  
  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metody do przekształcenia pliku Books. XML do pliku Books. html przy użyciu arkusza stylów Transform. xsl. Pliki Books. XML i Transform. xsl można znaleźć w tym temacie: [instrukcje: wykonywanie transformacji XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Aby uzyskać więcej informacji, zobacz [rozpoznawanie zasobów zewnętrznych podczas przetwarzania XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
