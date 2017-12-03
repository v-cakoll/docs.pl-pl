---
title: XML i serializacji SOAP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d5b89392801e7cf85fcda121a86d0bda4e7ac18
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="xml-and-soap-serialization"></a>XML i serializacji SOAP
Konwertuje serializacji XML (serializuje) pola publiczne i właściwości obiektu, lub parametry i wartości zwracane metod do strumień XML, który odpowiada określony dokument języka (XSD) definicji schematu XML. Powoduje serializacji XML w silnie typizowanej klasy z właściwości publiczne i pola, które są konwertowane na format seryjny (w tym przypadku XML) do przechowywania lub transportu.  
  
 Ponieważ XML jest standardem otwartym, strumień XML mogą być przetwarzane przez dowolną aplikację, zgodnie z potrzebami, niezależnie od platformy. Na przykład usługi XML sieci Web utworzony przy użyciu platformy ASP.NET <xref:System.Xml.Serialization.XmlSerializer> klasa do tworzenia strumieni XML, które przekazywania danych między aplikacjami usług XML sieci Web w Internecie lub intranecie. Z kolei deserializacji pobiera strumień XML i rekonstruuje obiektu.  
  
 Umożliwia także serializacji XML można serializować obiektów do strumieni XML, które są zgodne ze specyfikacją protokołu SOAP. Protokołu SOAP to protokół oparte na języku XML, zaprojektowany specjalnie w celu transportu wywołań procedur za pomocą języka XML.  
  
 Do serializacji lub deserializacji obiekty, użyj <xref:System.Xml.Serialization.XmlSerializer> klasy. Aby utworzyć klasy serializacji, należy użyć narzędzia definicji schematu XML.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie do serializacji XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 Udostępnia ogólne definicji serializacji, zwłaszcza serializacji XML.  
  
 [Porady: szeregowania obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 Instrukcje krok po kroku dotyczący dla serializacji obiektu.  
  
 [Porady: deserializacji obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 Instrukcje krok po kroku deserializacji obiektu.  
  
 [Przykłady serializacji XML](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 Przykłady, które przedstawiają podstawy serializacji XML.  
  
 [Narzędzie definicji schematu XML i serializacja XML](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 Opisuje sposób można utworzyć klasy, które będą zgodne z określonym schematem języka (XSD) definicji schematu XML lub do generowania schematu XML z PLiku dll za pomocą narzędzia definicji schematu XML.  
  
 [Kontrolowanie serializacji XML przy użyciu atrybutów](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 Opisuje sposób kontroluje serializacji przy użyciu atrybutów.  
  
 [Atrybuty, które kontrolują serializacji XML](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 Wyświetla listę atrybutów, które są używane do kontrolowania serializacji XML.  
  
 [Porady: Określ nazwę elementu alternatywnego strumienia XML](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 Przedstawia informacje o zaawansowanych scenariusz przedstawiający sposób generowania wielu strumieni XML przez zastąpienie serializacji.  
  
 [Porady: kontrolowanie serializacji klas pochodnych](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 Przykład sposobu sterowania serializacją klas pochodnych.  
  
 [Porady: kwalifikują się do elementu XML i nazwach atrybutów XML](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 Opisuje sposób definiowania i kontrolować sposób, w których XML obszary nazw są używane w strumieniu XML.  
  
 [Serializacja XML z usługami sieci Web XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 Wyjaśniono, jak serializacji XML jest używany w usług XML sieci Web.  
  
 [Porady: szeregowania obiektu jako strumień SOAP zakodowane w formacie XML](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 Informacje dotyczące używania <xref:System.Xml.Serialization.XmlSerializer> klasy w celu utworzenia zakodowanego strumieni XML protokołu SOAP, które są zgodne z sekcji 5 konsorcjum World Wide Web (www.w3.org) dokumentu "Simple Object Access Protocol (SOAP) 1.1."  
  
 [Porady: Zastąp serializacji XML użyciu zakodowanego protokołu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 Opisuje proces zastępowanie serializacji obiektów XML jako komunikaty protokołu SOAP.  
  
 [Atrybuty, które sterowania serializacją użyciu zakodowanego protokołu SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 Wyświetla listę atrybutów, które są używane do kontrolowania serializacji kodowany w formacie protokołu SOAP.  
  
 [\<System.XML.serialization > — Element](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 Element konfiguracji najwyższego poziomu do sterowania serializacji XML.  
  
 [\<dateTimeSerialization > — Element](../../../docs/standard/serialization/datetimeserialization-element.md)  
 Określa tryb serializacji <xref:System.DateTime> obiektów.  
  
 [\<schemaImporterExtensions > — Element](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.  
  
 [\<Dodaj > elementu \<xmlSchemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 Dodaje typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Programowanie zaawansowanych technologii](http://msdn.microsoft.com/en-us/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 Łącza do dodatkowych informacji zadań związanych z projektowaniem zaawansowane i techniki programistyczne w programie .NET Framework.  
  
 [Utworzone za pomocą programu ASP.NET i klientami usługi XML sieci Web usług XML sieci Web](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 Zawiera tematy, które opisują oraz wyjaśniono, jak do usług XML sieci Web za pomocą programu ASP.NET programu.  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja binarna](../../../docs/standard/serialization/binary-serialization.md)
