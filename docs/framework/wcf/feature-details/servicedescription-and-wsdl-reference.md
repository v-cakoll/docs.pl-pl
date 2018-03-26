---
title: Odwołania do elementu ServiceDescription i kodu WSDL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7eadfaaae920071092f569fe2b8882875ed9497f
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="servicedescription-and-wsdl-reference"></a>Odwołania do elementu ServiceDescription i kodu WSDL
W tym temacie opisano sposób [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mapy dokumentów sieci Web Services Description Language (WSDL) do i z <xref:System.ServiceModel.Description.ServiceDescription> wystąpień.  
  
## <a name="how-servicedescription-maps-to-wsdl-11"></a>Sposób mapowania ServiceDescription WSDL 1.1  
 Można użyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do eksportu WSDL dokumentów z <xref:System.ServiceModel.Description.ServiceDescription> wystąpienia usługi. Dokumentów WSDL są generowane automatycznie dla usługi publikowania punkty końcowe metadanych.  
  
 Możesz również zaimportować <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpień, <xref:System.ServiceModel.Description.ContractDescription> wystąpień, i <xref:System.ServiceModel.Channels.Binding> wystąpień z dokumentów WSDL za pomocą `WsdlImporter` typu.  
  
 Dokumentów WSDL wyeksportowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zaimportować żadnych definicji schematu XML używane z zewnętrznych dokumentów schematu XML. Dla każdej docelowej przestrzeni nazw, typów danych używanych w usłudze eksportowany jest oddzielny dokument schematu XML. Podobnie, wyeksportowaniu oddzielny dokument WSDL dla każdej docelowej przestrzeni nazw usługi umów użycia.  
  
### <a name="servicedescription"></a>ServiceDescription  
 A <xref:System.ServiceModel.Description.ServiceDescription> mapuje wystąpienia `wsdl:service` elementu. A <xref:System.ServiceModel.Description.ServiceDescription> wystąpienia zawiera kolekcję <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia każdej mapowane do poszczególnych `wsdl:port` elementów.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:service` /@name Wartość dla usługi.|  
|`Namespace`|Przestrzeń nazw targetNamespace dla `wsdl:service` definicji usługi.|  
|`Endpoints`|`wsdl:port` Definicji usługi.|  
  
### <a name="serviceendpoint"></a>ServiceEndpoint  
 A <xref:System.ServiceModel.Description.ServiceEndpoint> mapuje wystąpienia `wsdl:port` elementu. A <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienie zawiera adres, powiązania i kontrakt.  
  
 Zachowania punktu końcowego, które implementują <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejsu można modyfikować `wsdl:port` elementu są one dołączone do punktu końcowego.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:port` /@name Wartość dla punktu końcowego i `wsdl:binding` /@name wartość dla powiązania punktu końcowego.|  
|`Address`|Adres `wsdl:port` definicji punktu końcowego.<br /><br /> Transport dla punktu końcowego określa format adresu. Na przykład w przypadku [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-obsługiwanych transportów adres protokołu SOAP i odwołanie do punktu końcowego.|  
|`Binding`|`wsdl:binding` Definicji punktu końcowego.<br /><br /> W odróżnieniu od `wsdl:binding` definicje, powiązania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie są związane z dowolnym jeden kontrakt.|  
|`Contract`|`wsdl:portType` Definicji punktu końcowego.|  
|`Behaviors`|Zachowania punktu końcowego, które implementują <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejsu można modyfikować `wsdl:port` dla punktu końcowego.|  
  
### <a name="bindings"></a>Powiązania  
 Wystąpienie powiązania dla `ServiceEndpoint` mapuje wystąpienia `wsdl:binding` definicji. W odróżnieniu od `wsdl:binding` definicje, które muszą być skojarzone z określonym `wsdl:portType` definicji, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania są niezależne od wszelkich kontraktu.  
  
 Powiązanie składa się z kolekcji elementów wiązania. Każdy element opisano niektóre aspekty jak punkt końcowy komunikuje się z klientami. Ponadto ma powiązanie <xref:System.ServiceModel.Channels.MessageVersion> wskazujące <xref:System.ServiceModel.EnvelopeVersion> i <xref:System.ServiceModel.Channels.AddressingVersion> dla punktu końcowego.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|Używane w domyślnej nazwy punktu końcowego, będący nazwą powiązanie o nazwie kontraktu dołączany oddzielone znaku podkreślenia.|  
|`Namespace`|`targetNamespace` Dla `wsdl:binding` definicji.<br /><br /> Importu, jeśli zasady jest podłączony do portu WSDL nazw powiązania importowanych mapuje `targetNamespace` dla `wsdl:port` definicji.|  
|`BindingElementCollection`, zwrócony przez `CreateBindingElements`— metoda)|Różne rozszerzenia specyficznego dla domeny `wsdl:binding` definicji, zwykle potwierdzeń zasad.|  
|`MessageVersion`|`EnvelopeVersion` i `AddressingVersion` dla punktu końcowego.<br /><br /> Gdy `MessageVersion.None` określono Powiązanie WSDL nie zawiera powiązaniem SOAP i portu WSDL nie zawiera zawartości WS-Addressing. To ustawienie jest zazwyczaj używane do zwykłego stare punkty końcowe XML (POX).|  
  
#### <a name="bindingelements"></a>Elementy BindingElements  
 Elementy powiązania dla powiązania punktu końcowego mapowania różnych rozszerzenia WSDL w `wsdl:binding`, takich jak potwierdzeń zasad.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement> Dla powiązania określa transportu identyfikatora URI (Uniform Resource) dla powiązania SOAP.  
  
#### <a name="addressingversion"></a>Wersja adresowania mogła być  
 `AddressingVersion` Dla powiązania mapy do wersji adresowania używane w `wsd:port`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje SOAP 1.1 i SOAP 1.2 adresy i WS-Addressing 08/2004 i odwołania do punktu końcowego usługi WS-Addressing 1.0.  
  
#### <a name="envelopeversion"></a>EnvelopeVersion  
 `EnvelopeVersion` Na powiązanie mapy do wersji SOAP używane w `wsdl:binding`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje powiązania SOAP 1.1 i SOAP 1.2.  
  
### <a name="contracts"></a>Kontrakty  
 <xref:System.ServiceModel.Description.ContractDescription> Wystąpienie `ServiceEndpoint` mapuje wystąpienia `wsdl:portType`. A `ContractDescription` wystąpienia opisano wszystkie operacje dla danego kontraktu.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` /@name Wartości dla kontraktu.|  
|`Namespace`|Przestrzeń nazw targetNamespace dla `wsdl:portType` definicji.|  
|`SessionMode`|`wsdl:portType` /@msc:usingSession Wartości dla kontraktu. Ten atrybut jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozszerzenia WSDL 1.1.|  
|`Operations`|`wsdl:operation` Definicje kontraktu.|  
  
### <a name="operations"></a>Operacje  
 <xref:System.ServiceModel.Description.OperationDescription> Mapuje wystąpienia `wsdl:portType` / `wsdl:operation`. `OperationDescription` Zawiera kolekcję `MessageDescription` wystąpień, które opisują komunikaty dla operacji.  
  
 Dwa zachowania operacji silnie uczestniczyć w sposób `OperationDescription` jest mapowany na dokument WSDL: `DataContractSerializerOperationBehavior` i `XmlSerializerOperationBehavior`.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` /@name Wartość dla tej operacji.|  
|`ProtectionLevel`|Ochrona potwierdzenia w zasadach zabezpieczeń dołączonych do `wsdl:binding/wsdl:operation` komunikatów dla tej operacji.|  
|`IsInitiating`|`wsdl:portType` / `wsdl:operation` /@msc:isInitiating Wartość dla tej operacji. Ten atrybut jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozszerzenia WSDL 1.1.|  
|`IsTerminating`|`wsdl:portType` / `wsdl:operation` /@msc:isTerminating Wartość dla tej operacji. Ten atrybut jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rozszerzenia WSDL 1.1.|  
|`Messages`|`wsdl:portType` / `wsdl:operation` / `wsdl:input` i `wsdl:portType` / `wsdl:operation` / `wsdl:output` komunikatów dla tej operacji.|  
|`Faults`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` Definicje dla tej operacji.|  
|`Behaviors`|`DataContractSerializerOperationBehavior` i `XmlSerializerOperationBehavior` postępowania w przypadku powiązanie operacji i komunikaty operacji.|  
  
#### <a name="the-datacontractserializeroperationbehavior"></a>DataContractSerializerOperationBehavior  
 `DataContractSerializerOperationBehavior` Dla operacji jest `IWsdlExportExtension` implementacji, które Eksportuje wiadomości WSDL i powiązania dla tej operacji. Typy schematu XML są eksportowane za pomocą `XsdDataContractExporter`. `DataContractSerializerOperationBehavior` Określa również eksportera użytkowania, stylu i schematu i importera do użycia dla tej operacji.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`DataContractFormatAttribute`|`Style` Mapy właściwości dla tego atrybutu aby `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style wartość dla tej operacji.<br /><br /> `DataContractSerializerOperationBehavior` Obsługuje tylko literału typów schematów w formacie WSDL.|  
  
#### <a name="the-xmlserializeroperationbehavior"></a>XmlSerializerOperationBehavior  
 `XmlSerializerOperationBehavior` Dla operacji jest `IWsdlExportExtension` implementacji, które Eksportuje wiadomości WSDL i powiązania dla tej operacji. Typy schematu XML są eksportowane za pomocą `XmlSchemaExporter`. `XmlSerializerOperationBehavior` Określa również eksportera użytkowania, stylu i schematu i importera do użycia dla tej operacji.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`XmlSerializerFormatAttribute`|`Style` Mapy właściwości dla tego atrybutu aby `wsdl:binding` / `wsdl:operation` / `soap:operation` /@style wartość dla tej operacji.<br /><br /> `Use` Mapy właściwości dla tego atrybutu aby `wsdl:binding` / `wsdl:operation` / `soap:operation`/ */@use wartości dla wszystkich wiadomości w tej operacji.|  
  
### <a name="messages"></a>Komunikaty  
 A `MessageDescription` mapuje wystąpienia `wsdl:message` , do którego odwołuje `wsdl:portType` / `wsdl:operation` / `wsdl:input` lub `wsdl:portType` / `wsdl:operation` / `wsdl:output`komunikatu w operacji. A `MessageDescription` ma treści i nagłówków.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Action`|Akcja SOAP lub WS-Addressing dla wiadomości.<br /><br /> Uwaga tej operacji, które użyć akcji ciągu "*" nie są reprezentowane w języku WSDL.|  
|`Direction`|`MessageDirection.Input` mapuje `wsdl:input`.<br /><br /> `MessageDirection.Output` mapuje `wsdl:output`.|  
|`ProtectionLevel`|Ochrona potwierdzenia w zasadach zabezpieczeń dołączonych do `wsdl:message` definicji dla tej wiadomości.|  
|`Body`|Treść wiadomości.|  
|`Headers`|Nagłówki dla wiadomości.|  
|`ContractDescription.Name`, `OperationContract.Name`|Podczas eksportowania, używany do uzyskania `wsdl:message` /@name wartości.|  
  
#### <a name="message-body"></a>Treść wiadomości  
 A `MessageBodyDescription` mapuje wystąpienia `wsdl:message` / `wsdl:part` definicji dla treści wiadomości. Treść komunikatu może być zawijany lub bez systemu operacyjnego.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`WrapperName`|Jeśli styl nie jest RPC, a następnie `WrapperName` map do nazwy elementu odwołuje się `wsdl:message` / `wsdl:part` z @name ustawioną wartość "Parametry".|  
|`WrapperNamespace`|Jeśli styl nie jest RPC, a następnie `WrapperNamespace` mapuje przestrzeń nazw elementu dla `wsdl:message` / `wsdl:part` z @name ustawioną wartość "Parametry".|  
|`Parts`|Części komunikatów dla tej treści wiadomości.|  
|`ReturnValue`|Element podrzędny elementu otoki: Jeśli element otoki istnieje (styl opakowanym dokumentem lub stylu wywołania RPC), w przeciwnym razie pierwszy `wsdl:message` / `wsdl:part` w komunikacie.|  
  
#### <a name="message-parts"></a>Części wiadomości  
 A `MessagePartDescription` mapuje wystąpienia `wsdl:message` / `wsdl:part` i typ schematu XML lub element, który wskazuje części komunikatu.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|`wsd:message` / `wsdl:part` /@name Wartość części komunikatu i nazwy elementu, który wskazuje części komunikatu.|  
|`Namespace`|Przestrzeń nazw elementu, który wskazuje części komunikatu.|  
|`Index`|Indeks `wsdl:message` / `wsdl:part` dla wiadomości.|  
|`ProtectionLevel`|Ochrona potwierdzenia w zasadach zabezpieczeń dołączonych do `wsdl:message` definicji dla tej części wiadomości. Zasady jest sparametryzowanych wskaż część określonego komunikatu.|  
|`MessageType`|Typ schematu XML elementu, który wskazuje części komunikatu.|  
  
#### <a name="message-headers"></a>Nagłówki komunikatów  
 A `MessageHeaderDescription` wystąpienie jest część komunikatu, który jest również mapowany na `soap:header` powiązania dla części komunikatu.  
  
### <a name="faults"></a>Błędy  
 A `FaultDescription` mapuje wystąpienia `wsdl:portType` / `wsdl:operation` / `wsdl:fault` definicji i jego skojarzony `wsdl:message` definicji. `wsdl:message` Zostanie dodany do tej samej docelowy obszar nazw jako jego skojarzony typ portu WSDL. `wsdl:message` Ma część pojedynczym komunikacie o nazwie "szczegóły", który wskazuje element schematu XML, który odpowiada `DefaultType` wartości właściwości dla `FaultDescription` wystąpienia.  
  
|Właściwości|Mapowanie WSDL|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` /@name Wartość błędu.|  
|`Namespace`|Przestrzeń nazw elementu schematu XML, który wskazuje części komunikatu szczegółów błędu.|  
|`Action`|Akcja SOAP lub WS-Addressing usterki.|  
|`ProtectionLevel`|Ochrona potwierdzenia w zasadach zabezpieczeń dołączonych do `wsdl:message` definicję dla tego błędu.|  
|`DetailType`|Typ schematu XML elementu, który wskazuje części komunikatu szczegółów.|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|Używany do uzyskania `wsdl:message` /@name wartość komunikat o błędzie.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description>
