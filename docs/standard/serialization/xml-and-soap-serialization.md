---
title: Serializacja XML i SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: d9dc68d8e7eced031af404aaec20784573c9930a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965621"
---
# <a name="xml-and-soap-serialization"></a>Serializacja XML i SOAP

Konwertuje serializacji XML (serializuje) pola publiczne i właściwości obiektu, lub parametry i wartości zwracane metod do strumień XML, który odpowiada określony dokument języka (XSD) definicji schematu XML. Powoduje serializacji XML w silnie typizowanej klasy z właściwości publiczne i pola, które są konwertowane na format seryjny (w tym przypadku XML) do przechowywania lub transportu.

Ponieważ kod XML jest otwarty standard, strumień XML mogą być przetwarzane przez dowolną aplikację, zgodnie z potrzebami, niezależnie od platformy. Na przykład usług sieci Web XML utworzone za pomocą programu ASP.NET, użyj <xref:System.Xml.Serialization.XmlSerializer> klasy w celu utworzenia strumieni XML, które przekazują dane między aplikacjami usług XML sieci Web w Internecie lub intranecie. Z kolei deserializacji pobiera strumień XML i rekonstruuje obiektu.

Umożliwia także serializacji XML można serializować obiektów do strumieni XML, które są zgodne ze specyfikacją protokołu SOAP. Protokołu SOAP to protokół oparte na języku XML, zaprojektowany specjalnie w celu transportu wywołań procedur za pomocą języka XML.

Do serializacji lub deserializacji obiekty, użyj <xref:System.Xml.Serialization.XmlSerializer> klasy. Aby utworzyć klasy serializacji, należy użyć narzędzia definicji schematu XML.

## <a name="in-this-section"></a>W tej sekcji

[Wprowadzenie do serializacji XML](introducing-xml-serialization.md)  
Udostępnia ogólne definicji serializacji, zwłaszcza serializacji XML.

[Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)  
Instrukcje krok po kroku dotyczący dla serializacji obiektu.

[Instrukcje: Deserializacji obiektu](how-to-deserialize-an-object.md)  
Instrukcje krok po kroku deserializacji obiektu.

[Przykłady serializacji XML](examples-of-xml-serialization.md)  
Zawiera przykłady demonstrujące podstawy serializacji XML.

[Narzędzie definicji schematu XML i serializacja XML](the-xml-schema-definition-tool-and-xml-serialization.md)  
Opisuje sposób można utworzyć klasy, które będą zgodne z określonym schematem języka (XSD) definicji schematu XML lub do generowania schematu XML z PLiku dll za pomocą narzędzia definicji schematu XML.

[Kontrolowanie serializacji XML przy użyciu atrybutów](controlling-xml-serialization-using-attributes.md)  
Opisuje sposób kontroluje serializacji przy użyciu atrybutów.

[Atrybuty kontrolujące serializację XML](attributes-that-control-xml-serialization.md)  
Wyświetla listę atrybutów, które są używane do kontrolowania serializacji XML.

[Instrukcje: Określ nazwę elementu alternatywny Stream XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
Przedstawia informacje o zaawansowanym scenariuszu prezentujący do generowania wielu strumieni XML przez zastąpienie serializacji.

[Instrukcje: Kontrola serializacji w klasach pochodnych](how-to-control-serialization-of-derived-classes.md)  
Zawiera przykładowy sposób kontroluje serializacji w klasach pochodnych.

[Instrukcje: Kwalifikowanie elementu XML i nazw atrybutów XML](how-to-qualify-xml-element-and-xml-attribute-names.md)  
Opisuje sposób definiowania i kontrolować sposób, w których XML obszary nazw są używane w strumieniu XML.

[Serializacja XML z usługami internetowymi XML](xml-serialization-with-xml-web-services.md)  
W tym artykule wyjaśniono, jak serializacji XML jest używany w usługach sieci Web XML.

[Instrukcje: Serializacja obiektu jako Stream XML kodowany w formacie protokołu SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
Opisuje sposób używania <xref:System.Xml.Serialization.XmlSerializer> klasy w celu utworzenia zakodowany strumieni XML protokołu SOAP, które są zgodne z części 5 dokumentu World Wide Web Consortium (W3C) [proste obiektu dostępu protokołu (protokołu SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/).

[Instrukcje: Zastąp zakodowanego protokołu SOAP serializacji XML](how-to-override-encoded-soap-xml-serialization.md)  
Opisuje proces zastępowanie serializacji obiektów XML jako komunikaty protokołu SOAP.

[Atrybuty kontrolujące zakodowaną serializację SOAP](attributes-that-control-encoded-soap-serialization.md)  
Wyświetla listę atrybutów, które są używane do kontrolowania serializacji kodowany w formacie protokołu SOAP.

[\<system.xml.serialization> Element](system-xml-serialization-element.md)  
Element konfiguracji najwyższego poziomu do sterowania serializacji XML.

[\<dateTimeSerialization> Element](datetimeserialization-element.md)  
Określa tryb serializacji <xref:System.DateTime> obiektów.

[\<schemaImporterExtensions> Element](schemaimporterextensions-element.md)  
Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.

[\<add> Element for \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)  
Dodaje typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> klasy.

## <a name="related-sections"></a>Sekcje pokrewne

[Usługi sieci Web XML utworzone za pomocą platformy ASP.NET i klientów usługi sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))  
Zawiera tematy, które opisują, a wyjaśniają, jak program usług XML sieci Web za pomocą programu ASP.NET.

## <a name="see-also"></a>Zobacz także

- [Serializacja binarna](binary-serialization.md)
