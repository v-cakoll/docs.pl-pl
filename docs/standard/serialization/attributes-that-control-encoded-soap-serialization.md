---
title: Atrybuty kontrolujące zakodowaną serializację SOAP
description: W tym artykule wymieniono specjalny zestaw atrybutów znalezionych w przestrzeni nazw System. XML. Serialization, które są konieczne do zgodności ze specyfikacją protokołu SOAP.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: d9a4631189d348c02ab36054257a54c9c4673018
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289671"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>Atrybuty kontrolujące zakodowaną serializację SOAP

Dokument organizacja World Wide Web Consortium (W3C) o nazwie [Simple Object Access Protocol (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) zawiera sekcję opcjonalną (sekcja 5) opisującą sposób kodowania parametrów protokołu SOAP. Aby zachować zgodność z sekcją 5 specyfikacji, należy użyć specjalnego zestawu atrybutów znalezionych w <xref:System.Xml.Serialization> przestrzeni nazw. Zastosuj te atrybuty stosownie do klas i elementów członkowskich klas, a następnie użyj <xref:System.Xml.Serialization.XmlSerializer> do serializacji wystąpień klasy lub klas.

W poniższej tabeli przedstawiono atrybuty, w których można je zastosować i co robią. Aby uzyskać więcej informacji o używaniu tych atrybutów do kontrolowania serializacji XML, zobacz [How to: deserializacji obiektu jako strumień XML szyfrowany przy użyciu protokołu SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) i [instrukcje: zastępowanie ZAKODOWANEJ serializacji XML protokołu SOAP](how-to-override-encoded-soap-xml-serialization.md).

Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty](../attributes/index.md).

|Atrybut|Dotyczy|Określa|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|Pole publiczne, właściwość, parametru lub wartości zwracanej.|Składowa klasy będzie serializowana jako atrybut XML.|
|<xref:System.Xml.Serialization.SoapElementAttribute>|Pole publiczne, właściwość, parametru lub wartości zwracanej.|Klasa będzie serializowana jako XML element.|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|Pole publicznej jest identyfikatorem wyliczenia.|Nazwa elementu element członkowski wyliczenia.|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|Właściwości publiczne i pola.|Właściwości lub pól mają być ignorowane, gdy klasa zawierająca jest serializowana.|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|Klasa pochodna publicznego deklaracje i metod publicznych w dokumentach sieci Web Services Description Language (WSDL).|Typ mają zostać uwzględnione podczas generowania schematów (do rozpoznany po serializacji).|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|Klasa publiczna deklaracji.|Klasa powinien zostać Zserializowany jako typ XML.|

## <a name="see-also"></a>Zobacz także

- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
- [Instrukcje: Serializacja obiektu jako kodowanego strumienia XML protokołu SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [Instrukcje: Przesłanianie zakodowanej serializacji XML protokołu SOAP](how-to-override-encoded-soap-xml-serialization.md)
- [Atrybuty](../attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)
- [Instrukcje: Deserializacja obiektu](how-to-deserialize-an-object.md)
