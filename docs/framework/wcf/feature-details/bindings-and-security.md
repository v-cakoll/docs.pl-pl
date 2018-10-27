---
title: Powiązania i zabezpieczenia
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
ms.openlocfilehash: 9cd180c5e1bd8afff462c380ad3389a78027eb48
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195323"
---
# <a name="bindings-and-security"></a>Powiązania i zabezpieczenia
Powiązania dostarczane przez system, dołączone za pomocą programu Windows Communication Foundation (WCF) oferują szybki sposób program aplikacji WCF. Z jednym wyjątkiem wszystkie powiązania ma domyślny schemat zabezpieczeń włączone. W tym temacie pomaga wybrać odpowiednie powiązanie dla wymagania w zakresie zabezpieczeń.  
  
 Aby uzyskać omówienie zabezpieczeń programu WCF, zobacz [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md). Aby uzyskać więcej informacji na temat programowania za pomocą powiązań WCF zobacz [programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).  
  
 Jeśli została już wybrana powiązanie, możesz znaleźć więcej informacji na temat zachowania czasu wykonywania, które są skojarzone z zabezpieczeniami w [zachowania zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
 Niektóre funkcje zabezpieczeń nie są programowalne, za pomocą powiązania dostarczane przez system. Aby uzyskać większą kontrolę przy użyciu niestandardowego powiązania, zobacz [możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="security-functions-of-bindings"></a>Funkcje zabezpieczeń powiązania  
 Usługi WCF obejmuje wiele powiązań dostarczanych przez system, które spełniają potrzeby większości. Określonego powiązania nie wystarcza, można również utworzyć niestandardowego powiązania. Aby uzyskać listę powiązania dostarczane przez system, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md). Aby uzyskać więcej informacji na temat powiązania niestandardowej zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Każde powiązanie w usłudze WCF ma dwie formy: jako interfejsu API i jako XML element używany w pliku konfiguracji. Na przykład `WSHttpBinding` (API) ma odpowiednik w [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Poniższa sekcja wyświetla obie formy dla każdego powiązania, a także podsumowano funkcje zabezpieczeń.  
  
### <a name="basichttp"></a>BasicHttp  
 W kodzie, należy użyć <xref:System.ServiceModel.BasicHttpBinding> klasy; w konfiguracji, użyj [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 To powiązanie jest przeznaczony do użytku z użyciem wielu istniejących technologii, w tym następujące:  
  
-   Usługi sieci Web platformy ASP.NET (ASMX) w wersji 1.  
  
-   Ulepszenia usługi (WSE) internetowych.  
  
-   Profil podstawowe, zgodnie z definicją w współdziałania usług sieci Web (WS-I) specyfikacji ([https://go.microsoft.com/fwlink/?LinkId=38955](https://go.microsoft.com/fwlink/?LinkId=38955)).  
  
-   Profil zabezpieczeń podstawowe, zgodnie z definicją w WS-I.  
  
 Domyślnie to powiązanie nie jest bezpieczny. Jest on zaprojektowany pod kątem współdziałania z usługami ASMX. Po włączeniu zabezpieczeń powiązania zaprojektowano z myślą bezproblemowe współdziałanie z mechanizmów zabezpieczeń Internet Information Services (IIS), takich jak uwierzytelnianie podstawowe, szyfrowane i zintegrowanych zabezpieczeń Windows. Aby uzyskać więcej informacji, zobacz [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md). To powiązanie obsługuje następujące funkcje:  
  
-   Zabezpieczenia transportu HTTPS.  
  
-   Podstawowe uwierzytelnianie HTTP.  
  
-   WS-Security.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>, i <xref:System.ServiceModel.BasicHttpSecurityMode>.  
  
### <a name="wshttpbinding"></a>WSHttpBinding  
 W kodzie, należy użyć <xref:System.ServiceModel.WSHttpBinding> klasy; w konfiguracji, użyj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Domyślnie to powiązanie implementuje specyfikacji WS-Security i umożliwia współdziałanie z usługami, które implementują WS-* specyfikacji. Obsługuje on następujące funkcje:  
  
-   Zabezpieczenia transportu HTTPS.  
  
-   WS-Security.  
  
-   Protokół HTTPS transportu ochrony za pomocą protokołu SOAP wiadomości poświadczeń zabezpieczeń w celu uwierzytelniania obiektu wywołującego.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>, i <xref:System.ServiceModel.HttpProxyCredentialType>.  
  
### <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 W kodzie, należy użyć <xref:System.ServiceModel.WSDualHttpBinding> klasy; w konfiguracji, użyj [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 To powiązanie jest przeznaczona do umożliwiają aplikacjom usługi duplex. To powiązanie implementuje specyfikacji WS-Security bezpieczeństwie transferu oparta na komunikatach. Zabezpieczenia transportu nie jest dostępna. Domyślnie udostępnia następujące funkcje:  
  
-   Implementuje usługi WS-Reliable Messaging niezawodności.  
  
-   Implementuje usługi WS-Security do uwierzytelniania i bezpieczeństwie transferu.  
  
-   Korzysta z protokołu HTTP do dostarczania wiadomości.  
  
-   Używa kodowania komunikatu tekstu/XML.  
  
 Za pomocą WS-Security (zabezpieczenia warstwie wiadomości), wiązanie umożliwia skonfigurowanie następujących parametrów:  
  
-   Aby określić algorytm kryptograficzny pakiet algorytmów zabezpieczeń.  
  
-   Powiązanie następujące opcje:  
  
    -   Udostępnianie usługi poświadczenia dostępne poza pasmem po stronie klienta.  
  
    -   Dostarczanie poświadczeń usługi negocjowane z usługi w ramach instalacji kanału.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.WSDualHttpSecurity> i <xref:System.ServiceModel.WSDualHttpSecurityMode>.  
  
### <a name="nettcpbinding"></a>NetTcpBinding  
 W kodzie, należy użyć <xref:System.ServiceModel.NetTcpBinding> klasy; w konfiguracji, użyj [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 To powiązanie jest zoptymalizowany pod kątem komunikacji między komputerami. Domyślnie ma następujące cechy:  
  
-   Implementuje zabezpieczeń warstwy transportowej.  
  
-   Wykorzystuje zabezpieczeń Windows do uwierzytelniania i bezpieczeństwie transferu.  
  
-   Używa protokołu TCP dla transportu.  
  
-   Implementuje kodowania komunikatu binarnego.  
  
-   Implementuje usługi WS-Reliable Messaging.  
  
 Dostępne są następujące opcje:  
  
-   Zabezpieczenia warstwy komunikat (przy użyciu usługi WS-Security).  
  
-   Transport security z poświadczeniami komunikatu — poufności i integralności udostępniane przez zabezpieczeń TLS (Transport Layer) za pośrednictwem protokołu TCP i poświadczenia autoryzacji dostarczonych przez WS-Security.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>, i <xref:System.ServiceModel.MessageCredentialType>.  
  
### <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 W kodzie, należy użyć <xref:System.ServiceModel.NetNamedPipeBinding> klasy; w konfiguracji, użyj [ \<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).  
  
 To powiązanie jest zoptymalizowany pod kątem komunikacji między procesami (zwykle w tym samym komputerze). Domyślnie to powiązanie ma następującą charakterystykę:  
  
-   Zastosowań transportu zabezpieczeń do uwierzytelniania i transferu komunikatów.  
  
-   Korzysta z nazwanych potoków do dostarczania wiadomości.  
  
-   Implementuje kodowania komunikatu binarnego.  
  
-   Szyfrowanie i podpisywanie komunikatów.  
  
 Dostępne są następujące opcje:  
  
-   Uwierzytelnianie przy użyciu zabezpieczeń Windows.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode>, i <xref:System.ServiceModel.NamedPipeTransportSecurity>.  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 W kodzie, należy użyć <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> klasy; w konfiguracji, użyj [ \<msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).  
  
 To powiązanie jest zoptymalizowany pod kątem tworzenia WCF klientów i usług, które współdziałać z punktami końcowymi innych niż - WCF Microsoft usługi kolejkowania komunikatów MSMQ.  
  
 Domyślnie to powiązanie korzysta z zabezpieczeń transportu i zawiera następujące właściwości zabezpieczeń:  
  
-   Zabezpieczeń może być wyłączona (Brak).  
  
-   Zabezpieczenia transportu usługi MSMQ (transportu).  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.NetMsmqSecurity> i <xref:System.ServiceModel.NetMsmqSecurityMode>.  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 W kodzie, należy użyć <xref:System.ServiceModel.NetMsmqBinding> klasy; w konfiguracji, użyj [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).  
  
 To powiązanie jest przeznaczona do użytku podczas tworzenia usług WCF, które wymagają usługi MSMQ Obsługa komunikatów w kolejce.  
  
 Domyślnie to powiązanie korzysta z zabezpieczeń transportu i zawiera następujące właściwości zabezpieczeń:  
  
-   Zabezpieczeń może być wyłączona (Brak).  
  
-   Zabezpieczenia transportu usługi MSMQ (transportu).  
  
-   Zabezpieczenia komunikatów opartego na protokole SOAP (komunikat).  
  
-   Jednoczesne transportu i komunikat zabezpieczeń (oba).  
  
-   Obsługiwane typy poświadczeń klienta: Brak, Windows, nazwa użytkownika, certyfikat, IssuedToken.  
  
 <xref:System.ServiceModel.MessageCredentialType.Certificate> Poświadczeń jest obsługiwana tylko wtedy, gdy tryb zabezpieczeń jest ustawiony na <xref:System.ServiceModel.NetMsmqSecurityMode.Both> lub <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MessageSecurityOverMsmq> i <xref:System.ServiceModel.MsmqTransportSecurity>.  
  
### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 W kodzie, należy użyć <xref:System.ServiceModel.WSFederationHttpBinding> klasy; w konfiguracji, użyj [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 Domyślnie WS-Security (Zabezpieczenia wiadomości warstwa) używa tego powiązania.  
  
 Aby uzyskać więcej informacji, zobacz [Federacji](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>, i <xref:System.ServiceModel.WSFederationHttpSecurityMode>.  
  
## <a name="custom-bindings"></a>Powiązania niestandardowe  
 Jeśli żaden z powiązań dostarczanych przez system spełnia wymagania, można utworzyć niestandardowego powiązania za pomocą elementu powiązania zabezpieczeń niestandardowych. Aby uzyskać więcej informacji, zobacz [możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="binding-choices"></a>Opcje  
 Poniższa tabela zawiera podsumowanie funkcji oferowanych w ramach ustawienie Tryb zabezpieczeń, oznacza to, wyświetla listę funkcji dostępnych podczas tryb zabezpieczeń jest ustawiony na `Transport`, `Message`, lub `TransportWithMessageCredential`. Użyj tej tabeli ułatwia znajdowanie funkcji zabezpieczeń wymaganych przez aplikację.  
  
|Ustawienie|Funkcje|  
|-------------|--------------|  
|Transportu|Uwierzytelnianie serwera<br /><br /> Uwierzytelnianie klienta<br /><br /> Bezpieczeństwo typu punkt-punkt<br /><br /> Współdziałanie<br /><br /> Przyspieszanie sprzętowe<br /><br /> Wysoka przepływność<br /><br /> Zabezpieczanie zapory<br /><br /> Aplikacje z dużym opóźnieniem<br /><br /> Ponownie szyfrować w wielu przeskoków|  
|Komunikat|Uwierzytelnianie serwera<br /><br /> Uwierzytelnianie klienta<br /><br /> Zabezpieczenia end-to-end<br /><br /> Współdziałanie<br /><br /> Rozbudowane oświadczeń<br /><br /> Federacja<br /><br /> Uwierzytelnianie wieloskładnikowe<br /><br /> Tokeny niestandardowe<br /><br /> Usługa notariusz/sygnatura czasowa<br /><br /> Aplikacje z dużym opóźnieniem<br /><br /> Stan trwały komunikat podpisów|  
|TransportWithMessageCredential|Uwierzytelnianie serwera<br /><br /> Uwierzytelnianie klienta<br /><br /> Bezpieczeństwo typu punkt-punkt<br /><br /> Współdziałanie<br /><br /> Przyspieszanie sprzętowe<br /><br /> Wysoka przepływność<br /><br /> Oświadczenia wzbogaconego klienta<br /><br /> Federacja<br /><br /> Uwierzytelnianie wieloskładnikowe<br /><br /> Tokeny niestandardowe<br /><br /> Zabezpieczanie zapory<br /><br /> Aplikacje z dużym opóźnieniem<br /><br /> Ponownie szyfrować w wielu przeskoków|  
  
 W poniższej tabeli wymieniono powiązania, które obsługują różne ustawienia trybu. Wybierz powiązanie z tabeli, aby użyć do utworzenia punktu końcowego usługi.  
  
|Powiązanie|Obsługa trybu transportu|Obsługa trybu wiadomości|Obsługa TransportWithMessageCredential|  
|-------------|----------------------------|--------------------------|--------------------------------------------|  
|`BasicHttpBinding`|Tak|Tak|Tak|  
|`WSHttpBinding`|Tak|Tak|Tak|  
|`WSDualHttpBinding`|Nie|Tak|Nie|  
|`NetTcpBinding`|Tak|Tak|Tak|  
|`NetNamedPipeBinding`|Tak|Nie|Nie|  
|`NetMsmqBinding`|Tak|Tak|Nie|  
|`MsmqIntegrationBinding`|Tak|Nie|Nie|  
|`wsFederationHttpBinding`|Nie|Tak|Tak|  
  
## <a name="transport-credentials-in-bindings"></a>Transport poświadczenia w powiązaniach  
 W poniższej tabeli wymieniono dostępne typy poświadczeń klienta przy użyciu `BasicHttpBinding` lub `WSHttpBinding` w trybie zabezpieczeń transportu.  
  
|Typ|Opis|  
|----------|-----------------|  
|Brak|Określa, klient musi przedstawić żadnych poświadczeń. Przekłada się to anonimowym klientem.|  
|Podstawowy|Uwierzytelnianie podstawowe. Aby uzyskać więcej informacji, zobacz RFC 2617 — uwierzytelnianie HTTP: podstawowe i uwierzytelnianie szyfrowane, dostępne pod adresem [ https://go.microsoft.com/fwlink/?LinkId=84023 ](https://go.microsoft.com/fwlink/?LinkId=84023).|  
|Podsumowanie|Uwierzytelnianie szyfrowane. Aby uzyskać więcej informacji, zobacz RFC 2617 — uwierzytelnianie HTTP: podstawowe i uwierzytelnianie szyfrowane, dostępne pod adresem [ https://go.microsoft.com/fwlink/?LinkId=84023 ](https://go.microsoft.com/fwlink/?LinkId=84023).|  
|NTLM|Uwierzytelniania NT LAN Manager (NTLM).|  
|Windows|Uwierzytelnianie Windows.|  
|Certyfikat|Uwierzytelnianie jest wykonywane przy użyciu certyfikatu.|  
|IssuedToken|Umożliwia usłudze wymagają który uwierzytelnienia klienta przy użyciu tokenu wystawionego przez usługę tokenu zabezpieczającego lub przez [!INCLUDE[infocard](../../../../includes/infocard-md.md)]. Aby uzyskać więcej informacji, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="message-client-credentials-in-bindings"></a>Poświadczenia klienta wiadomości w powiązaniach  
 W poniższej tabeli wymieniono dostępne typy poświadczeń klienta, gdy za pomocą powiązania w trybie zabezpieczeń wiadomości.  
  
|Typ|Opis|  
|----------|-----------------|  
|Brak|Umożliwia usłudze na współdziałanie z anonimowych klientów.|  
|Windows|Umożliwia wymianę komunikatów SOAP ma zostać wykonane w kontekście uwierzytelnionych poświadczeń Windows.|  
|UserName|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą poświadczenie nazwy użytkownika. Należy pamiętać, że gdy tryb zabezpieczeń jest ustawiony na `TransportWithMessageCredential`, usługi WCF nie obsługuje wysyłanie hasła szyfrowane lub wyprowadzanie kluczy przy użyciu hasła i rozpoczęcie używania te klucze dla zabezpieczenia trybu komunikatów. W efekcie WCF wymusza, czy transport jest zabezpieczony przy użyciu poświadczeń nazwy użytkownika.|  
|Certyfikat|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu.|  
|IssuedToken|Umożliwia usłudze Użyj usługi tokenu zabezpieczającego, aby określić niestandardowy token.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Zachowania zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
