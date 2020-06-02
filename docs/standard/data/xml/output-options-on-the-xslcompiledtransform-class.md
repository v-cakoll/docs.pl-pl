---
title: Opcje danych wyjściowych klasy XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
ms.openlocfilehash: e9ffdc1377dbf124f042802279e7e7a275222eff
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288709"
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>Opcje danych wyjściowych klasy XslCompiledTransform
W tym temacie omówiono dostępne opcje danych wyjściowych XSLT. Możesz określić opcje danych wyjściowych w arkuszu stylów lub w <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodzie.  
  
## <a name="xsloutput-element"></a>xsl: output — element  
 `xsl:output`Element określa opcje dla danych wyjściowych. Typ wyjściowy określony przez <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metodę określa zachowanie `xsl:output` opcji.  
  
 W poniższej tabeli opisano zachowanie każdego z atrybutów dostępnych dla `xsl:output` elementu, gdy typem danych wyjściowych jest strumień lub <xref:System.IO.TextWriter> .  
  
|Nazwa atrybutu|Zachowanie|  
|--------------------|--------------|  
|method|Obsługiwane.|  
|version|Ignorowane. Wersja jest zawsze 1,0 dla plików XML i 4,0 dla języka HTML.|  
|encoding|Ignorowane podczas umieszczania w <xref:System.IO.TextWriter> . <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType>Zamiast tego zostanie użyta właściwość.|  
|Pomiń deklarację XML|Obsługiwane.|  
|niezależne|Obsługiwane.|  
|DOCTYPE — publiczny|Obsługiwane.|  
|DOCTYPE — system|Obsługiwane.|  
|CDATA-elementy sekcji|Obsługiwane.|  
|wyświetlane|Obsługiwane.|  
|Typ nośnika|Obsługiwane.|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>Wysyłanie danych wyjściowych do elementu XmlWriter  
 Jeśli arkusz stylów używa `xsl:output` elementu, a typ danych wyjściowych jest <xref:System.Xml.XmlWriter> obiektem, należy użyć <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> właściwości podczas tworzenia <xref:System.Xml.XmlWriter> obiektu. <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType>Właściwość zwraca <xref:System.Xml.XmlWriterSettings> obiekt, który zawiera informacje pochodzące z `xsl:output` elementu skompilowanego arkusza stylów. Ten <xref:System.Xml.XmlWriterSettings> obiekt może zostać przesłany do <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> metody w celu utworzenia <xref:System.Xml.XmlWriter> obiektu z prawidłowymi ustawieniami.  
  
## <a name="output-types"></a>Typy wyjściowe  
 Poniższa lista zawiera opis typów danych wyjściowych dostępnych w <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> poleceniu.  
  
#### <a name="xmlwriter"></a>Element  
 <xref:System.Xml.XmlWriter>Klasa zapisuje strumienie lub pliki XML. Można określić funkcje do obsługi dla <xref:System.Xml.XmlWriter> obiektu, w tym opcje wyjściowe, przy użyciu <xref:System.Xml.XmlWriterSettings> klasy. <xref:System.Xml.XmlWriter>Klasa jest integralną częścią <xref:System.Xml> struktury. Użyj tego typu danych wyjściowych, aby przetworzyć wyniki wyjściowe w innym procesie XML.  
  
#### <a name="string"></a>String (ciąg)  
 Użyj tego typu danych wyjściowych, aby określić identyfikator URI pliku wyjściowego.  
  
#### <a name="stream"></a>Strumień  
 Strumień jest abstrakcją sekwencji bajtów, takich jak plik, urządzenie wejścia/wyjścia, potok komunikacji między procesami lub gniazdo TCP/IP. <xref:System.IO.Stream>Klasa i jej klasy pochodne zapewniają ogólny widok tych różnych typów danych wejściowych i wyjściowych, izolując programistę od określonych szczegółów systemu operacyjnego i podstawowych urządzeń.  
  
 Ten typ danych wyjściowych służy do wysyłania danych <xref:System.IO.FileStream> do <xref:System.IO.MemoryStream> strumienia wyjściowego ( `Response.OutputStream` ).  
  
#### <a name="textwriter"></a>TextWriter  
 <xref:System.IO.TextWriter>Zapisuje sekwencyjne znaki. Jest zaimplementowana w <xref:System.IO.StringWriter> <xref:System.IO.StreamWriter> klasach i, które zapisują znaki odpowiednio do ciągów lub strumieni. Użyj tego typu danych wyjściowych, jeśli chcesz, aby dane wyjściowe były przekazywane do ciągu.  
  
## <a name="notes"></a>Uwagi  
  
- Podczas zapisywania pustych tagów spacja jest zapisywana między ostatnim znakiem nazwy elementu a ukośnikiem odwrotnym `<myElement />` . Dzięki temu starsze przeglądarki mogą poprawnie wyświetlać wygenerowane strony HTML.  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](xslt-transformations.md)
