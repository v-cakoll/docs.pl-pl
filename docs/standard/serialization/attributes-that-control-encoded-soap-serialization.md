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
ms.openlocfilehash: 7b5a48003ff9bfb398c05c8d70a9076d49ad83d6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44127774"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>Atrybuty kontrolujące zakodowaną serializację SOAP

Dokument World Wide Web Consortium (W3C) o nazwie [proste obiektu dostępu protokołu (protokołu SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) zawiera sekcję opcjonalną (sekcja 5), w tym artykule opisano, jak można zakodować parametry protokołu SOAP. Aby jest zgodny z sekcji 5 specyfikacji, należy użyć specjalnego zestawu atrybutów w <xref:System.Xml.Serialization> przestrzeni nazw. Zastosuj te atrybuty właściwe dla klas i składowych klas, a następnie użyj <xref:System.Xml.Serialization.XmlSerializer> do serializacji wystąpień klasy lub klas.

W poniższej tabeli przedstawiono atrybuty, których może być stosowana, i co robią. Aby uzyskać więcej informacji o korzystaniu z tych atrybutów do kontroli serializacji XML, zobacz [jak: serializacja obiektu jako protokołu SOAP-Encoded XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) i [jak: Przesłoń zakodowany serializacji XML protokołu SOAP](how-to-override-encoded-soap-xml-serialization.md).

Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty](../../../docs/standard/attributes/index.md).

|Atrybut|Informacje zawarte w tym artykule dotyczą|Określa|
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
- [Atrybuty](../../../docs/standard/attributes/index.md)  
- <xref:System.Xml.Serialization.XmlSerializer>  
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)  
- [Instrukcje: Deserializacja obiektu](how-to-deserialize-an-object.md)
