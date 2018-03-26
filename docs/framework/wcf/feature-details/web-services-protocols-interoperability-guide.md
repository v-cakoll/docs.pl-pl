---
title: Przewodnik dotyczący współpracy protokołów usług sieci Web
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b962452b6127d259733418969f1fb7b5036b1e5
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="web-services-protocols-interoperability-guide"></a>Przewodnik dotyczący współpracy protokołów usług sieci Web
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementuje wiele protokołów usług sieci Web. Wiele z tych protokołów zawiera szereg opcji i punkty rozszerzalności w gestii implementujący. W tym temacie przedstawiono protokoły usług sieci Web wykaz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementuje. Inne tematy w tej sekcji Podaj szczegóły implementacji dla każdego protokołu obsługiwane.  
  
## <a name="web-services-protocols-implemented-by-wcf"></a>Usługi sieci Web protokołów implementowanych przez usługi WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia obsługę protokołów infrastruktury (WS) usługi sieci Web za pośrednictwem kanałów i protokołów aplikacji usługi sieci Web za pomocą funkcji umów. Współdziałanie protokołu aplikacji odbywa się za pośrednictwem języka opisu schematu XML 1.0 (XSD) i sieci Web Services Description Language (WSDL) 1.1.  
  
 Infrastruktury współdziałania protokoły są udostępniane przez usługi WS-* specyfikacji. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Kanały zapewniają obsługę wielu WS -\* protokołów infrastruktury. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanały są skonfigurowane za pomocą elementów powiązania. Poniższe tabele zawierają pełną listę WS -\* infrastruktury protokołów implementowanych przez różnych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] elementów wiązania.  
  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> obsługuje specyfikacje w poniższej tabeli.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|HTTP 1.1|[RFC 2616](http://go.microsoft.com/fwlink/?LinkId=90372)|  
|SOAP 1.1 powiązanie HTTP|[Simple Object Access Protocol (SOAP) 1.1](http://go.microsoft.com/fwlink/?LinkId=90520), sekcji 7|  
|SOAP 1.2 powiązanie HTTP|[Wersja protokołu SOAP 1.2 część 2: Adjuncts (wydanie drugie)](http://go.microsoft.com/fwlink/?LinkId=95329), sekcji 7|  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> i <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> obsługuje specyfikacje w poniższej tabeli.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|XML|[Extensible Markup Language (XML) 1.0 (czwarty Edition)](http://go.microsoft.com/fwlink/?LinkId=15139)|  
|SOAP 1.1|[Simple Object Access Protocol (SOAP) 1.1](http://go.microsoft.com/fwlink/?LinkId=96687)|  
|SOAP 1.2 Core|[Wersja protokołu SOAP 1.2 część 1: Wiadomości Framework (wydanie drugie)](http://go.microsoft.com/fwlink/?LinkId=94664)|  
|Protokół WS-Addressing 2004/08|[Usługi sieci Web adresowanie (WS-Addressing)](http://go.microsoft.com/fwlink/?LinkId=81239)|  
|Usługi sieci Web W3C adresowania 1.0 — podstawowe|[Usługi sieci Web adresowanie 1.0 — podstawowe](http://go.microsoft.com/fwlink/?LinkId=96688)|  
|Adresowania 1.0 — wiązanie protokołu SOAP usług sieci Web W3C|[Usługi sieci Web adresowanie 1.0 - powiązania SOAP](http://go.microsoft.com/fwlink/?LinkId=96689)|  
|Usługi sieci Web W3C adresowania 1.0 - WSDL powiązanie *|[Usługi sieci Web adresowanie 1.0 - Powiązanie WSDL](http://go.microsoft.com/fwlink/?LinkId=96690)|  
|W3C usług sieci Web adresowanie metadanych 1.0|[Usługi sieci Web adresowanie 1.0 - metadanych](http://www.w3.org/TR/ws-addr-metadata/)|  
|Powiązanie WSDL SOAP1.1|[Web Services Description Language (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)|  
|Powiązanie WSDL SOAP1.2|[Rozszerzenie 1.1 powiązania WSDL SOAP 1.2](http://go.microsoft.com/fwlink/?LinkId=96691)|  
  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> obsługuje specyfikacje w poniższej tabeli.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|XOP|[Dane binarne XML zoptymalizowanych pod kątem tworzenia pakietów](http://go.microsoft.com/fwlink/?LinkId=96714)|  
|MTOM + SOAP1.2 powiązania|[Mechanizmu optymalizacji transmisji wiadomości SOAP](http://go.microsoft.com/fwlink/?LinkId=96713)|  
|MTOM SOAP 1.1 powiązania|[SOAP 1.1 powiązania dla MTOM 1.0](http://go.microsoft.com/fwlink/?LinkId=96712)|  
|MTOM WS-PolicyAssertions|Do opublikowania.|  
  
 <xref:System.ServiceModel.Channels.SecurityBindingElement> obsługuje specyfikacje w poniższej tabeli.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|WSS: Zabezpieczenia komunikatów SOAP 1.0|[Zabezpieczenia usługi sieci Web: Zabezpieczenia komunikatów SOAP 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)|  
|Programu WSS: Profil Token nazwy użytkownika 1.0|[Profil zabezpieczeń UsernameToken 1.0 usług sieci Web](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> Wymagaj Password/@Type= PasswordText (ustawienie domyślne)|  
|Programu WSS: Profil tokenu X.509 1.0|[Web Services zabezpieczeń X.509 certyfikatu tokenu profilu](http://go.microsoft.com/fwlink/?LinkId=95335)|  
|Programu WSS: SAML 1.1 Token profilu 1.0|[Zabezpieczenia usługi sieci Web: Profil tokenu SAML](http://go.microsoft.com/fwlink/?LinkId=96693)|  
|Programu WSS: Zabezpieczenia komunikatów SOAP 1.1|[Zabezpieczenia usługi sieci Web: Zabezpieczenia komunikatów SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=91240)|  
|1.1 tokenu profilu programu WSS nazwy użytkownika|[1.1 profilu UsernameToken zabezpieczeń usług sieci Web](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> nie należy implementować wyprowadzania klucza opartego na hasłach;<br /><br /> Wymagaj Password/@Type= PasswordText (ustawienie domyślne)|  
|WSS: X509 Token 1.1 profilu|[Web Services zabezpieczeń X.509 tokenu profil certyfikatu 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)|  
|WSS: 1.1 profilu Token protokołu Kerberos|[1.1 profilu Kerberos tokenu zabezpieczeń usług sieci Web](http://go.microsoft.com/fwlink/?LinkId=95333)|  
|Programu WSS: SAML 1.1 Token 1.1 profilu|[Web Services SAML tokenu profil zabezpieczeń 1.1](http://go.microsoft.com/fwlink/?LinkId=96694)|  
|Zabezpieczenia WS konwersacji|[Język bezpiecznej konwersacji usług sieci Web](http://go.microsoft.com/fwlink/?LinkId=95317)|  
|WS-Trust 1.4|[Język zaufania usług sieci Web](http://go.microsoft.com/fwlink/?LinkId=169514)|  
|WS-SecurityPolicy 2005/07|[Język bezpiecznej konwersacji usług sieci Web](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Zmienionej erracie przesłane do Komitetu Technicznego WS-SX OASIS.<br /><br /> [wiadomości ws-sx](http://go.microsoft.com/fwlink/?LinkId=96700)|  
|WS-ReliableMessaging 1.1|[Reliable Messaging Protocol w wersji 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)|  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> obsługuje specyfikacje w poniższej tabeli.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|WS-Coordination|[Koordynację usług sieci Web](http://go.microsoft.com/fwlink/?LinkId=95324)|  
|WS-AtomicTransaction|[Niepodzielne transakcji usług sieci Web](http://go.microsoft.com/fwlink/?LinkId=95323)|  
  
 <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <!--zz <xref:System.ServiceModel.Description.WSDLExporter>, <xref:System.ServiceModel.Description.WSDLImporter>, --> `System.ServiceModel.Description.MetadataImporter`, `System.ServiceModel.Description.WSDLImporter`, I <xref:System.ServiceModel.Description.MetadataResolver> klasy zapewniają obsługę następujących specyfikacji metadanych:  
  
-   [XML schematu część 1: Wydanie drugie struktury](http://go.microsoft.com/fwlink/?LinkId=3536)  
  
-   [XML schematu część 2: Typy danych wydanie drugie](http://go.microsoft.com/fwlink/?LinkId=40138)  
  
-   [WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)  
  
-   [WS-Policy 1.2](http://go.microsoft.com/fwlink/?LinkId=96705)  
  
-   [WS-Policy 1.5](http://go.microsoft.com/fwlink/?LinkId=96706)  
  
-   [WS-PolicyAttachment 1.2](http://go.microsoft.com/fwlink/?LinkId=96707)  
  
-   [WS-MetadataExchange 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)  
  
-   [Pobierz usługę WS-Transfer do pobierania metadanych](http://go.microsoft.com/fwlink/?LinkId=96708)  
  
 Ponadto następujące profile współdziałanie są implementowane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   [Basic Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=69313)  
  
-   [Simple SOAP powiązanie 1.0](http://go.microsoft.com/fwlink/?LinkId=96710)  
  
-   [Podstawowe zabezpieczeń profilu 1.0 pracy projektu](http://go.microsoft.com/fwlink/?LinkId=96711)  
  
## <a name="see-also"></a>Zobacz też  
 [Protokoły usług internetowych obsługiwane przez wiązania współdziałania udostępnione przez system](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [Protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)  
 [Odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 [WSDL i zasady](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)  
 [Protokoły zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md)  
 [Reliable Messaging Protocol w wersji 1.0](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-0.md)  
 [Reliable Messaging Protocol w wersji 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)  
 [Protokoły transakcji](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)  
 [Protokół wymiany kontekstu](../../../../docs/framework/wcf/feature-details/context-exchange-protocol.md)
