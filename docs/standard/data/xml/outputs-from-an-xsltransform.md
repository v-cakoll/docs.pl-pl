---
title: Dane wyjściowe klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a6c2ea2fe2f02dc1897cb1348f4c2585b730036
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924968"
---
# <a name="outputs-from-an-xsltransform"></a>Dane wyjściowe klasy XslTransform
Ponieważ arkusze stylów mogą określić format danych wyjściowych przy `<xsl:output>` użyciu instrukcji `method` z atrybutem, w poniższej tabeli opisano, w jaki <xref:System.Xml.Xsl.XslTransform.Transform%2A> sposób format danych wyjściowych jest używany do pisania danych wyjściowych, a format danych wyjściowych to zadeklarowane jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Ponieważ arkusze stylów mogą określić format danych wyjściowych przy `<xsl:output>` użyciu instrukcji `method` z atrybutem, w poniższej tabeli opisano, w jaki <xref:System.Xml.Xsl.XslTransform.Transform%2A> sposób format danych wyjściowych jest używany do pisania danych wyjściowych, a format danych wyjściowych to zadeklarowane jako <xref:System.IO.Stream> lub <xref:System.IO.TextWriter>. W poniższej tabeli opisano, <xref:System.Xml.Xsl.XslTransform.Transform%2A> co się dzieje, gdy typ danych wyjściowych jest zadeklarowany przez metodę w połączeniu z użyciem `<xsl:output>` instrukcji:  
  
|\<xsl: output — Metoda = > atrybut|Format wyniku|  
|-----------------------------------------|-------------------|  
|method="xml"|XML|  
|method="html"|HTML|  
|method="text"|Tekst|  
  
> [!NOTE]
> Uwaga: Instrukcja jest ignorowana, jeśli dane wyjściowe <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody są <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter>. `<xsl:output>`  
  
 Następujące atrybuty są obsługiwane, <xref:System.Xml.Xsl.XslTransform.Transform%2A> gdy wynikiem metody <xref:System.IO.Stream> jest lub <xref:System.IO.TextWriter>:  
  
- encoding*  
  
- Pomiń deklarację XML  
  
- niezależne  
  
- DOCTYPE — publiczny  
  
- DOCTYPE — system  
  
- CDATA-elementy sekcji  
  
- wyświetlane  
  
    > [!NOTE]
    > \*Atrybut Encoding jest ignorowany, gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> Metoda wysyła dane wyjściowe <xref:System.IO.TextWriter>do. Właściwość Encoding w <xref:System.IO.TextWriter> jest używana w zamian. 
  
 Następujący atrybut jest ignorowany, <xref:System.Xml.Xsl.XslTransform.Transform%2A> gdy wyjście metody <xref:System.IO.Stream>jest:  
  
- Wersja: wersja jest zawsze 1,0  
  
- Typ nośnika: typ nośnika  
  
## <a name="escaping-special-characters"></a>Znaki specjalne ucieczki  
 Tag służy do wskazywania, czy znaki specjalne muszą być wyprowadzane do formularza XML (na przykład przy użyciu `<&lt>` zamiast `"<"` symbolu) lub pozostawione w stanie obecne. `<xsl:text disable-output-escaping>` Atrybut jest ignorowany podczas przekształcania <xref:System.Xml.XmlReader> do obiektu lub <xref:System.Xml.XmlWriter> i nie ma wpływu na znaki specjalne. `disable-output-escaping`  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
