---
title: Formaty metadanych
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: a3c6b1f551d1bff8c68a91f33e62df289d2078cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="metadata-formats"></a>Formaty metadanych
Windows Communication Foundation (WCF) obsługuje formaty metadanych w poniższej tabeli.  
  
## <a name="metadata-specifications-and-usage"></a>Specyfikacje metadanych i użycia  
  
|Protokół|Specyfikacja i użycia|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> Do opisania usług WCF używa usługi sieci Web Services Description Language (WSDL).|  
|schemat XML|[XML schematu część 2: Wydanie drugie typów danych](http://go.microsoft.com/fwlink/?LinkId=94861) i [część schematu XML 1: struktury wydanie drugie](http://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> Do opisania typów danych używanych w wiadomości WCF używa schematu XML.|  
|Zasady protokołu WS|[Zasady usługi sieci Web 1.2 - Framework (WS-Policy)](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Zasady usługi sieci Web w wersji 1.5 — Framework](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> 1.2 WS-Policy lub specyfikacji 1,5 z potwierdzeniami specyficznego dla domeny WCF używa do opisu usługi wymagań i możliwości.|  
|Załączniki polityki WS|[Zasady usługi sieci Web 1.2 - załącznika (WS-PolicyAttachment)](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> Usługi WCF implementuje usługi WS-Policy załączników do podłączenia zasad wyrażenia w różnych zakresów w języku WSDL.|  
|Wymiany metadanych WS|[Wymiany metadanych usługi sieci Web (WS-MetadataExchange) w wersji 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> Usługi WCF implementuje usługi WS-MetadataExchange, można pobrać schematu XML, WSDL i WS-Policy.|  
|Powiązanie WSDL adresowania WS|[Usługi sieci Web adresowanie 1.0 - Powiązanie WSDL](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> Usługi WCF implementuje usługi WS-Addressing Powiązanie WSDL dołączyć informacje adresowania w języku WSDL.|  
  
## <a name="see-also"></a>Zobacz też  
 [Protokoły usług internetowych obsługiwane przez wiązania współdziałania udostępnione przez system](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [WSDL i zasady](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
