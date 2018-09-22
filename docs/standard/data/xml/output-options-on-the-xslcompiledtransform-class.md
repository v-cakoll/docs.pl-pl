---
title: Opcje danych wyjściowych klasy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 694d2be51d025ab054caf19e4aa2900216ad5b2e
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46699121"
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>Opcje danych wyjściowych klasy XslCompiledTransform
W tym temacie opisano dostępne opcje wyjściowe XSLT. Możesz określić opcje danych wyjściowych w arkuszu stylów lub na <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="xsloutput-element"></a>: Output — Element  
 `xsl:output` Element określa opcje dla danych wyjściowych. Typ danych wyjściowych, określony przez <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody określa zachowanie `xsl:output` opcje.  
  
 W poniższej tabeli przedstawiono zachowania dla każdego z atrybutów, które są dostępne na `xsl:output` elementu w przypadku typu danych wyjściowych jest strumień lub <xref:System.IO.TextWriter>.  
  
|Nazwa atrybutu|Zachowanie|  
|--------------------|--------------|  
|— metoda|Obsługiwane.|  
|version|Ignorowane. Wersja jest zawsze 1.0 dla formatu XML i 4.0 dla kodu HTML.|  
|encoding|Ignorowane w przypadku podawania do <xref:System.IO.TextWriter>. <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> Właściwość jest używana zamiast tego.|  
|Pomiń xml deklaracji|Obsługiwane.|  
|niezależne|Obsługiwane.|  
|publiczna doctype|Obsługiwane.|  
|DOCTYPE system|Obsługiwane.|  
|elementy w przypadku sekcja CDATA|Obsługiwane.|  
|wcięcie|Obsługiwane.|  
|Typ nośnika|Obsługiwane.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Wysyłanie danych wyjściowych do XmlWriter  
 Jeśli korzysta z arkusza stylów `xsl:output` elementu i typ danych wyjściowych jest <xref:System.Xml.XmlWriter> obiektu, należy użyć <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> właściwości po utworzeniu <xref:System.Xml.XmlWriter> obiektu. <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> Właściwość zwraca <xref:System.Xml.XmlWriterSettings> obiektu, który zawiera informacje pochodzące z `xsl:output` element arkusza stylów skompilowanego. To <xref:System.Xml.XmlWriterSettings> obiekt może być przekazywany do <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> metodę w celu utworzenia <xref:System.Xml.XmlWriter> obiektu z prawidłowymi ustawieniami.  
  
## <a name="output-types"></a>Typy danych wyjściowych  
 Poniższa lista zawiera opis typów danych wyjściowych, dostępne na <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> polecenia.  
  
#### <a name="xmlwriter"></a>Parametr XmlWriter  
 <xref:System.Xml.XmlWriter> Klasy zapisuje strumieni XML lub plików. Można określić funkcji do obsługi na <xref:System.Xml.XmlWriter> obiekt, w tym opcje danych wyjściowych za pomocą <xref:System.Xml.XmlWriterSettings> klasy. <xref:System.Xml.XmlWriter> Klasa jest integralną częścią <xref:System.Xml> framework. Użyj tego typu danych wyjściowych do potoku wyników danych wyjściowych do innego procesu XML.  
  
#### <a name="string"></a>String  
 Użyj tego typu danych wyjściowych, aby określić identyfikator URI pliku wyjściowego.  
  
#### <a name="stream"></a>Strumień  
 Strumień jest klasą abstrakcyjną sekwencji bajtów, takich jak plik, urządzenia z systemem wejścia/wyjścia, potok komunikacji między procesami lub gniazda TCP/IP. <xref:System.IO.Stream> Klasy i jej klasy pochodne oferują ogólny widok tych różnych typów danych wejściowych i wyjściowych, izolując programistę od specyficznych szczegółów systemu operacyjnego i podstawowych urządzeń.  
  
 Ten typ danych wyjściowych służy do wysyłania danych do <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, lub strumień wyjściowy (`Response.OutputStream`).  
  
#### <a name="textwriter"></a>TextWriter  
 <xref:System.IO.TextWriter> Zapisywać znaki sekwencyjne. Jest zaimplementowana w <xref:System.IO.StringWriter> i <xref:System.IO.StreamWriter> klasy, które zapisywanie znaków ciągów lub strumieni, odpowiednio. Użyj tego typu dane wyjściowe, gdy użytkownik chce przesyłać dane wyjściowe do ciągu.  
  
## <a name="notes"></a>Uwagi  
  
-   Podczas pisania się puste znaczniki, spacja jest zapisywany między ostatni znak nazwy elementu i ukośnik odwrotny, `<myElement />` na przykład. Dzięki temu starsze przeglądarki poprawnie wyświetlić wygenerowanych stron HTML.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
