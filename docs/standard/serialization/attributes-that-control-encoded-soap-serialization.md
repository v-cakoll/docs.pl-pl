---
title: Atrybuty, które sterowania serializacją użyciu zakodowanego protokołu SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: b7f0d8bf7c7c1013937f7ce0a87c326b707fbc6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582425"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>Atrybuty, które sterowania serializacją użyciu zakodowanego protokołu SOAP 
Dokument konsorcjum World Wide Web (www.w3.org) o nazwie "Simple Object Access Protocol (SOAP) 1.1" zawiera sekcja opcjonalna (sekcja 5), opisujące, jak mogą być kodowane parametry protokołu SOAP. Aby jest zgodny z sekcji 5 specyfikacji, należy użyć specjalnego zestawu atrybutów w <xref:System.Xml.Serialization> przestrzeni nazw. Zastosuj te atrybuty odpowiednio do klas i członków klas, a następnie użyj <xref:System.Xml.Serialization.XmlSerializer> do serializacji wystąpienia klasy lub klas.  
  
 W poniższej tabeli przedstawiono atrybuty, których może być stosowana, a ich działania. Aby uzyskać więcej informacji o korzystaniu z tych atrybutów do formantu serializacji XML, zobacz [jak: szeregowania obiektu jako SOAP-Encoded strumień XML](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) i [jak: zastąpienie zakodowane serializacji XML protokołu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md).  
  
 Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybutów](../../../docs/standard/attributes/index.md).  
  
|Atrybut|Informacje zawarte w tym artykule dotyczą|Określa|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|Pole publiczne, właściwość, parametru lub wartości zwracanej.|Składowa klasy będzie serializowana jako atrybut XML.|  
|<xref:System.Xml.Serialization.SoapElementAttribute>|Pole publiczne, właściwość, parametru lub wartości zwracanej.|Klasa będzie serializowana jako XML element.|  
|<xref:System.Xml.Serialization.SoapEnumAttribute>|Pole publicznej jest identyfikatorem wyliczenia.|Nazwa elementu element członkowski wyliczenia.|  
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|Właściwości publiczne i pola.|Właściwości lub pól mają być ignorowane, gdy klasa zawierająca jest serializowana.|  
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|Klasa pochodna publicznego deklaracje i metod publicznych w dokumentach sieci Web Services Description Language (WSDL).|Typ mają zostać uwzględnione podczas generowania schematów (do rozpoznany po serializacji).|  
|<xref:System.Xml.Serialization.SoapTypeAttribute>|Klasa publiczna deklaracji.|Klasa powinien zostać Zserializowany jako typ XML.|  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Instrukcje: Serializacja obiektu jako kodowanego strumienia XML protokołu SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [Instrukcje: Przesłanianie zakodowanej serializacji XML protokołu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [Atrybuty](../../../docs/standard/attributes/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Instrukcje: Serializacja obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Instrukcje: Deserializacja obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
