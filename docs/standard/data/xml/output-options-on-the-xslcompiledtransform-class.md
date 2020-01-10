---
title: Opcje danych wyjściowych klasy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
ms.openlocfilehash: 504057bd5e10498d39b2bce908742fc20b112c52
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710508"
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>Opcje danych wyjściowych klasy XslCompiledTransform
W tym temacie omówiono dostępne opcje danych wyjściowych XSLT. Możesz określić opcje wyjściowe w arkuszu stylów lub w metodzie <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="xsloutput-element"></a>xsl: output — element  
 Element `xsl:output` określa opcje dla danych wyjściowych. Typ wyjściowy określony przez metodę <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> określa zachowanie opcji `xsl:output`.  
  
 W poniższej tabeli opisano zachowanie każdego z atrybutów dostępnych dla elementu `xsl:output`, gdy typem danych wyjściowych jest strumień lub <xref:System.IO.TextWriter>.  
  
|Nazwa atrybutu|Zachowanie|  
|--------------------|--------------|  
|metoda|Obsługiwane.|  
|Wersja programu|Ignorowane. Wersja jest zawsze 1,0 dla plików XML i 4,0 dla języka HTML.|  
|{1&gt;encoding&lt;1}|Ignorowany podczas wyprowadzania do <xref:System.IO.TextWriter>. Zamiast tego zostanie użyta Właściwość <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType>.|  
|Pomiń deklarację XML|Obsługiwane.|  
|autonomiczne|Obsługiwane.|  
|DOCTYPE — publiczny|Obsługiwane.|  
|DOCTYPE — system|Obsługiwane.|  
|CDATA-elementy sekcji|Obsługiwane.|  
|wyświetlane|Obsługiwane.|  
|Typ nośnika|Obsługiwane.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Wysyłanie danych wyjściowych do elementu XmlWriter  
 Jeśli arkusz stylów używa elementu `xsl:output`, a typ danych wyjściowych jest obiektem <xref:System.Xml.XmlWriter>, należy użyć właściwości <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> podczas tworzenia obiektu <xref:System.Xml.XmlWriter>. Właściwość <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> zwraca obiekt <xref:System.Xml.XmlWriterSettings>, który zawiera informacje pochodzące z elementu `xsl:output` skompilowanego arkusza stylów. Ten obiekt <xref:System.Xml.XmlWriterSettings> można przesłać do metody <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType>, aby utworzyć obiekt <xref:System.Xml.XmlWriter> z prawidłowymi ustawieniami.  
  
## <a name="output-types"></a>Typy wyjściowe  
 Poniższa lista zawiera opis typów danych wyjściowych dostępnych w <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> polecenie.  
  
#### <a name="xmlwriter"></a>Element  
 Klasa <xref:System.Xml.XmlWriter> zapisuje strumienie lub pliki XML. Można określić funkcje do obsługi na obiekcie <xref:System.Xml.XmlWriter>, w tym opcje wyjściowe, przy użyciu klasy <xref:System.Xml.XmlWriterSettings>. Klasa <xref:System.Xml.XmlWriter> jest integralną częścią <xref:System.Xml> Framework. Użyj tego typu danych wyjściowych, aby przetworzyć wyniki wyjściowe w innym procesie XML.  
  
#### <a name="string"></a>String  
 Użyj tego typu danych wyjściowych, aby określić identyfikator URI pliku wyjściowego.  
  
#### <a name="stream"></a>Strumień  
 Strumień jest abstrakcją sekwencji bajtów, takich jak plik, urządzenie wejścia/wyjścia, potok komunikacji między procesami lub gniazdo TCP/IP. Klasa <xref:System.IO.Stream> i jej klasy pochodne zapewniają ogólny widok tych różnych typów danych wejściowych i wyjściowych, izolując programistę od określonych szczegółów systemu operacyjnego i podstawowych urządzeń.  
  
 Użyj tego typu danych wyjściowych, aby wysyłać dane do <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>lub strumienia wyjściowego (`Response.OutputStream`).  
  
#### <a name="textwriter"></a>TextWriter  
 <xref:System.IO.TextWriter> zapisuje znaki sekwencyjne. Jest zaimplementowana w klasach <xref:System.IO.StringWriter> i <xref:System.IO.StreamWriter>, które zapisują znaki odpowiednio do ciągów lub strumieni. Użyj tego typu danych wyjściowych, jeśli chcesz, aby dane wyjściowe były przekazywane do ciągu.  
  
## <a name="notes"></a>Uwagi  
  
- Podczas zapisywania pustych tagów spacja jest zapisywana od ostatniego znaku nazwy elementu i ukośnika odwrotnego, `<myElement />` na przykład. Dzięki temu starsze przeglądarki mogą poprawnie wyświetlać wygenerowane strony HTML.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
