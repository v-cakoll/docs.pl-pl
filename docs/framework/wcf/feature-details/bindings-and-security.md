---
title: Wiązania i zabezpieczenia
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
ms.openlocfilehash: 63d3888df364d033b17972a5fd3ba3b851e00c42
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964438"
---
# <a name="bindings-and-security"></a>Wiązania i zabezpieczenia

Powiązania dostarczane przez system Windows Communication Foundation (WCF) umożliwiają szybkie programowanie aplikacji WCF. Po jednym wyjątku wszystkie powiązania mają włączony domyślny schemat zabezpieczeń. Ten temat ułatwia wybór odpowiedniego powiązania dla potrzeb związanych z bezpieczeństwem.

Aby zapoznać się z omówieniem zabezpieczeń WCF, zobacz [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md). Aby uzyskać więcej informacji na temat programowania WCF przy użyciu powiązań, zobacz [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).

Jeśli masz już wybrane powiązanie, możesz dowiedzieć się więcej o zachowaniach w czasie wykonywania, które są skojarzone z zabezpieczeniami w [zachowaniach zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).

Niektóre funkcje zabezpieczeń nie są programowalne przy użyciu powiązań dostarczonych przez system. Aby uzyskać większą kontrolę przy użyciu niestandardowego powiązania, zobacz [funkcje zabezpieczeń z powiązaniami niestandardowymi](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).

## <a name="security-functions-of-bindings"></a>Funkcje zabezpieczeń powiązań

Program WCF zawiera wiele powiązań dostarczonych przez system, które spełniają większość potrzeb. Jeśli określone powiązanie nie jest wystarczające, można również utworzyć niestandardowe powiązanie. Aby uzyskać listę powiązań dostarczanych przez system, zobacz [powiązania dostarczone przez system](../../../../docs/framework/wcf/system-provided-bindings.md). Aby uzyskać więcej informacji na temat powiązań niestandardowych, zobacz [niestandardowe powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).

Każde powiązanie w programie WCF ma dwie formy: jako interfejs API i jako element XML używany w pliku konfiguracji. Na przykład `WSHttpBinding` (API) ma odpowiedni odpowiednik w [\<WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).

Poniższa sekcja zawiera listę obu formularzy dla każdego powiązania i podsumowuje funkcje zabezpieczeń.

### <a name="basichttp"></a>BasicHttp

W kodzie, należy użyć klasy <xref:System.ServiceModel.BasicHttpBinding>; w obszarze Konfiguracja Użyj [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).

To powiązanie jest przeznaczone do użycia z zakresem istniejących technologii, w tym następujących:

- ASP.NET Web Services (ASMX), wersja 1.

- Udoskonalenia usługi sieci Web (WSE).

- Profil podstawowy zgodnie z definicją w specyfikacji współdziałania usług sieci Web (WS-I) (<https://go.microsoft.com/fwlink/?LinkId=38955>).

- Podstawowy profil zabezpieczeń zgodnie z definicją w WS-I.

Domyślnie to powiązanie nie jest bezpieczne. Jest ona przeznaczona do współpracy z usługami ASMX. Po włączeniu zabezpieczeń powiązanie jest przeznaczone do bezproblemowego współdziałania z mechanizmami zabezpieczeń Internet Information Services (IIS), takimi jak uwierzytelnianie podstawowe, skróty i zintegrowane zabezpieczenia systemu Windows. Aby uzyskać więcej informacji, zobacz [Omówienie zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md). To powiązanie obsługuje następujące elementy:

- Zabezpieczenia transportu HTTPS.

- Uwierzytelnianie podstawowe protokołu HTTP.

- WS-Security.

Więcej informacji znajduje się w tematach <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType> i <xref:System.ServiceModel.BasicHttpSecurityMode>.

### <a name="wshttpbinding"></a>WSHttpBinding

W kodzie, należy użyć klasy <xref:System.ServiceModel.WSHttpBinding>; w obszarze Konfiguracja Użyj [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).

Domyślnie to powiązanie implementuje specyfikację WS-Security i zapewnia współdziałanie z usługami, które implementują specyfikacje WS-*. Obsługiwane są następujące elementy:

- Zabezpieczenia transportu HTTPS.

- WS-Security.

- Ochrona transportu HTTPS przy użyciu zabezpieczeń poświadczeń protokołu SOAP do uwierzytelniania obiektu wywołującego.

Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>i <xref:System.ServiceModel.HttpProxyCredentialType>.

### <a name="wsdualhttpbinding"></a>WSDualHttpBinding

W kodzie, należy użyć klasy <xref:System.ServiceModel.WSDualHttpBinding>; w obszarze Konfiguracja Użyj [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).

To powiązanie jest przeznaczone do włączania wielostronnych aplikacji usługi. To powiązanie implementuje specyfikację protokołu WS-Security na potrzeby zabezpieczeń transferów opartych na komunikatach. Zabezpieczenia transportu nie są dostępne. Domyślnie zapewnia następujące funkcje:

- Implementowanie niezawodnej obsługi komunikatów w usłudze WS.

- Implementuje zabezpieczenia WS-Security na potrzeby transferu i uwierzytelniania.

- Używa protokołu HTTP do dostarczania komunikatów.

- Używa kodowania wiadomości tekstowych/XML.

 Za pomocą protokołu WS-Security (zabezpieczenia warstwy komunikatów), powiązanie umożliwia skonfigurowanie następujących parametrów:

- Pakiet algorytmów zabezpieczeń, aby określić algorytm kryptograficzny.

- Opcje powiązań dla następujących:

  - Udostępnianie poświadczeń usługi poza pasmem u klienta.

  - Podawanie poświadczeń usługi negocjowanych z usługi w ramach konfiguracji kanału.

Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.WSDualHttpSecurity> i <xref:System.ServiceModel.WSDualHttpSecurityMode>.

### <a name="nettcpbinding"></a>NetTcpBinding

W kodzie, należy użyć klasy <xref:System.ServiceModel.NetTcpBinding>; w obszarze Konfiguracja Użyj [\<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).

To powiązanie jest zoptymalizowane pod kątem komunikacji między komputerami. Domyślnie ma następującą charakterystykę:

- Implementuje zabezpieczenia warstwy transportowej.

- Wykorzystuje zabezpieczenia systemu Windows do transferowania zabezpieczeń i uwierzytelniania.

- Używa protokołu TCP do transportu.

- Implementuje kodowanie komunikatów binarnych.

- Implementuje obsługę protokołu WS-niezawodny.

Dostępne są następujące opcje:

- Zabezpieczenia warstwy komunikatów (przy użyciu usługi WS-Security).

- Zabezpieczenia transportu z poświadczeniami wiadomości — poufność i integralność zapewnioną przez Transport Layer Security (TLS) przez TCP i poświadczenia na potrzeby autoryzacji udostępniane przez usługę WS-Security.

Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>i <xref:System.ServiceModel.MessageCredentialType>.

### <a name="netnamedpipebinding"></a>NetNamedPipeBinding

W kodzie, należy użyć klasy <xref:System.ServiceModel.NetNamedPipeBinding>; w obszarze Konfiguracja Użyj [\<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).

To powiązanie jest zoptymalizowane pod kątem komunikacji między procesami (zazwyczaj na tym samym komputerze). Domyślnie to powiązanie ma następującą charakterystykę:

- Używa zabezpieczeń transportu do transferowania i uwierzytelniania komunikatów.

- Używa nazwanych potoków do dostarczania komunikatów.

- Implementuje kodowanie komunikatów binarnych.

- Szyfrowanie i podpisywanie komunikatów.

Dostępne są następujące opcje:

- Uwierzytelnianie przy użyciu zabezpieczeń systemu Windows.

Aby uzyskać więcej informacji, zobacz tematy <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode> oraz <xref:System.ServiceModel.NamedPipeTransportSecurity>.

### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding

W kodzie, należy użyć klasy <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>; w obszarze Konfiguracja Użyj [\<msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).

To powiązanie jest zoptymalizowane pod kątem tworzenia klientów i usług WCF, które współdziałają z punktami końcowymi usługi kolejkowania komunikatów (MSMQ) innych niż WCF.

Domyślnie to powiązanie używa zabezpieczeń transportu i zapewnia następujące cechy zabezpieczeń:

- Zabezpieczenia można wyłączyć (brak).

- Zabezpieczenia transportu usługi MSMQ (transport).

Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.NetMsmqSecurity> i <xref:System.ServiceModel.NetMsmqSecurityMode>.

### <a name="netmsmqbinding"></a>NetMsmqBinding

W kodzie, należy użyć klasy <xref:System.ServiceModel.NetMsmqBinding>; w obszarze Konfiguracja Użyj [\<> msmqbinding](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).

To powiązanie jest przeznaczone do użycia podczas tworzenia usług WCF, które wymagają obsługi komunikatów w kolejce usługi MSMQ.

Domyślnie to powiązanie używa zabezpieczeń transportu i zapewnia następujące cechy zabezpieczeń:

- Zabezpieczenia można wyłączyć (brak).

- Zabezpieczenia transportu usługi MSMQ (transport).

- Zabezpieczenia komunikatów opartych na protokole SOAP (Message).

- Jednoczesne transport i zabezpieczenia komunikatów (oba).

- Obsługiwane typy poświadczeń klienta: brak, Windows, nazwa użytkownika, certyfikat, IssuedToken.

Poświadczenie <xref:System.ServiceModel.MessageCredentialType.Certificate> jest obsługiwane tylko wtedy, gdy tryb zabezpieczeń jest ustawiony na <xref:System.ServiceModel.NetMsmqSecurityMode.Both> lub <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.

Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.MessageSecurityOverMsmq> i <xref:System.ServiceModel.MsmqTransportSecurity>.

### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding

W kodzie, należy użyć klasy <xref:System.ServiceModel.WSFederationHttpBinding>; w obszarze Konfiguracja Użyj [\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).

Domyślnie to powiązanie używa protokołu WS-Security (zabezpieczeń warstwy wiadomości).

Aby uzyskać więcej informacji, zobacz [federacyjne](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>i <xref:System.ServiceModel.WSFederationHttpSecurityMode>.

## <a name="custom-bindings"></a>Powiązania niestandardowe

Jeśli żadne z powiązań dostarczonych przez system nie spełnia wymagań, można utworzyć niestandardowe powiązanie z niestandardowym elementem powiązania zabezpieczeń. Aby uzyskać więcej informacji, zobacz [funkcje zabezpieczeń z powiązaniami niestandardowymi](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).

## <a name="binding-choices"></a>Opcje powiązania

Poniższa tabela zawiera podsumowanie funkcji oferowanych w ustawieniach trybu zabezpieczeń, czyli listę funkcji dostępnych w trybie zabezpieczeń ustawionym na `Transport`, `Message`lub `TransportWithMessageCredential`. Ta tabela ułatwia znalezienie funkcji zabezpieczeń wymaganych przez aplikację.

|Ustawienie|Funkcje|
|-------------|--------------|
|Transport|Uwierzytelnianie serwera<br /><br /> Uwierzytelnianie klienta<br /><br /> Zabezpieczenia punkt-punkt<br /><br /> Współdziałanie<br /><br /> Przyspieszenie sprzętowe<br /><br /> Wysoka przepływność<br /><br /> Bezpieczna Zapora<br /><br /> Aplikacje o wysokim opóźnieniu<br /><br /> Ponowne szyfrowanie między wieloma przeskokami|
|Komunikat|Uwierzytelnianie serwera<br /><br /> Uwierzytelnianie klienta<br /><br /> Kompleksowe zabezpieczenia<br /><br /> Współdziałanie<br /><br /> Rozbudowane oświadczenia<br /><br /> Federacja<br /><br /> Uwierzytelnianie wieloskładnikowe<br /><br /> {1&gt;Tokeny niestandardowe&lt;1}<br /><br /> Usługa notariusz/sygnatura czasowa<br /><br /> Aplikacje o wysokim opóźnieniu<br /><br /> Trwałość sygnatur komunikatów|
|TransportWithMessageCredential|Uwierzytelnianie serwera<br /><br /> Uwierzytelnianie klienta<br /><br /> Zabezpieczenia punkt-punkt<br /><br /> Współdziałanie<br /><br /> Przyspieszenie sprzętowe<br /><br /> Wysoka przepływność<br /><br /> Rozbudowane oświadczenia klienta<br /><br /> Federacja<br /><br /> Uwierzytelnianie wieloskładnikowe<br /><br /> {1&gt;Tokeny niestandardowe&lt;1}<br /><br /> Bezpieczna Zapora<br /><br /> Aplikacje o wysokim opóźnieniu<br /><br /> Ponowne szyfrowanie między wieloma przeskokami|

W poniższej tabeli wymieniono powiązania obsługujące różne ustawienia trybu. Wybierz powiązanie z tabeli, która ma zostać użyta do utworzenia punktu końcowego usługi.

|Wiązanie|Obsługa trybu transportowego|Obsługa trybu wiadomości|Obsługa TransportWithMessageCredential|
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

W poniższej tabeli wymieniono typy poświadczeń klienta dostępne w przypadku korzystania z `BasicHttpBinding` lub `WSHttpBinding` w trybie zabezpieczeń transportu.

|Typ|Opis|
|----------|-----------------|
|Brak|Określa, że klient nie musi zaprezentować żadnego poświadczenia. Powoduje to przetłumaczenie na klienta anonimowego.|
|Podstawowy|Uwierzytelnianie podstawowe. Aby uzyskać więcej informacji, zobacz RFC 2617 — uwierzytelnianie HTTP: uwierzytelnianie podstawowe i szyfrowane, dostępne w <https://go.microsoft.com/fwlink/?LinkId=84023>.|
|Szyfrowane|Uwierzytelnianie szyfrowane. Aby uzyskać więcej informacji, zobacz RFC 2617 — uwierzytelnianie HTTP: uwierzytelnianie podstawowe i szyfrowane, dostępne w <https://go.microsoft.com/fwlink/?LinkId=84023>.|
|NTLM|Uwierzytelnianie przy użyciu programu NT LAN Manager (NTLM).|
|Windows|Uwierzytelnianie systemu Windows.|
|Certyfikat|Uwierzytelnianie wykonywane przy użyciu certyfikatu.|
|IssuedToken|Zezwala usłudze na wymaganie uwierzytelniania klienta przy użyciu tokenu wystawionego przez usługę tokenu zabezpieczającego lub przez program CardSpace. Aby uzyskać więcej informacji, zobacz [federacyjne i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|

### <a name="message-client-credentials-in-bindings"></a>Poświadczenia klienta wiadomości w powiązaniach

W poniższej tabeli wymieniono typy poświadczeń klienta dostępne w przypadku korzystania z powiązania w trybie zabezpieczenia komunikatów.

|Typ|Opis|
|----------|-----------------|
|Brak|Umożliwia usłudze współpracującie z klientami anonimowymi.|
|Windows|Umożliwia wymianę komunikatów protokołu SOAP w ramach uwierzytelnionego kontekstu poświadczeń systemu Windows.|
|UserName|Zezwala usłudze na wymaganie uwierzytelniania klienta przy użyciu poświadczeń nazwy użytkownika. Należy pamiętać, że gdy tryb zabezpieczeń ma wartość `TransportWithMessageCredential`, usługa WCF nie obsługuje wysyłania skrótu hasła ani wyprowadzania kluczy przy użyciu hasła i używania tych kluczy do zabezpieczenia w trybie komunikatów. W związku z tym WCF wymusza, aby transport był zabezpieczony przy użyciu poświadczeń nazwy użytkownika.|
|Certyfikat|Zezwala usłudze na wymaganie uwierzytelniania klienta przy użyciu certyfikatu.|
|IssuedToken|Zezwala usłudze na używanie usługi tokenu zabezpieczającego do dostarczania niestandardowego tokenu.|

## <a name="see-also"></a>Zobacz także

- [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Zachowania zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
