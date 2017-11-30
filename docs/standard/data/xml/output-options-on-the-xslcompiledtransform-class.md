---
title: "Opcje wyjściowe klasy XslCompiledTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 61f59c1be3376fb76c91994996840b915cd662ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>Opcje wyjściowe klasy XslCompiledTransform
W tym temacie opisano dostępne opcje wyjściowe XSLT. Opcje wyjściowe można określić w arkuszu stylów lub na <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="xsloutput-element"></a>XSL: Output — Element  
 `xsl:output` Element określa opcje dla danych wyjściowych. Typ danych wyjściowych, określony przez <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Metoda określa zachowanie `xsl:output` opcje.  
  
 W poniższej tabeli przedstawiono zachowania dla każdego z atrybutów, które są dostępne na `xsl:output` elementu, gdy strumień jest typ danych wyjściowych lub <xref:System.IO.TextWriter>.  
  
|Nazwa atrybutu|Zachowanie|  
|--------------------|--------------|  
|— metoda|Obsługiwane.|  
|version|Ignorowane. Wersja jest zawsze 1.0 XML i 4.0 dla kodu HTML.|  
|encoding|Ignorowane podczas wyprowadzania do <xref:System.IO.TextWriter>. <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> Zamiast niego jest używana właściwość.|  
|Pomiń xml deklaracji|Obsługiwane.|  
|niezależne|Obsługiwane.|  
|publiczna doctype|Obsługiwane.|  
|DOCTYPE system|Obsługiwane.|  
|elementy w przypadku sekcja CDATA|Obsługiwane.|  
|wcięcie|Obsługiwane.|  
|Typ nośnika|Obsługiwane.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Wysyłanie danych wyjściowych do XmlWriter  
 Jeśli używa arkusza stylów `xsl:output` elementu i typ danych wyjściowych jest <xref:System.Xml.XmlWriter> obiektu, należy użyć <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> właściwości po utworzeniu <xref:System.Xml.XmlWriter> obiektu. <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> Zwraca <xref:System.Xml.XmlWriterSettings> obiekt zawierający informacje pochodzące z `xsl:output` element arkusza stylów skompilowanego. To <xref:System.Xml.XmlWriterSettings> obiektu mogą zostać przekazane do <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> metodę w celu utworzenia <xref:System.Xml.XmlWriter> obiektu z prawidłowymi ustawieniami.  
  
## <a name="output-types"></a>Typy danych wyjściowych  
 Na poniższej liście opisano dostępne na typy danych wyjściowych <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> polecenia.  
  
#### <a name="xmlwriter"></a>Element XmlWriter  
 <xref:System.Xml.XmlWriter> Klasy zapisuje strumieni XML lub plików. Można określić funkcji obsługiwanych w <xref:System.Xml.XmlWriter> obiektu, w tym opcje wyjściowe przy użyciu <xref:System.Xml.XmlWriterSettings> klasy. <xref:System.Xml.XmlWriter> Klasy jest integralną częścią <xref:System.Xml> framework. Użyj tego typu danych wyjściowych do potoku wynik do innego procesu XML.  
  
#### <a name="string"></a>String  
 Użyj tego typu danych wyjściowych, aby określić identyfikator URI pliku wyjściowego.  
  
#### <a name="stream"></a>Strumień  
 Strumień jest abstrakcję sekwencję bajtów, takie jak plik, urządzenia wejścia/wyjścia, potok komunikacji międzyprocesowej lub gniazda TCP/IP. <xref:System.IO.Stream> Klasy i jej klas pochodnych Podaj ogólny widok różnego typu dane wejściowe i wyjściowe izolowanie programisty z szczegóły podstawowej urządzeń i systemu operacyjnego.  
  
 Ten typ danych wyjściowych służy do wysyłania danych do <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, lub strumienia wyjściowego (`Response.OutputStream`).  
  
#### <a name="textwriter"></a>Element TextWriter  
 <xref:System.IO.TextWriter> Zapisywać znaki sekwencyjne. Jest zaimplementowana w <xref:System.IO.StringWriter> i <xref:System.IO.StreamWriter> klasy, które zapisywanie znaków ciągów lub strumienie, odpowiednio. Należy używać tego typu danych wyjściowych, gdy ma zostać wyprowadzony na ciąg.  
  
## <a name="notes"></a>Uwagi  
  
-   Podczas zapisywania puste znaczniki, spację napisano między ostatnim znakiem w nazwie elementu i ukośnik odwrotny, `<myElement />` np. Dzięki temu starsze przeglądarki ją poprawnie wyświetlić wygenerowany stron HTML.  
  
## <a name="see-also"></a>Zobacz też  
 [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
