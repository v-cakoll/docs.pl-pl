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
ms.openlocfilehash: 043c37a17375bf2dcdad9e4b429cfca7b96ef7cb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966975"
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>Dane wejściowe klasy XslCompiledTransform
Metoda akceptuje trzy typy danych wejściowych dla dokumentu źródłowego: obiekt <xref:System.Xml.XPath.IXPathNavigable> implementujący interfejs, <xref:System.Xml.XmlReader> obiekt, który odczytuje dokument źródłowy lub ciąg URI. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslCompiledTransform> Klasa zachowuje domyślnie biały znak. Jest to zgodne z [sekcją 3,4 zalecenia W3C XSLT 1,0](https://www.w3.org/TR/xslt.html#strip).  
  
## <a name="ixpathnavigable-interface"></a>IXPathNavigable, interfejs  
 Interfejs jest implementowany <xref:System.Xml.XmlNode> w klasach <xref:System.Xml.XPath.XPathDocument>i. <xref:System.Xml.XPath.IXPathNavigable> Klasy te reprezentują pamięć podręczną danych XML.  
  
- <xref:System.Xml.XmlNode> Klasa jest oparta na Document Object Model W3C (dom) i oferuje możliwości edycji.  
  
- <xref:System.Xml.XPath.XPathDocument> Klasa to magazyn danych tylko do odczytu oparty na modelu danych XPath. <xref:System.Xml.XPath.XPathDocument>jest zalecaną klasą przetwarzania XSLT. Zapewnia większą wydajność w porównaniu z <xref:System.Xml.XmlNode> klasą.  
  
> [!NOTE]
> Przekształcenia są stosowane do dokumentu jako całości. Innymi słowy, jeśli przejdziesz do węzła innego niż węzeł główny dokumentu, nie uniemożliwi to proces przekształcania uzyskuje dostęp do wszystkich węzłów w załadowanym dokumencie. Aby przekształcić fragment węzła, należy utworzyć obiekt zawierający tylko fragment węzła i przekazać go do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Aby uzyskać więcej informacji, zobacz [jak: Przekształcanie fragmentu](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)węzła.  
  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metody do przekształcenia pliku Books. XML do pliku Books. html przy użyciu arkusza stylów Transform. xsl. Pliki Books. XML i Transform. xsl można znaleźć w tym temacie: [Instrukcje: Wykonaj transformację XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>XmlReader — obiekt  
 Metoda <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> jest ładowana z bieżącego węzła <xref:System.Xml.XmlReader> przez wszystkie jego elementy podrzędne. Dzięki temu można użyć części dokumentu jako dokumentu kontekstowego. Po powrocie <xref:System.Xml.XmlReader> metody element jest ustawiany w następnym węźle po zakończeniu dokumentu kontekstowego. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Jeśli koniec dokumentu zostanie osiągnięty, <xref:System.Xml.XmlReader> zostanie umieszczony na końcu pliku (EOF).  
  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metody do przekształcenia pliku Books. XML do pliku Books. html przy użyciu arkusza stylów Transform. xsl. Pliki Books. XML i Transform. xsl można znaleźć w tym temacie: [Instrukcje: Wykonaj transformację XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Identyfikator URI ciągu  
 Możesz również określić identyfikator URI dokumentu źródłowego jako dane wejściowe XSLT. <xref:System.Xml.XmlResolver> Służy do rozpoznawania identyfikatora URI. Możesz określić, <xref:System.Xml.XmlResolver> aby użyć, przechodząc <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> do metody. Jeśli nie <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>jestokreślony , metoda używa domyślnego ustawienia <xref:System.Xml.XmlUrlResolver> bez poświadczeń. <xref:System.Xml.XmlResolver>  
  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> metody do przekształcenia pliku Books. XML do pliku Books. html przy użyciu arkusza stylów Transform. xsl. Pliki Books. XML i Transform. xsl można znaleźć w tym temacie: [Instrukcje: Wykonaj transformację XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Aby uzyskać więcej informacji, zobacz [rozpoznawanie zasobów zewnętrznych podczas przetwarzania XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
