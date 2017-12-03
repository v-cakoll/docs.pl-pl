---
title: "Atrybuty, które sterowania serializacją użyciu zakodowanego protokołu SOAP"
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
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 358b635ee74699d9d427e8fac23fabd70c6cfa98
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
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
 [XML i serializacji SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Porady: szeregowania obiektu jako strumień SOAP zakodowane w formacie XML](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [Porady: Zastąp serializacji XML użyciu zakodowanego protokołu SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [Atrybuty](../../../docs/standard/attributes/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Porady: szeregowania obiektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Porady: deserializacji obiektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
