---
title: Powiązania i zabezpieczenia
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
caps.latest.revision: 42
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 5eb1019694f6228edbe3656849b85dfa7611ef18
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="bindings-and-security"></a>Powiązania i zabezpieczenia
Powiązania dostarczane przez system dołączonego [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] oferują możliwość szybkiego program [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji. Z jednym wyjątkiem wszystkie powiązania ma domyślny schemat zabezpieczeń włączone. Ten temat ułatwia wybierz prawa powiązanie dla wymagania w zakresie zabezpieczeń.  
  
 Omówienie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń, zobacz [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Programowanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przy użyciu powiązań, zobacz [programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).  
  
 Jeśli zostały już wybrane powiązanie, można znaleźć więcej informacji na temat zachowania czasu wykonywania, które są skojarzone z zabezpieczeniami w [zachowania zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
 Niektóre funkcje zabezpieczeń nie są programowalny za pomocą powiązania dostarczane przez system. Aby uzyskać większą kontrolę przy użyciu niestandardowego powiązania, zobacz [możliwości zabezpieczeń wiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="security-functions-of-bindings"></a>Funkcje związane z bezpieczeństwem powiązań  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawiera liczbę powiązania dostarczane przez system, które spełniają potrzeby większości. Jeśli określonego powiązania nie wystarcza, można również utworzyć niestandardowego powiązania. Aby uzyskać listę powiązania dostarczane przez system, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] powiązania niestandardowe, zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Każde powiązanie w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ma dwie formy: interfejs API, a element XML używane w pliku konfiguracji. Na przykład `WSHttpBinding` (API) ma odpowiednik w [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Poniższa sekcja zawiera listę zarówno formularzy dla każdego powiązania i zawiera podsumowanie funkcji zabezpieczeń.  
  
### <a name="basichttp"></a>BasicHttp  
 W kodzie, użyj <xref:System.ServiceModel.BasicHttpBinding> klasy; w konfiguracji, użyj [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 To powiązanie jest przeznaczony do użytku z zakresu istniejących technologii, takie jak następujące:  
  
-   Usługi sieci Web platformy ASP.NET (ASMX) w wersji 1.  
  
-   Aplikacje usługi ulepszenia (WSE) sieci Web.  
  
-   Basic Profile zgodnie z definicją w współdziałanie usług sieci Web (WS-I) specyfikacja ([http://go.microsoft.com/fwlink/?LinkId=38955](http://go.microsoft.com/fwlink/?LinkId=38955)).  
  
-   Profil zabezpieczeń podstawowe, zgodnie z definicją w WS-I.  
  
 Domyślnie to powiązanie nie jest bezpieczne. Zaprojektowano go na potrzeby współdziałania z usługami ASMX. Po włączeniu zabezpieczeń powiązania jest przeznaczona dla bezproblemowe współdziałanie z mechanizmów zabezpieczeń Internet Information Services (IIS), takich jak uwierzytelnianie podstawowe, szyfrowane i zintegrowane zabezpieczenia systemu Windows. Aby uzyskać więcej informacji, zobacz [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md). To powiązanie obsługuje następujące funkcje:  
  
-   Zabezpieczenia transportu dla protokołu HTTPS.  
  
-   Podstawowe uwierzytelnianie HTTP.  
  
-   WS-Security.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>, i <xref:System.ServiceModel.BasicHttpSecurityMode>.  
  
### <a name="wshttpbinding"></a>WSHttpBinding  
 W kodzie, użyj <xref:System.ServiceModel.WSHttpBinding> klasy; w konfiguracji, użyj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Domyślnie to powiązanie implementuje specyfikacji WS-Security i umożliwia współdziałanie z usługami, które implementują WS-* specyfikacji. Obsługuje on następujące funkcje:  
  
-   Zabezpieczenia transportu dla protokołu HTTPS.  
  
-   WS-Security.  
  
-   HTTPS transportu ochrony z protokołu SOAP wiadomości poświadczeń zabezpieczeń w celu uwierzytelniania wywołującego.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>, i <xref:System.ServiceModel.HttpProxyCredentialType>.  
  
### <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 W kodzie, użyj <xref:System.ServiceModel.WSDualHttpBinding> klasy; w konfiguracji, użyj [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 To powiązanie zaprojektowana w celu umożliwienia aplikacji usługi duplex. To powiązanie implementuje ze specyfikacją WS-Security zabezpieczeń transferu komunikatów. Zabezpieczenia transportu nie jest dostępna. Domyślnie zapewnia następujące funkcje:  
  
-   Implementuje usługi WS-Reliable Messaging niezawodności.  
  
-   Implementuje WS-Security transfer zabezpieczeń i uwierzytelniania.  
  
-   Używa protokołu HTTP w celu dostarczania komunikatów.  
  
-   Używa tekstu/XML Kodowanie komunikatu.  
  
 Przy użyciu WS-Security (Zabezpieczenia wiadomości warstwy), wiązanie można skonfigurować następujące parametry:  
  
-   Aby określić algorytm kryptograficzny pakietu algorytmów zabezpieczeń.  
  
-   Powiązanie następujące opcje:  
  
    -   Udostępnia usługi poświadczenia dostępne poza pasmem po stronie klienta.  
  
    -   Podawanie poświadczeń usługi negocjowane z usługi w ramach instalacji kanału.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.WSDualHttpSecurity> i <xref:System.ServiceModel.WSDualHttpSecurityMode>.  
  
### <a name="nettcpbinding"></a>NetTcpBinding  
 W kodzie, użyj <xref:System.ServiceModel.NetTcpBinding> klasy; w konfiguracji, użyj [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 To powiązanie jest zoptymalizowana pod kątem komunikacji między komputerami. Domyślnie ma następującą charakterystykę:  
  
-   Implementuje zabezpieczeń warstwy transportu.  
  
-   Wykorzystuje zabezpieczenia systemu Windows do uwierzytelniania i zabezpieczeń transferu.  
  
-   Używa protokołu TCP dla transportu.  
  
-   Implementuje Kodowanie komunikatu binarnego.  
  
-   Implementuje usługi WS-Reliable Messaging.  
  
 Dostępne są następujące opcje:  
  
-   Zabezpieczenia warstwy komunikatu (przy użyciu WS-Security).  
  
-   Transport zabezpieczeń z poświadczeniami komunikatu — poufności i integralności udostępniane przez zabezpieczeń TLS (Transport Layer) za pośrednictwem TCP i poświadczenia do autoryzacji dostarczane przez usługę WS-Security.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>, i <xref:System.ServiceModel.MessageCredentialType>.  
  
### <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 W kodzie, użyj <xref:System.ServiceModel.NetNamedPipeBinding> klasy; w konfiguracji, użyj [ \<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).  
  
 To powiązanie jest zoptymalizowana pod kątem komunikacji między procesami (zwykle na tym samym komputerze). Domyślnie to powiązanie ma następującą charakterystykę:  
  
-   Używa transportu zabezpieczeń do uwierzytelniania i transferu komunikatów.  
  
-   Używa nazwanych potoków do dostarczania komunikatów.  
  
-   Implementuje Kodowanie komunikatu binarnego.  
  
-   Szyfrowania i podpisywania komunikatu.  
  
 Dostępne są następujące opcje:  
  
-   Uwierzytelnianie przy użyciu zabezpieczeń systemu Windows.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode>, i <xref:System.ServiceModel.NamedPipeTransportSecurity>.  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 W kodzie, użyj <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> klasy; w konfiguracji, użyj [ \<msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).  
  
 To powiązanie jest zoptymalizowany do tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów i usług, które współdziałają z inną niż[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktów końcowych usługi kolejkowania wiadomości firmy Microsoft (MSMQ).  
  
 Domyślnie to powiązanie korzysta z zabezpieczeń transportu i zawiera następujące właściwości zabezpieczeń:  
  
-   Zabezpieczeń może być wyłączone (Brak).  
  
-   Zabezpieczenia transportu usługi MSMQ (transportu).  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.NetMsmqSecurity> i <xref:System.ServiceModel.NetMsmqSecurityMode>.  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 W kodzie, użyj <xref:System.ServiceModel.NetMsmqBinding> klasy; w konfiguracji, użyj [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).  
  
 To powiązanie jest przeznaczona do użycia podczas tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługi wiadomości w kolejce usług, które wymagają usługi MSMQ.  
  
 Domyślnie to powiązanie korzysta z zabezpieczeń transportu i zawiera następujące właściwości zabezpieczeń:  
  
-   Zabezpieczeń może być wyłączone (Brak).  
  
-   Zabezpieczenia transportu usługi MSMQ (transportu).  
  
-   Zabezpieczenia komunikatów opartego na protokole SOAP (komunikat).  
  
-   Jednoczesne transportu i komunikat zabezpieczeń (oba).  
  
-   Obsługiwane typy poświadczeń klienta: Brak, Windows, nazwa użytkownika, certyfikat, IssuedToken.  
  
 <xref:System.ServiceModel.MessageCredentialType.Certificate> Poświadczeń jest obsługiwana tylko wtedy, gdy tryb zabezpieczeń jest ustawiona jako <xref:System.ServiceModel.NetMsmqSecurityMode.Both> lub <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MessageSecurityOverMsmq> i <xref:System.ServiceModel.MsmqTransportSecurity>.  
  
### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 W kodzie, użyj <xref:System.ServiceModel.WSFederationHttpBinding> klasy; w konfiguracji, użyj [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 Domyślnie używa tego powiązania WS-Security (Zabezpieczenia warstwy komunikat).  
  
 Aby uzyskać więcej informacji, zobacz [federacyjnego](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>, i <xref:System.ServiceModel.WSFederationHttpSecurityMode>.  
  
## <a name="custom-bindings"></a>Powiązania niestandardowe  
 Jeśli żaden z powiązania dostarczane przez system spełnia wymagania, można utworzyć niestandardowego powiązania z elementu powiązania zabezpieczeń niestandardowych. Aby uzyskać więcej informacji, zobacz [możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="binding-choices"></a>Opcje  
 W poniższej tabeli przedstawiono funkcje oferowane w ustawieniu trybu zabezpieczeń, oznacza to, wyświetlane są funkcje dostępne podczas tryb zabezpieczeń jest ustawiony na `Transport`, `Message`, lub `TransportWithMessageCredential`. Użyj tej tabeli w celu znalezienia funkcji zabezpieczeń wymaganych przez aplikację.  
  
|Ustawienie|Funkcje|  
|-------------|--------------|  
|Transportu|Uwierzytelnianie serwera<br /><br /> Uwierzytelnianie klienta<br /><br /> Point-to-Point zabezpieczeń<br /><br /> Współdziałanie<br /><br /> Przyspieszanie sprzętowe<br /><br /> Wysoka przepustowość<br /><br /> Zabezpieczenia zapory<br /><br /> Aplikacje długim czasie oczekiwania<br /><br /> Ponownie szyfrować między wieloma przeskokami|  
|Komunikat|Uwierzytelnianie serwera<br /><br /> Uwierzytelnianie klienta<br /><br /> Zabezpieczeń na trasie<br /><br /> Współdziałanie<br /><br /> Zaawansowana oświadczeń<br /><br /> Federacja<br /><br /> Uwierzytelnianie wieloskładnikowe<br /><br /> Tokeny niestandardowe<br /><br /> Usługa notariusz/znacznik czasu<br /><br /> Aplikacje długim czasie oczekiwania<br /><br /> Trwałość sygnatury komunikatów|  
|TransportWithMessageCredential|Uwierzytelnianie serwera<br /><br /> Uwierzytelnianie klienta<br /><br /> Point-to-Point zabezpieczeń<br /><br /> Współdziałanie<br /><br /> Przyspieszanie sprzętowe<br /><br /> Wysoka przepustowość<br /><br /> Oświadczenia wzbogaconego klienta<br /><br /> Federacja<br /><br /> Uwierzytelnianie wieloskładnikowe<br /><br /> Tokeny niestandardowe<br /><br /> Zabezpieczenia zapory<br /><br /> Aplikacje długim czasie oczekiwania<br /><br /> Ponownie szyfrować między wieloma przeskokami|  
  
 W poniższej tabeli wymieniono powiązania, które obsługują różne ustawienia trybu. Wybierz powiązania z tabeli używanej do utworzenia punktu końcowego usługi.  
  
|Powiązanie|Pomoc techniczna trybu transportu|Pomoc techniczna trybu wiadomości|Obsługa TransportWithMessageCredential|  
|-------------|----------------------------|--------------------------|--------------------------------------------|  
|`BasicHttpBinding`|Tak|Tak|Tak|  
|`WSHttpBinding`|Tak|Tak|Tak|  
|`WSDualHttpBinding`|Nie|Tak|Nie|  
|`NetTcpBinding`|Tak|Tak|Tak|  
|`NetNamedPipeBinding`|Tak|Nie|Nie|  
|`NetMsmqBinding`|Tak|Tak|Nie|  
|`MsmqIntegrationBinding`|Tak|Nie|Nie|  
|`wsFederationHttpBinding`|Nie|Tak|Tak|  
  
## <a name="transport-credentials-in-bindings"></a>Poświadczenia transportu w powiązaniach  
 W poniższej tabeli wymieniono dostępne typy poświadczeń klienta przy użyciu `BasicHttpBinding` lub `WSHttpBinding` w tryb zabezpieczeń transport.  
  
|Typ|Opis|  
|----------|-----------------|  
|Brak|Określa, że klient musi przedstawiać żadnego poświadczenia. Umożliwia to anonimowym klientem.|  
|Podstawowy|Uwierzytelnianie podstawowe. Aby uzyskać więcej informacji, zobacz dokument RFC 2617 — uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego, dostępne pod adresem [ http://go.microsoft.com/fwlink/?LinkId=84023 ](http://go.microsoft.com/fwlink/?LinkId=84023).|  
|Skrót|Uwierzytelnianie szyfrowane. Aby uzyskać więcej informacji, zobacz dokument RFC 2617 — uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego, dostępne pod adresem [ http://go.microsoft.com/fwlink/?LinkId=84023 ](http://go.microsoft.com/fwlink/?LinkId=84023).|  
|NTLM|Uwierzytelnianie NT LAN Manager (NTLM).|  
|Windows|Uwierzytelnianie systemu Windows.|  
|certyfikat|Uwierzytelnianie jest wykonywane przy użyciu certyfikatu.|  
|IssuedToken|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą tokenu wystawiony przez usługę tokenu zabezpieczającego przez [!INCLUDE[infocard](../../../../includes/infocard-md.md)]. Aby uzyskać więcej informacji, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="message-client-credentials-in-bindings"></a>Poświadczenia klienta komunikatu w powiązaniach  
 W poniższej tabeli wymieniono dostępne typy poświadczeń klienta, gdy użycie powiązania w trybie zabezpieczeń wiadomości.  
  
|Typ|Opis|  
|----------|-----------------|  
|Brak|Umożliwia usłudze na współdziałanie z anonimowego klientów.|  
|Windows|Umożliwia wymianę wiadomości protokołu SOAP ma zostać wykonane w kontekście uwierzytelnionych poświadczeń systemu Windows.|  
|UserName|Umożliwia usłudze wymagają który uwierzytelnienia klienta przy użyciu poświadczeń użytkownika. Należy pamiętać, że jeśli ustawiono tryb zabezpieczeń `TransportWithMessageCredential`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie obsługuje wysyłanie hasła klawiszy skrótu lub wyprowadzanie przy użyciu hasła i te klucze dla zabezpieczenia trybu wiadomości. W efekcie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymusza, czy transport jest zabezpieczony, korzystając z poświadczeń nazwy użytkownika.|  
|certyfikat|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu.|  
|IssuedToken|Umożliwia usłudze Użyj usługi tokenu zabezpieczającego, aby określić niestandardowy token.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Zachowania zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
