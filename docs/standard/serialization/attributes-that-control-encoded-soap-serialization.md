---
title: Atrybuty kontrolujące zakodowaną serializację SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 2961d9abc6c32e78b5a61e8f2bbea5cfcf6677bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794943"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>Atrybuty kontrolujące zakodowaną serializację SOAP

Dokument organizacja World Wide Web Consortium (W3C) o nazwie [Simple Object Access Protocol (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) zawiera sekcję opcjonalną (sekcja 5) opisującą sposób kodowania parametrów protokołu SOAP. Aby zachować zgodność z sekcją 5 specyfikacji, należy użyć specjalnego zestawu atrybutów znalezionych w <xref:System.Xml.Serialization> przestrzeni nazw. Zastosuj te atrybuty stosownie do klas i elementów członkowskich klas, a następnie użyj <xref:System.Xml.Serialization.XmlSerializer> do serializacji wystąpień klasy lub klas.

W poniższej tabeli przedstawiono atrybuty, w których można je zastosować i co robią. Aby uzyskać więcej informacji o używaniu tych atrybutów do kontrolowania serializacji XML, zobacz [How to: deserializacji obiektu jako strumień XML szyfrowany przy użyciu protokołu SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) i [instrukcje: zastępowanie ZAKODOWANEJ serializacji XML protokołu SOAP](how-to-override-encoded-soap-xml-serialization.md).

Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty](../../../docs/standard/attributes/index.md).

|Atrybut|Informacje zawarte w tym artykule dotyczą|Określa|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|Pole publiczne, właściwość, parametru lub wartości zwracanej.|Składowa klasy będzie serializowana jako atrybut XML.|
|<xref:System.Xml.Serialization.SoapElementAttribute>|Pole publiczne, właściwość, parametru lub wartości zwracanej.|Klasa będzie serializowana jako XML element.|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|Pole publicznej jest identyfikatorem wyliczenia.|Nazwa elementu element członkowski wyliczenia.|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|Właściwości publiczne i pola.|Właściwości lub pól mają być ignorowane, gdy klasa zawierająca jest serializowana.|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|Klasa pochodna publicznego deklaracje i metod publicznych w dokumentach sieci Web Services Description Language (WSDL).|Typ mają zostać uwzględnione podczas generowania schematów (do rozpoznany po serializacji).|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|Klasa publiczna deklaracji.|Klasa powinien zostać Zserializowany jako typ XML.|

## <a name="see-also"></a>Zobacz też

- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
- [Instrukcje: Serializacja obiektu jako kodowanego strumienia XML protokołu SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [Instrukcje: Przesłanianie zakodowanej serializacji XML protokołu SOAP](how-to-override-encoded-soap-xml-serialization.md)
- [Atrybuty](../../../docs/standard/attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)
- [Instrukcje: Deserializacja obiektu](how-to-deserialize-an-object.md)
