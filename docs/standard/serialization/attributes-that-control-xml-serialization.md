---
title: Atrybuty kontrolujące serializację XML
description: Ten artykuł zawiera atrybuty, które można zastosować do klas i elementów członkowskich klasy w celu kontrolowania sposobu serializacji lub deserializacji instancji klasy XmlSerializer.
ms.date: 03/30/2017
helpviewer_keywords:
- classes, serializing
- XmlSerializer class, serializing
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
- XML Schema, serializing
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
ms.openlocfilehash: fbc42ff696107f4a1b06d3611fc97a09cc4a3542
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84276702"
---
# <a name="attributes-that-control-xml-serialization"></a>Atrybuty kontrolujące serializację XML
Można zastosować atrybuty w poniższej tabeli do klas i elementów członkowskich klasy, aby kontrolować sposób, w jaki <xref:System.Xml.Serialization.XmlSerializer> Serializacja lub deserializacji wystąpienia klasy. Aby zrozumieć, jak te atrybuty kontrolują serializacji XML, zobacz [Kontrolowanie serializacji XML przy użyciu atrybutów](controlling-xml-serialization-using-attributes.md).  
  
 Te atrybuty mogą również kontrolować wiadomości protokołu SOAP literału stylu generowanych przez usługi sieci Web XML. Aby uzyskać więcej informacji na temat stosowania tych atrybutów do metody usług sieci Web XML, zobacz [serializacji XML z usługami sieci Web XML](xml-serialization-with-xml-web-services.md).  
  
 Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty](../attributes/index.md).  
  
|Atrybut|Dotyczy|Określa|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.XmlAnyAttributeAttribute>|Pole publiczne, właściwość, parametru lub zwracanej wartości, która zwraca tablicę <xref:System.Xml.XmlAttribute> obiektów.|Podczas deserializacji, tablica będzie wypełniona <xref:System.Xml.XmlAttribute> obiektów, które reprezentują wszystkie atrybuty XML nieznany schematu.|  
|<xref:System.Xml.Serialization.XmlAnyElementAttribute>|Pole publiczne, właściwość, parametru lub zwracanej wartości, która zwraca tablicę <xref:System.Xml.XmlElement> obiektów.|Podczas deserializacji, tablica jest wypełniany <xref:System.Xml.XmlElement> obiekty reprezentujące wszystkie elementy XML nieznany schematu.|  
|<xref:System.Xml.Serialization.XmlArrayAttribute>|Pole publiczne, właściwość, parametr lub wartość zwracana zwracająca tablicę obiektów złożonych.|Zostanie wygenerowany tablicy elementów członkowskich jako elementy członkowskie tablicy XML.|  
|<xref:System.Xml.Serialization.XmlArrayItemAttribute>|Pole publiczne, właściwość, parametr lub wartość zwracana zwracająca tablicę obiektów złożonych.|Typy pochodne, które mogą być wstawiane do tablicy. Zwykle stosowana w połączeniu z <xref:System.Xml.Serialization.XmlArrayAttribute> .|  
|<xref:System.Xml.Serialization.XmlAttributeAttribute>|Pole publiczne, właściwość, parametru lub wartości zwracanej.|Element członkowski będzie serializowana jako atrybut XML.|  
|<xref:System.Xml.Serialization.XmlChoiceIdentifierAttribute>|Pole publiczne, właściwość, parametru lub wartości zwracanej.|Element członkowski może dodatkowo rozróżniane przy użyciu wyliczenia.|  
|<xref:System.Xml.Serialization.XmlElementAttribute>|Pole publiczne, właściwość, parametru lub wartości zwracanej.|Pole lub właściwość będzie serializowana jako XML element.|  
|<xref:System.Xml.Serialization.XmlEnumAttribute>|Pole publicznej jest identyfikatorem wyliczenia.|Nazwa elementu element członkowski wyliczenia.|  
|<xref:System.Xml.Serialization.XmlIgnoreAttribute>|Właściwości publiczne i pola.|Właściwości lub pól mają być ignorowane, gdy klasa zawierająca jest serializowana.|  
|<xref:System.Xml.Serialization.XmlIncludeAttribute>|Publiczna uzyskiwany deklaracje klas i zwracanymi wartościami metod publicznych w dokumentach sieci Web Services Description Language (WSDL).|Klasa mają zostać uwzględnione podczas generowania schematów (do rozpoznany po serializacji).|  
|<xref:System.Xml.Serialization.XmlRootAttribute>|Klasa publiczna deklaracji.|Formanty XML serializacji w celu atrybutu jako element główny XML. Użyj atrybutu do dalszego określenia nazwy obszaru nazw i elementu.|  
|<xref:System.Xml.Serialization.XmlTextAttribute>|Właściwości publiczne i pola.|Właściwości lub pól powinien zostać Zserializowany jako tekst XML.|  
|<xref:System.Xml.Serialization.XmlTypeAttribute>|Klasa publiczna deklaracji.|Nazwa i nazw typu XML.|  
  
 Oprócz tych atrybutów, które znajdują się w <xref:System.Xml.Serialization> przestrzeni nazw, można także zastosować <xref:System.ComponentModel.DefaultValueAttribute> atrybut do pola. **DefaultValueAttribute —** ustawia wartość, która zostanie automatycznie przypisana do elementu członkowskiego, jeśli nie określono wartości.  
  
 Aby kontrolować zakodowaną serializacji XML protokołu SOAP, zobacz atrybuty kontrolujące [zakodowaną serializację protokołu SOAP](attributes-that-control-encoded-soap-serialization.md).  
  
## <a name="see-also"></a>Zobacz także

- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Kontrolowanie serializacji XML przy użyciu atrybutów](controlling-xml-serialization-using-attributes.md)
- [Instrukcje: Określanie alternatywnej nazwy elementu dla strumienia XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)
- [Instrukcje: Deserializacja obiektu](how-to-deserialize-an-object.md)
