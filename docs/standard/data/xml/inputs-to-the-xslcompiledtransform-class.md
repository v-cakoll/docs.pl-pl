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
Metoda <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> akceptuje trzy typy danych wejściowych dla dokumentu źródłowego: obiekt implementujący interfejs <xref:System.Xml.XPath.IXPathNavigable>, obiekt <xref:System.Xml.XmlReader>, który odczytuje dokument źródłowy lub ciąg URI.  
  
> [!NOTE]
> Klasa <xref:System.Xml.Xsl.XslCompiledTransform> domyślnie zachowuje biały znak. Jest to zgodne z [sekcją 3,4 zalecenia W3C XSLT 1,0](https://www.w3.org/TR/xslt.html#strip).  
  
## <a name="ixpathnavigable-interface"></a>IXPathNavigable, interfejs  
 Interfejs <xref:System.Xml.XPath.IXPathNavigable> jest zaimplementowany w klasach <xref:System.Xml.XmlNode> i <xref:System.Xml.XPath.XPathDocument>. Klasy te reprezentują pamięć podręczną danych XML.  
  
- Klasa <xref:System.Xml.XmlNode> jest oparta na Document Object Model W3C (DOM) i oferuje możliwości edycji.  
  
- Klasa <xref:System.Xml.XPath.XPathDocument> to magazyn danych tylko do odczytu oparty na modelu danych XPath. <xref:System.Xml.XPath.XPathDocument> jest zalecaną klasą przetwarzania XSLT. Zapewnia większą wydajność w porównaniu z klasą <xref:System.Xml.XmlNode>.  
  
> [!NOTE]
> Przekształcenia są stosowane do dokumentu jako całości. Innymi słowy, jeśli przejdziesz do węzła innego niż węzeł główny dokumentu, nie uniemożliwi to proces przekształcania uzyskuje dostęp do wszystkich węzłów w załadowanym dokumencie. Aby przekształcić fragment węzła, należy utworzyć obiekt zawierający tylko fragment węzła i przekazać go do metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>. Aby uzyskać więcej informacji, zobacz [jak: przekształcanie fragmentu węzła](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md).  
  
 W poniższym przykładzie użyto metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType>, aby przekształcić plik Books. XML do pliku Books. html przy użyciu arkusza stylów Transform. xsl. Pliki Books. XML i Transform. xsl można znaleźć w tym temacie: [instrukcje: wykonywanie transformacji XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>XmlReader — obiekt  
 Metoda <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> jest ładowana z bieżącego węzła <xref:System.Xml.XmlReader> przez wszystkie jego elementy podrzędne. Dzięki temu można użyć części dokumentu jako dokumentu kontekstowego. Po powrocie metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>, <xref:System.Xml.XmlReader> jest umieszczana w następnym węźle po zakończeniu dokumentu kontekstowego. Jeśli koniec dokumentu zostanie osiągnięty, <xref:System.Xml.XmlReader> zostanie umieszczony na końcu pliku (EOF).  
  
 W poniższym przykładzie użyto metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType>, aby przekształcić plik Books. XML do pliku Books. html przy użyciu arkusza stylów Transform. xsl. Pliki Books. XML i Transform. xsl można znaleźć w tym temacie: [instrukcje: wykonywanie transformacji XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Identyfikator URI ciągu  
 Możesz również określić identyfikator URI dokumentu źródłowego jako dane wejściowe XSLT. <xref:System.Xml.XmlResolver> jest używany do rozpoznawania identyfikatora URI. Możesz określić <xref:System.Xml.XmlResolver> do użycia przez przekazanie go do metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>. Jeśli nie określono <xref:System.Xml.XmlResolver>, Metoda <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> używa domyślnego <xref:System.Xml.XmlUrlResolver> bez poświadczeń.  
  
 W poniższym przykładzie użyto metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType>, aby przekształcić plik Books. XML do pliku Books. html przy użyciu arkusza stylów Transform. xsl. Pliki Books. XML i Transform. xsl można znaleźć w tym temacie: [instrukcje: wykonywanie transformacji XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Aby uzyskać więcej informacji, zobacz [rozpoznawanie zasobów zewnętrznych podczas przetwarzania XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
