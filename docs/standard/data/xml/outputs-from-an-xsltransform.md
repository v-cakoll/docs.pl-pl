---
title: Dane wyjściowe z klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b299f09f3dc47b5d136284d4d1d285f2e5aad5f
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705378"
---
# <a name="outputs-from-an-xsltransform"></a>Dane wyjściowe z klasy XslTransform
Ponieważ arkusze stylów można określić przy użyciu formatu danych wyjściowych `<xsl:output>` instrukcję, określając `method` atrybutu w poniższej tabeli opisano format danych wyjściowych jest, gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda służy do zapisywania danych wyjściowych i format danych wyjściowych zadeklarowany jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 Ponieważ arkusze stylów można określić przy użyciu formatu danych wyjściowych `<xsl:output>` instrukcję, określając `method` atrybutu w poniższej tabeli opisano format danych wyjściowych jest, gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda służy do zapisywania danych wyjściowych i format danych wyjściowych zadeklarowany jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>. W poniższej tabeli opisano, co się stanie, gdy typ danych wyjściowych jest deklarowana przez <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody w połączeniu z użyciem `<xsl:output>` instrukcji:  
  
|\<Metoda: output = > atrybut|Format wyników|  
|-----------------------------------------|-------------------|  
|method="xml"|XML|  
|method="html"|HTML|  
|method="text"|Tekst|  
  
> [!NOTE]
>  Uwaga: `<xsl:output>` instrukcji jest ignorowana, gdy dane wyjściowe <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodą jest <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter>.  
  
 Następujące atrybuty są obsługiwane podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda danych wyjściowych jest <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>:  
  
-   encoding*  
  
-   Pomiń xml deklaracji  
  
-   niezależne  
  
-   publiczna doctype  
  
-   DOCTYPE system  
  
-   elementy w przypadku sekcja CDATA  
  
-   wcięcie  
  
    > [!NOTE]
    >  * kodowania. atrybut jest ignorowany podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda wysyła dane wyjściowe do <xref:System.IO.TextWriter>. Właściwość kodowania <xref:System.IO.TextWriter> zamian jest używana.  
  
 Następujący atrybut jest ignorowany podczas <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda danych wyjściowych jest <xref:System.IO.Stream>:  
  
-   Wersja: wersja jest zawsze 1.0  
  
-   Typ nośnika: typ nośnika  
  
## <a name="escaping-special-characters"></a>Znaki specjalne wyjścia  
 `<xsl:text disable-output-escaping>` Tag jest używany do wskazania, czy znaki specjalne, należy wstawić do postaci XML (na przykład za pomocą `<&lt>` zamiast `"<"` symbol) lub po lewej stronie w obecnym stanie. `disable-output-escaping` Atrybut jest ignorowany podczas przekształcania w <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter> obiektu i nie ma wpływu na znaki specjalne.  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
