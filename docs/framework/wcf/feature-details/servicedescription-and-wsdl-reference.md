---
title: Odwołania do elementu ServiceDescription i kodu WSDL
ms.date: 03/30/2017
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
ms.openlocfilehash: 6690bea3d3df0f39a5581c3a6c14723c0f30f40c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182887"
---
# <a name="servicedescription-and-wsdl-reference"></a>Odwołania do elementu ServiceDescription i kodu WSDL
W tym temacie opisano, jak Windows Communication Foundation (WCF) mapuje dokumentów sieci Web Services Description Language (WSDL), do i z <xref:System.ServiceModel.Description.ServiceDescription> wystąpień.  
  
## <a name="how-servicedescription-maps-to-wsdl-11"></a>Sposób mapowania modelu ServiceDescription WSDL 1.1  
 Usługi WCF można użyć do wyeksportowania dokumenty WSDL z <xref:System.ServiceModel.Description.ServiceDescription> wystąpienia usługi. Dokumenty WSDL są generowane automatycznie dla usługi, gdy opublikujesz punkty końcowe metadanych.  
  
 Możesz również zaimportować <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień <xref:System.ServiceModel.Description.ContractDescription> wystąpień i <xref:System.ServiceModel.Channels.Binding> wystąpień z dokumenty WSDL przy użyciu `WsdlImporter` typu.  
  
 Dokumenty WSDL, eksportowane przez architekturę WCF, importować żadnych definicji schematu XML używane z zewnętrznych dokumentów schematu XML. Oddzielny dokument schematu XML jest eksportowany dla każdej przestrzeni nazw docelowym, używane przez typy danych w usłudze. Podobnie, oddzielny dokument WSDL jest eksportowana dla każdej przestrzeni nazw docelowym usługi umów dotyczących użycia.  
  
### <a name="servicedescription"></a>ServiceDescription  
 A <xref:System.ServiceModel.Description.ServiceDescription> mapuje wystąpienia `wsdl:service` elementu. A <xref:System.ServiceModel.Description.ServiceDescription> wystąpienie zawiera zbiór <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia, aby mapować każdy pojedynczych `wsdl:port` elementów.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:service` /@name Wartość dla usługi.|  
|`Namespace`|Docelowy obszar nazw dla `wsdl:service` definicji usługi.|  
|`Endpoints`|`wsdl:port` Definicji usługi.|  
  
### <a name="serviceendpoint"></a>ServiceEndpoint  
 A <xref:System.ServiceModel.Description.ServiceEndpoint> mapuje wystąpienia `wsdl:port` elementu. A <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienie zawiera adres, powiązanie i kontrakt.  
  
 Zachowań punktu końcowego, które implementują <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejsu można zmodyfikować `wsdl:port` elementu dla punktu końcowego są dołączone.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:port` /@name Wartość punktu końcowego i `wsdl:binding` /@name wartość dla powiązania punktu końcowego.|  
|`Address`|Adres `wsdl:port` definicji punktu końcowego.<br /><br /> Transport dla punktu końcowego określa format adresu. Na przykład dla transportu obsługiwane WCF możliwe adresu protokołu SOAP lub odwołania do punktu końcowego.|  
|`Binding`|`wsdl:binding` Definicji punktu końcowego.<br /><br /> W odróżnieniu od `wsdl:binding` definicje, powiązań w usłudze WCF nie są związane z dowolnym jednego kontraktu.|  
|`Contract`|`wsdl:portType` Definicji punktu końcowego.|  
|`Behaviors`|Zachowań punktu końcowego, które implementują <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejsu można zmodyfikować `wsdl:port` dla punktu końcowego.|  
  
### <a name="bindings"></a>Powiązania  
 Wystąpienie obiektu binding dla `ServiceEndpoint` mapuje wystąpienia `wsdl:binding` definicji. W odróżnieniu od `wsdl:binding` definicje, które muszą być skojarzone z określonym `wsdl:portType` definicji, powiązaniami WCF są niezależne od wszelkich kontraktu.  
  
 Powiązanie składa się z kolekcji elementów wiązania. Każdy element w tym artykule opisano niektóre aspekty jak punkt końcowy komunikuje się z klientami. Ponadto ma powiązanie <xref:System.ServiceModel.Channels.MessageVersion> oznacza <xref:System.ServiceModel.EnvelopeVersion> i <xref:System.ServiceModel.Channels.AddressingVersion> dla punktu końcowego.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|Używane w domyślną nazwę punktu końcowego, czyli nazwa powiązania z nazwą kontraktu dołączany oddzielone znakiem podkreślenia.|  
|`Namespace`|`targetNamespace` Dla `wsdl:binding` definicji.<br /><br /> Przy imporcie, jeśli zasady jest podłączona do portu WSDL przestrzeni nazw importowanych powiązania mapuje `targetNamespace` dla `wsdl:port` definicji.|  
|`BindingElementCollection`, zwrócone przez `CreateBindingElements`() — metoda|Różne rozszerzenia specyficznego dla domeny `wsdl:binding` definicji, zazwyczaj asercji zasad.|  
|`MessageVersion`|`EnvelopeVersion` i `AddressingVersion` dla punktu końcowego.<br /><br /> Gdy `MessageVersion.None` określono Powiązanie WSDL nie zawiera powiązań protokołu SOAP i WSDL port nie zawiera usługi WS-Addressing zawartości. To ustawienie jest zazwyczaj używana dla zwykłych starych punktów końcowych XML (POX).|  
  
#### <a name="bindingelements"></a>Elementy BindingElements  
 Elementy powiązania dla powiązania punktu końcowego mapowania różnych rozszerzenia WSDL w `wsdl:binding`, takich jak asercji zasad.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement> Dla powiązania określa transportu identyfikatora URI (Uniform Resource) dla powiązania protokołu SOAP.  
  
#### <a name="addressingversion"></a>Wersja adresowania mogła być  
 `AddressingVersion` w powiązaniu mapuje do wersji adresowania używane w `wsd:port`. Usługi WCF obsługuje SOAP 1.1 i SOAP 1.2 adresów i WS-Addressing 08/2004 i odwołania do punktu końcowego usługi WS-Addressing 1.0.  
  
#### <a name="envelopeversion"></a>EnvelopeVersion  
 `EnvelopeVersion` w powiązaniu mapy wersję protokołu SOAP jest używany w `wsdl:binding`. Usługi WCF obsługuje powiązania SOAP 1.1 i SOAP 1.2.  
  
### <a name="contracts"></a>Kontrakty  
 <xref:System.ServiceModel.Description.ContractDescription> Wystąpienie `ServiceEndpoint` mapuje wystąpienia `wsdl:portType`. A `ContractDescription` wystąpienia w tym artykule opisano wszystkie operacje dla danego kontraktu.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` /@name Wartości dla kontraktu.|  
|`Namespace`|Docelowy obszar nazw dla `wsdl:portType` definicji.|  
|`SessionMode`|`wsdl:portType` /@msc:usingSession Wartości dla kontraktu. Ten atrybut jest rozszerzenia WSDL 1.1 dla programu WCF.|  
|`Operations`|`wsdl:operation` Definicje dla kontraktu.|  
  
### <a name="operations"></a>Operacje  
 <xref:System.ServiceModel.Description.OperationDescription> Mapuje wystąpienia `wsdl:portType` / `wsdl:operation`. `OperationDescription` Zawiera zbiór `MessageDescription` wystąpień, które opisują komunikaty dotyczące operacji.  
  
 Dwa zachowania operacja intensywnie uczestniczyć w sposób `OperationDescription` jest mapowana na dokument WSDL: `DataContractSerializerOperationBehavior` i `XmlSerializerOperationBehavior`.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` /@name Wartość dla tej operacji.|  
|`ProtectionLevel`|Ochrona potwierdzenia w zasadach zabezpieczeń dołączonych do `wsdl:binding/wsdl:operation` komunikatów dla tej operacji.|  
|`IsInitiating`|`wsdl:portType` / `wsdl:operation` /@msc:isInitiating Wartość dla tej operacji. Ten atrybut jest rozszerzenia WSDL 1.1 dla programu WCF.|  
|`IsTerminating`|`wsdl:portType` / `wsdl:operation` /@msc:isTerminating Wartość dla tej operacji. Ten atrybut jest rozszerzenia WSDL 1.1 dla programu WCF.|  
|`Messages`|`wsdl:portType` / `wsdl:operation` / `wsdl:input` i `wsdl:portType` / `wsdl:operation` / `wsdl:output` komunikaty dotyczące operacji.|  
|`Faults`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` Definicje dla tej operacji.|  
|`Behaviors`|`DataContractSerializerOperationBehavior` i `XmlSerializerOperationBehavior` powiązanie operacji i komunikaty operacji.|  
  
#### <a name="the-datacontractserializeroperationbehavior"></a>DataContractSerializerOperationBehavior  
 `DataContractSerializerOperationBehavior` Jest operacją `IWsdlExportExtension` implementacji, które Eksportuje wiadomości WSDL i powiązanie dla tej operacji. Typy schematu XML są eksportowane za pomocą `XsdDataContractExporter`. `DataContractSerializerOperationBehavior` Określa również eksporter użycia, stylu i schematu i importera, do użycia dla tej operacji.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`DataContractFormatAttribute`|`Style` Mapuje właściwość dla tego atrybutu `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style wartość dla tej operacji.<br /><br /> `DataContractSerializerOperationBehavior` Obsługuje użycie literału typu schematu w formacie WSDL.|  
  
#### <a name="the-xmlserializeroperationbehavior"></a>XmlSerializerOperationBehavior  
 `XmlSerializerOperationBehavior` Jest operacją `IWsdlExportExtension` implementacji, które Eksportuje wiadomości WSDL i powiązanie dla tej operacji. Typy schematu XML są eksportowane za pomocą `XmlSchemaExporter`. `XmlSerializerOperationBehavior` Określa również eksporter użycia, stylu i schematu i importera, do użycia dla tej operacji.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`XmlSerializerFormatAttribute`|`Style` Mapuje właściwość dla tego atrybutu `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style wartość dla tej operacji.<br /><br /> `Use` Mapuje właściwość dla tego atrybutu `wsdl:binding` / `wsdl:operation` / `soap:operation`/ */@use wartości dla wszystkich komunikatów w ramach operacji.|  
  
### <a name="messages"></a>Komunikaty  
 A `MessageDescription` mapuje wystąpienia `wsdl:message` która odwołuje się do niej `wsdl:portType` / `wsdl:operation` / `wsdl:input` lub `wsdl:portType` / `wsdl:operation` / `wsdl:output`komunikatu w operacji. Element `MessageDescription` zawiera nagłówki i treść.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Action`|Akcja SOAP lub WS-Addressing dla wiadomości.<br /><br /> Uwaga tej operacji, korzystających z ciąg akcji "*" nie są reprezentowane w języku WSDL.|  
|`Direction`|`MessageDirection.Input` mapuje `wsdl:input`.<br /><br /> `MessageDirection.Output` mapuje `wsdl:output`.|  
|`ProtectionLevel`|Ochrona potwierdzenia w zasadach zabezpieczeń dołączonych do `wsdl:message` definicji dla tego komunikatu.|  
|`Body`|Treść wiadomości.|  
|`Headers`|Nagłówki dla wiadomości.|  
|`ContractDescription.Name`, `OperationContract.Name`|Podczas eksportowania, użyty do wyprowadzenia `wsdl:message` /@name wartości.|  
  
#### <a name="message-body"></a>Treść komunikatu  
 A `MessageBodyDescription` mapuje wystąpienia `wsdl:message` / `wsdl:part` definicje dla treści wiadomości. Treść komunikatu może zostać opakowany lub bez.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`WrapperName`|Jeśli styl nie jest RPC, a następnie `WrapperName` mapuje do nazwy elementu odwołuje się `wsdl:message` / `wsdl:part` z @name ustawiona na "parameters".|  
|`WrapperNamespace`|Jeśli styl nie jest RPC, a następnie `WrapperNamespace` mapuje przestrzeń nazw elementu dla `wsdl:message` / `wsdl:part` z @name ustawiona na "parameters".|  
|`Parts`|Części wiadomości dla tej treści komunikatu.|  
|`ReturnValue`|Element podrzędny element otoki, jeśli element otoki istnieje (styl opakowanym dokumentem lub stylu RPC), w przeciwnym razie pierwszy `wsdl:message` / `wsdl:part` w komunikacie.|  
  
#### <a name="message-parts"></a>Części wiadomości  
 A `MessagePartDescription` mapuje wystąpienia `wsdl:message` / `wsdl:part` i typ schematu XML lub elementu, który wskazuje części komunikatu.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|`wsd:message` / `wsdl:part` /@name Wartość część wiadomości oraz nazwa elementu, który wskazuje części komunikatu.|  
|`Namespace`|Przestrzeń nazw elementu, który wskazuje części komunikatu.|  
|`Index`|Indeks `wsdl:message` / `wsdl:part` dla wiadomości.|  
|`ProtectionLevel`|Ochrona potwierdzenia w zasadach zabezpieczeń dołączonych do `wsdl:message` definicji w tej części wiadomości. Zasady są parametryzowane wskaż część szczegółowy komunikat o błędzie.|  
|`MessageType`|Typ schematu XML element, który wskazuje części komunikatu.|  
  
#### <a name="message-headers"></a>Nagłówki wiadomości  
 A `MessageHeaderDescription` wystąpienie jest również mapowana na części komunikatu `soap:header` powiązanie dla części komunikatu.  
  
### <a name="faults"></a>Błędy  
 A `FaultDescription` mapuje wystąpienia `wsdl:portType` / `wsdl:operation` / `wsdl:fault` definicji i związanych z nią `wsdl:message` definicji. `wsdl:message` Zostanie dodany do tej samej docelowego obszaru nazw jako jego skojarzony typ portu WSDL. `wsdl:message` Ma jeden komunikat o część o nazwie "szczegóły", który wskazuje element schematu XML, który odpowiada `DefaultType` wartości właściwości dla `FaultDescription` wystąpienia.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` /@name Wartości błędu.|  
|`Namespace`|Przestrzeń nazw elementu schematu XML, który wskazuje części komunikatu szczegóły błędów.|  
|`Action`|Akcja SOAP lub WS-Addressing błędu.|  
|`ProtectionLevel`|Ochrona potwierdzenia w zasadach zabezpieczeń dołączonych do `wsdl:message` definicję dla tego błędu.|  
|`DetailType`|Typ schematu XML element, który wskazuje części komunikatu szczegółów.|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|Użyty do wyprowadzenia `wsdl:message` /@name wartość komunikat o błędzie.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description>
