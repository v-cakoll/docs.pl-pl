---
title: Dane wyjściowe klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: 178b1e949868d3af893cbcb6df63590053341a3e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710495"
---
# <a name="outputs-from-an-xsltransform"></a>Dane wyjściowe klasy XslTransform
Ponieważ arkusze stylów mogą określić format danych wyjściowych przy użyciu instrukcji `<xsl:output>` z atrybutem `method`, w poniższej tabeli opisano, w jaki sposób format danych wyjściowych <xref:System.Xml.Xsl.XslTransform.Transform%2A> jest używany do zapisywania danych wyjściowych, a format danych wyjściowych jest zadeklarowany jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>.  
  
> [!NOTE]
> Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0. Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Ponieważ arkusze stylów mogą określić format danych wyjściowych przy użyciu instrukcji `<xsl:output>` z atrybutem `method`, w poniższej tabeli opisano, w jaki sposób format danych wyjściowych <xref:System.Xml.Xsl.XslTransform.Transform%2A> jest używany do zapisywania danych wyjściowych, a format danych wyjściowych jest zadeklarowany jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>. W poniższej tabeli opisano, co się dzieje, gdy typ danych wyjściowych jest zadeklarowany przez metodę <xref:System.Xml.Xsl.XslTransform.Transform%2A> w połączeniu z użyciem instrukcji `<xsl:output>`:  
  
|\<xsl: output — Metoda = atrybut >|Format wyniku|  
|-----------------------------------------|-------------------|  
|method="xml"|{1&gt;XML&lt;1}|  
|method="html"|HTML|  
|method="text"|Tekst|  
  
> [!NOTE]
> Uwaga: Instrukcja `<xsl:output>` jest ignorowana, gdy dane wyjściowe metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> są <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter>.  
  
 Następujące atrybuty są obsługiwane, gdy dane wyjściowe metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> są <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>:  
  
- encoding*  
  
- Pomiń deklarację XML  
  
- autonomiczne  
  
- DOCTYPE — publiczny  
  
- DOCTYPE — system  
  
- CDATA-elementy sekcji  
  
- wyświetlane  
  
    > [!NOTE]
    > \*atrybut kodowania jest ignorowany, gdy metoda <xref:System.Xml.Xsl.XslTransform.Transform%2A> wysyła dane wyjściowe do <xref:System.IO.TextWriter>. Zamiast tego zostanie użyta Właściwość Encoding w <xref:System.IO.TextWriter>. 
  
 Następujący atrybut jest ignorowany, gdy dane wyjściowe metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> są <xref:System.IO.Stream>:  
  
- Wersja: wersja jest zawsze 1,0  
  
- Typ nośnika: typ nośnika  
  
## <a name="escaping-special-characters"></a>Znaki specjalne ucieczki  
 Tag `<xsl:text disable-output-escaping>` służy do wskazywania, czy znaki specjalne muszą być wyprowadzane do formularza XML (na przykład przy użyciu `<&lt>` zamiast symbolu `"<"`) lub pozostawione w stanie obecne. Atrybut `disable-output-escaping` jest ignorowany podczas przekształcania do obiektu <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter> i nie ma wpływu na znaki specjalne.  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
