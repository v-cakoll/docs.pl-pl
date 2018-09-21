---
title: Przewodnik dotyczący współpracy protokołów usług sieci Web
ms.date: 03/30/2017
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
ms.openlocfilehash: 37416a80c8b6f2ac086dbface1cda37609698bfc
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46490379"
---
# <a name="web-services-protocols-interoperability-guide"></a>Przewodnik dotyczący współpracy protokołów usług sieci Web
Windows Communication Foundation (WCF) implementuje wiele protokołów usług sieci Web. Wiele z tych protokołów zawierają wiele opcji i punkty rozszerzalności w gestii implementujący. Ten temat zawiera listę protokołów usług sieci Web, który implementuje usługi WCF. Inne tematy w tej sekcji Podaj szczegóły implementacji dla każdego protokołu, obsługiwane.  
  
## <a name="web-services-protocols-implemented-by-wcf"></a>Usługi sieci Web protokołów implementowanych przez architekturę WCF  
 Usługi WCF zapewnia obsługę protokołów infrastruktury (WS) usługi sieci Web za pośrednictwem kanałów i protokoły aplikacji za pomocą funkcji kontraktów usług sieci Web. Współpraca programu protokołów aplikacji odbywa się za pośrednictwem języka opisu schematu XML (XSD) 1.0 i Web Services Description Language (WSDL) 1.1.  
  
 Współdziałanie protokołów infrastruktury jest dostarczany przez WS-* specyfikacji. Kanały programu WCF zapewnia pomoc techniczną dla szereg WS -\* protokołów infrastruktury. Kanały programu WCF są skonfigurowane za pomocą elementów powiązania. Poniższe tabele zawierają pełną listę WS -\* protokołów infrastruktury implementowanych przez różne elementy wiązania WCF.  
  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> obsługuje specyfikacji w poniższej tabeli.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|HTTP 1.1|[RFC 2616](https://go.microsoft.com/fwlink/?LinkId=90372)|  
|SOAP 1.1 powiązania protokołu HTTP|[Simple Object Access Protocol (SOAP) 1.1](https://go.microsoft.com/fwlink/?LinkId=90520), sekcja 7|  
|SOAP 1.2 powiązania protokołu HTTP|[Wersja protokołu SOAP 1.2 część 2: Adjuncts (wydanie drugie)](https://go.microsoft.com/fwlink/?LinkId=95329), sekcja 7|  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> i <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> obsługuje specyfikacji w poniższej tabeli.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|XML|[Extensible Markup Language (XML) 1.0 (wydanie czwarte)](https://go.microsoft.com/fwlink/?LinkId=15139)|  
|PROTOKOŁU SOAP 1.1|[Simple Object Access Protocol (SOAP) 1.1](https://go.microsoft.com/fwlink/?LinkId=96687)|  
|SOAP 1.2 Core|[Wersja protokołu SOAP 1.2 część 1: Messaging Framework (wydanie drugie)](https://go.microsoft.com/fwlink/?LinkId=94664)|  
|WS-Addressing 2004/08|[Usługi sieci Web eliminowanie (WS-Addressing)](https://go.microsoft.com/fwlink/?LinkId=81239)|  
|Eliminowanie Core 1.0 - usług sieci Web W3C|[Eliminowanie Core 1.0 - usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=96688)|  
|Eliminowanie 1.0 - powiązanie protokołu SOAP usług sieci Web W3C|[Eliminowanie 1.0 - powiązanie protokołu SOAP usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=96689)|  
|Usługi sieci Web W3C adresowania 1.0 - WSDL powiązania *|[Eliminowanie 1.0 - Powiązanie WSDL usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=96690)|  
|Usługi sieci Web W3C adresowania 1.0 metadanych|[Eliminowanie 1.0 - metadanych usług sieci Web](http://www.w3.org/TR/ws-addr-metadata/)|  
|Powiązanie SOAP1.1 WSDL|[Web Services Description Language (WSDL) 1.1](https://go.microsoft.com/fwlink/?LinkId=96160)|  
|Powiązanie SOAP1.2 WSDL|[Rozszerzenia 1.1 Powiązanie WSDL dla protokołu SOAP 1.2](https://go.microsoft.com/fwlink/?LinkId=96691)|  
  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> obsługuje specyfikacji w poniższej tabeli.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|XOP|[Plik binarny XML zoptymalizowane pod kątem tworzenia pakietów](https://go.microsoft.com/fwlink/?LinkId=96714)|  
|MTOM + SOAP1.2 powiązania|[Mechanizmu optymalizacji transmisji wiadomości protokołu SOAP](https://go.microsoft.com/fwlink/?LinkId=96713)|  
|MTOM SOAP 1.1 powiązania|[SOAP 1.1 powiązania dla MTOM 1.0](https://go.microsoft.com/fwlink/?LinkId=96712)|  
|MTOM WS-PolicyAssertions|Do opublikowania.|  
  
 <xref:System.ServiceModel.Channels.SecurityBindingElement> obsługuje specyfikacji w poniższej tabeli.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|Programu WSS: Zabezpieczenia komunikatów SOAP 1.0|[Zabezpieczeń usług sieci Web: Zabezpieczenia komunikatów SOAP 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)|  
|Grupie WSS: Token nazwy użytkownika profilu 1.0|[Profil UsernameToken zabezpieczeń 1.0 usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> Wymagaj Password/@Type= PasswordText (ustawienie domyślne)|  
|Grupie WSS: X.509 tokenu profilu 1.0|[W sieci Web usług zabezpieczeń X.509 certyfikatu tokenu profilu](https://go.microsoft.com/fwlink/?LinkId=95335)|  
|Grupie WSS: SAML 1.1 tokenu profilu 1.0|[Zabezpieczeń usług sieci Web: Profil tokenu SAML](https://go.microsoft.com/fwlink/?LinkId=96693)|  
|Programu WSS: Zabezpieczenia komunikatów w ramach SOAP 1.1|[Zabezpieczeń usług sieci Web: Zabezpieczenia komunikatów SOAP 1.1](https://go.microsoft.com/fwlink/?LinkId=91240)|  
|1.1 tokenu profilu programu WSS nazwy użytkownika|[1.1 profilu UsernameToken zabezpieczeń usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> nie należy implementować wyprowadzania klucza opartego na hasłach;<br /><br /> Wymagaj Password/@Type= PasswordText (ustawienie domyślne)|  
|Grupie WSS: X509 Token 1.1 profilu|[W sieci Web usług zabezpieczeń X.509 tokenu profilu certyfikatu 1.1](https://go.microsoft.com/fwlink/?LinkId=95332)|  
|Programu WSS: 1.1 profilu tokenu protokołu Kerberos|[1.1 profilu tokenu protokołu Kerberos zabezpieczeń usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=95333)|  
|Grupie WSS: SAML 1.1 Token 1.1 profilu|[W sieci Web usługi zabezpieczeń tokenu profil SAML 1.1](https://go.microsoft.com/fwlink/?LinkId=96694)|  
|Zabezpieczenia WS konwersacji|[Język bezpiecznej konwersacji usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=95317)|  
|WS-Trust 1.4|[Usługi sieci Web zaufania języka](https://go.microsoft.com/fwlink/?LinkId=169514)|  
|WS-SecurityPolicy 2005/07|[Język bezpiecznej konwersacji usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Zmienione przez errata przesłane do Komitet Techniczny usługi WS-SX OASIS.<br /><br /> [wiadomości ws-sx](https://go.microsoft.com/fwlink/?LinkId=96700)|  
|WS-ReliableMessaging 1.1|[Reliable Messaging Protocol w wersji 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)|  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> obsługuje specyfikacji w poniższej tabeli.  
  
|Specyfikacja/dokumentu|Łącze|  
|-----------------------------|----------|  
|WS-Coordination|[Koordynację usług sieci Web](https://go.microsoft.com/fwlink/?LinkId=95324)|  
|WS-AtomicTransaction|[Atomic Transaction usługi sieci Web](https://go.microsoft.com/fwlink/?LinkId=95323)|  
  
 <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <xref:System.ServiceModel.Description.WsdlExporter>, <xref:System.ServiceModel.Description.WsdlImporter>, I <xref:System.ServiceModel.Description.MetadataResolver> klasy zapewniają obsługę dla następujących specyfikacji metadanych:  
  
-   [XML schematu część 1: Wydanie drugie struktury](https://go.microsoft.com/fwlink/?LinkId=3536)  
  
-   [XML schematu część 2: Typy danych wydanie drugie](https://go.microsoft.com/fwlink/?LinkId=40138)  
  
-   [WSDL 1.1](https://go.microsoft.com/fwlink/?LinkId=96160)  
  
-   [WS-Policy 1.2](https://go.microsoft.com/fwlink/?LinkId=96705)  
  
-   [WS-Policy 1.5](https://go.microsoft.com/fwlink/?LinkId=96706)  
  
-   [WS-PolicyAttachment 1.2](https://go.microsoft.com/fwlink/?LinkId=96707)  
  
-   [WS-MetadataExchange 1.1](https://go.microsoft.com/fwlink/?LinkId=94868)  
  
-   [WS Transfer uzyskać pobierania metadanych](https://go.microsoft.com/fwlink/?LinkId=96708)  
  
 Ponadto następujące profile współdziałanie są zaimplementowane w obszarach WCF:  
  
-   [1.1 profilu podstawowego](https://go.microsoft.com/fwlink/?LinkId=69313)  
  
-   [SOAP proste powiązanie 1.0](https://go.microsoft.com/fwlink/?LinkId=96710)  
  
-   [Podstawowe zabezpieczeń profilu 1.0 pracy narzędzia Draft](https://go.microsoft.com/fwlink/?LinkId=96711)  
  
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
