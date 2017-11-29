---
title: "Dane wyjściowe z XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 92bf2d7184ca2eb8b17c1d83130c66d1f33f0483
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="outputs-from-an-xsltransform"></a>Dane wyjściowe z XslTransform
Ponieważ arkusze stylów można określić przy użyciu formatu danych wyjściowych `<xsl:output>` instrukcji z `method` atrybutu w poniższej tabeli opisano jest format danych wyjściowych, gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda służy do zapisywania danych wyjściowych i format wyjściowy to zadeklarowany jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 Ponieważ arkusze stylów można określić przy użyciu formatu danych wyjściowych `<xsl:output>` instrukcji z `method` atrybutu w poniższej tabeli opisano jest format danych wyjściowych, gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda służy do zapisywania danych wyjściowych i format wyjściowy to zadeklarowany jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>. W poniższej tabeli opisano, co się dzieje, gdy typ danych wyjściowych jest deklarowany przez <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody w połączeniu z użyciem `<xsl:output>` instrukcji:  
  
|\<Metoda XSL: output = > atrybutu|Format wyników|  
|-----------------------------------------|-------------------|  
|Metoda = "xml"|XML|  
|Metoda = "kod html"|HTML|  
|Metoda = "text"|Tekst|  
  
> [!NOTE]
>  Uwaga: `<xsl:output>` instrukcji jest ignorowany podczas dane wyjściowe <xref:System.Xml.Xsl.XslTransform.Transform%2A> jest metoda <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter>.  
  
 Następujące atrybuty są obsługiwane podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> danych wyjściowych metody <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>:  
  
-   kodowanie *  
  
-   Pomiń xml deklaracji  
  
-   niezależne  
  
-   publiczna doctype  
  
-   DOCTYPE system  
  
-   elementy w przypadku sekcja CDATA  
  
-   wcięcie  
  
    > [!NOTE]
    >  * kodowania atrybut jest ignorowany podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda wysyła dane wyjściowe do <xref:System.IO.TextWriter>. Właściwość kodowania <xref:System.IO.TextWriter> zamiast niego jest używana.  
  
 Następujący atrybut jest ignorowany podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> danych wyjściowych metody <xref:System.IO.Stream>:  
  
-   Wersja: wersja jest zawsze 1.0  
  
-   Typ nośnika: typ nośnika  
  
## <a name="escaping-special-characters"></a>Znaki specjalne wyjścia  
 `<xsl:text disable-output-escaping>` Tag jest używany do określania, czy znaki specjalne należy wstawić do postaci XML (na przykład za pomocą `<&lt>` zamiast `"<"` symbol) lub w lewo w obecnym stanie. `disable-output-escaping` Atrybut jest ignorowany w przypadku przekształcania do <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter> obiektu i nie ma wpływu na znaki specjalne.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa XslTransform implementuje procesorze XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
