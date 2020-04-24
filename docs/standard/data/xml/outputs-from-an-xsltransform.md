---
title: Dane wyjściowe klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 93cbf7807630a605e17e7f513055c052aad0d08e
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159640"
---
# <a name="outputs-from-an-xsltransform"></a>Dane wyjściowe klasy XslTransform
Ponieważ arkusze stylów mogą określić format danych wyjściowych przy `<xsl:output>` użyciu instrukcji z `method` atrybutem, w poniższej tabeli opisano, w jaki <xref:System.Xml.Xsl.XslTransform.Transform%2A> sposób format danych wyjściowych jest używany do pisania danych wyjściowych, a format danych wyjściowych jest <xref:System.IO.Stream> zadeklarowany jako lub <xref:System.IO.TextWriter>.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Ponieważ arkusze stylów mogą określić format danych wyjściowych przy `<xsl:output>` użyciu instrukcji z `method` atrybutem, w poniższej tabeli opisano, w jaki <xref:System.Xml.Xsl.XslTransform.Transform%2A> sposób format danych wyjściowych jest używany do pisania danych wyjściowych, a format danych wyjściowych jest <xref:System.IO.Stream> zadeklarowany jako lub <xref:System.IO.TextWriter>. W poniższej tabeli opisano, <xref:System.Xml.Xsl.XslTransform.Transform%2A> co się dzieje, gdy typ danych wyjściowych jest zadeklarowany przez metodę w połączeniu z `<xsl:output>` użyciem instrukcji:  
  
|\<xsl: output — Metoda = > atrybut|Format wyniku|  
|-----------------------------------------|-------------------|  
|Metoda = "XML"|XML|  
|Metoda = "HTML"|HTML|  
|Metoda = "text"|Tekst|  
  
> [!NOTE]
> Uwaga: `<xsl:output>` instrukcja jest ignorowana, jeśli dane wyjściowe <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody są <xref:System.Xml.XmlReader> lub. <xref:System.Xml.XmlWriter>  
  
 Następujące atrybuty są obsługiwane, <xref:System.Xml.Xsl.XslTransform.Transform%2A> gdy wynikiem metody jest <xref:System.IO.Stream> lub: <xref:System.IO.TextWriter>  
  
- Kody  
  
- Pomiń deklarację XML  
  
- niezależne  
  
- DOCTYPE — publiczny  
  
- DOCTYPE — system  
  
- CDATA-elementy sekcji  
  
- wyświetlane  
  
    > [!NOTE]
    > \*Atrybut Encoding jest ignorowany, gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> Metoda wysyła dane wyjściowe do <xref:System.IO.TextWriter>. Właściwość Encoding w <xref:System.IO.TextWriter> jest używana w zamian.
  
 Następujący atrybut jest ignorowany, <xref:System.Xml.Xsl.XslTransform.Transform%2A> gdy wyjście metody jest: <xref:System.IO.Stream>  
  
- Wersja: wersja jest zawsze 1,0  
  
- Typ nośnika: typ nośnika  
  
## <a name="escaping-special-characters"></a>Znaki specjalne ucieczki  
 `<xsl:text disable-output-escaping>` Tag służy do wskazywania, czy znaki specjalne muszą być wyprowadzane do formularza XML (na przykład przy użyciu `<&lt>` zamiast `"<"` symbolu) lub pozostawione w stanie obecne. `disable-output-escaping` Atrybut jest ignorowany podczas przekształcania do obiektu <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter> i nie ma wpływu na znaki specjalne.  
  
## <a name="see-also"></a>Zobacz też

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
