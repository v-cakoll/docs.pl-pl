---
title: Przewodnik współdziałania protokołów usług sieci Web
ms.date: 03/30/2017
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
ms.openlocfilehash: 1b949880b3ebbaf121b79a958d17cf5708affcf3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636149"
---
# <a name="web-services-protocols-interoperability-guide"></a>Przewodnik współdziałania protokołów usług sieci Web

Windows Communication Foundation (WCF) implementuje wiele protokołów usług sieci Web. Wiele z tych protokołów obejmuje kilka opcji i punkty rozszerzalności pozostawione do uznania. Ten temat zawiera listę protokołów usług sieci Web zaimplementowane w programie WCF. Inne tematy w tej sekcji zawierają szczegóły implementacji dla każdego obsługiwanego protokołu.

## <a name="web-services-protocols-implemented-by-wcf"></a>Protokoły usług sieci Web zaimplementowane przez funkcję WCF

Funkcja WCF zapewnia obsługę protokołów infrastruktury usług sieci Web (WS) za pomocą protokołów kanału i usług sieci Web za pomocą funkcji umowy. Współdziałanie z protokołami aplikacji jest realizowane za poorednictwem kodu XML schematu Description Language 1,0 (XSD) i Web Services Description Language (WSDL) 1,1.

Protokoły infrastruktury współdziałania są udostępniane przez specyfikacje WS-*. Kanały WCF zapewniają obsługę wielu protokołów infrastruktury WS-\*. Kanały WCF są konfigurowane przy użyciu elementów powiązania. Poniższe tabele zawierają pełną listę protokołów infrastruktury WS-\* wdrożonych przez różne elementy powiązania WCF.

<xref:System.ServiceModel.Channels.HttpTransportBindingElement> obsługuje specyfikacje w poniższej tabeli.

|Specyfikacja/dokument|Łącze|
|-----------------------------|----------|
|HTTP 1.1|[RFC 2616](https://www.rfc-editor.org/rfc/rfc2616.txt)|
|Powiązanie HTTP protokołu SOAP 1,1|[Simple Object Access Protocol (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), sekcja 7|
|Powiązanie HTTP protokołu SOAP 1,2|[SOAP w wersji 1,2 część 2: Adjuncts (Second Edition)](https://www.w3.org/TR/soap12-part2/), sekcja 7|

<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> i <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> obsługują specyfikacje w poniższej tabeli.

|Specyfikacja/dokument|Łącze|
|-----------------------------|----------|
|{1&gt;XML&lt;1}|[XML (XML) 1,0 (czwarta wersja)](https://www.w3.org/TR/REC-xml/)|
|PROTOKÓŁ SOAP 1,1|[Simple Object Access Protocol (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)|
|Rdzeń SOAP 1,2|[SOAP w wersji 1,2 część 1: architektura obsługi komunikatów (Second Edition)](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)|
|WS-Addressing 2004/08|[Adresowanie usług sieci Web (WS-Addressing)](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)|
|Usługi sieci Web w formacie W3C o 1,0-Core|[Web Services Addressing 1,0-Core](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509/)|
|Usługi sieci Web w formacie W3C adresowanie 1,0 — powiązanie SOAP|[Web Services Addressing 1,0-powiązania SOAP](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509/)|
|Usługi sieci Web w formacie W3C Addressing 1,0 — Powiązanie WSDL *|[Usługi sieci Web adresowanie 1,0 — Powiązanie WSDL](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)|
|Metadane 1,0 dla usług W3C Web Services|[Web Services Addressing 1,0-Metadata](https://www.w3.org/TR/ws-addr-metadata/)|
|Powiązanie SOAP 1.1 języka WSDL|[Web Services Description Language (WSDL) 1,1](https://www.w3.org/TR/wsdl/)|
|Powiązanie WSDL SOAP 1.2|[Rozszerzenie powiązania WSDL 1,1 dla protokołu SOAP 1,2](https://www.w3.org/Submission/wsdl11soap12/)|

<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> obsługuje specyfikacje w poniższej tabeli.

|Specyfikacja/dokument|Łącze|
|-----------------------------|----------|
|XOP|[Zoptymalizowane w formacie binarnym XML](https://www.w3.org/TR/xop10/)|
|Powiązanie MTOM + SOAP 1.2|[Mechanizm optymalizacji transmisji komunikatów SOAP](https://www.w3.org/TR/soap12-mtom/)|
|Powiązanie SOAP 1,1|[Powiązanie protokołu SOAP 1,1 dla mechanizmu MTOM 1,0](https://www.w3.org/Submission/soap11mtom10/)|
|MTOM WS-PolicyAssertions|[Potwierdzenie zasad serializacji MTOM (WS-MTOMPolicy)](https://www.w3.org/Submission/WS-MTOMPolicy/)|

<xref:System.ServiceModel.Channels.SecurityBindingElement> obsługuje specyfikacje w poniższej tabeli.

|Specyfikacja/dokument|Łącze|
|-----------------------------|----------|
|WSS: zabezpieczenia komunikatów SOAP 1,0|[Zabezpieczenia usług w sieci Web: zabezpieczenia komunikatów SOAP 1,0](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)|
|WSS: Nazwa użytkownika — profil tokenu 1,0|[Zabezpieczenia usług w sieci Web UsernameToken profile 1,0](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> Wymagaj Password/@Type= PasswordText (wartość domyślna)|
|WSS: Profil tokenu X. 509 1,0|[Zabezpieczenia usług w sieci Web profil tokenu certyfikatu X. 509](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)|
|WSS: Profil tokenu SAML 1,1 1,0|[Zabezpieczenia usług w sieci Web: Profil tokenu SAML](https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf)|
|WSS: zabezpieczenia komunikatów SOAP 1,1|[Zabezpieczenia usług w sieci Web: zabezpieczenia komunikatów SOAP 1,1](https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf)|
|Nazwa użytkownika programu WSS username profile 1,1|[Zabezpieczenia usług w sieci Web UsernameToken profile 1,1](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> nie należy implementować wyprowadzania klucza opartego na hasłach;<br /><br /> Wymagaj Password/@Type= PasswordText (wartość domyślna)|
|WSS: Profil tokenu x509 1,1|[Zabezpieczenia usług w sieci Web profil tokenu certyfikatu X. 509 1,1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)|
|WSS: Profil tokenu Kerberos 1,1|[Zabezpieczenia usług w sieci Web profilu tokenu Kerberos 1,1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)|
|WSS: Profil tokenu SAML 1,1 1,1|[Zabezpieczenia usług w sieci Web profilu tokenu SAML 1,1](https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf)|
|Bezpieczna konwersacja WS-Secure|[Język bezpiecznej konwersacji usług sieci Web](https://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)|
|WS-Trust 1,4|[Język zaufania usług sieci Web](https://docs.oasis-open.org/ws-sx/ws-trust/200802)|
|WS-SecurityPolicy 2005/07|[Język bezpiecznej konwersacji usług sieci Web](https://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> Zgodnie z zmianą Errata przesłaną do Komitetu Technicznego usługi WS-SX języka Oasis.<br /><br /> [komunikat WS-SX](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html)|
|WS-ReliableMessaging 1,1|[Reliable Messaging Protocol w wersji 1.1](reliable-messaging-protocol-version-1-1.md)|

<xref:System.ServiceModel.Channels.TransactionFlowBindingElement> obsługuje specyfikacje w poniższej tabeli.

|Specyfikacja/dokument|Łącze|
|-----------------------------|----------|
|WS-Coordination|[Koordynacja usług sieci Web](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))|
|Protokół WS-AtomicTransaction|[Niepodzielna transakcja usług sieci Web](https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)|

Klasy <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <xref:System.ServiceModel.Description.WsdlExporter>, <xref:System.ServiceModel.Description.WsdlImporter>i <xref:System.ServiceModel.Description.MetadataResolver> zapewniają obsługę następujących specyfikacji metadanych:

- [Schemat XML — część 1: struktury Second Edition](https://www.w3.org/TR/xmlschema-1/)

- [Schemat XML — część 2: typy danych Second Edition](https://www.w3.org/TR/xmlschema-2/)

- [WSDL 1.1](https://www.w3.org/TR/wsdl/)

- [WS-Policy 1.2](https://www.w3.org/Submission/2006/SUBM-WS-Policy-20060425/)

- [WS-Policy 1.5](https://www.w3.org/TR/ws-policy/)

- [WS-PolicyAttachment 1.2](https://www.w3.org/Submission/2006/SUBM-WS-PolicyAttachment-20060425/)

- [WS-MetadataExchange 1.1](https://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)

- [Pobieranie metadanych usługi WS-transfer](https://www.w3.org/Submission/2006/SUBM-WS-Transfer-20060315/)

Ponadto w ramach programu WCF Zaimplementowane są następujące profile współdziałania:

- [Profil podstawowy 1,1](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html)

- [Proste powiązanie SOAP 1,0](http://www.ws-i.org/Profiles/SimpleSoapBindingProfile-1.0-2004-08-24.html)

- [Podstawowy profil zabezpieczeń 1,0 roboczy — wersja robocza](http://www.ws-i.org/Profiles/BasicSecurityProfile-1.0-2006-03-29.html)

## <a name="see-also"></a>Zobacz także

- [Protokoły usług internetowych obsługiwane przez wiązania współdziałania udostępnione przez system](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [Protokoły obsługi komunikatów](messaging-protocols.md)
- [Odwołanie do schematu kontraktu danych](data-contract-schema-reference.md)
- [WSDL i zasady](wsdl-and-policy.md)
- [Protokoły zabezpieczeń](security-protocols.md)
- [Reliable Messaging Protocol w wersji 1.0](reliable-messaging-protocol-version-1-0.md)
- [Reliable Messaging Protocol w wersji 1.1](reliable-messaging-protocol-version-1-1.md)
- [Protokoły transakcji](transaction-protocols.md)
- [Protokół wymiany kontekstu](context-exchange-protocol.md)
