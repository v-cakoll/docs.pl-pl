---
title: Konfigurowanie powiązań dostarczanych przez system
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
ms.openlocfilehash: c2c1f468fba404768fe01e84260125843964fea0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949626"
---
# <a name="configuring-system-provided-bindings"></a>Konfigurowanie powiązań dostarczanych przez system
Powiązania określają mechanizm komunikacji, który ma być używany podczas komunikacji z punktem końcowym i wskazujący, jak nawiązać połączenie z punktem końcowym. Powiązania składają się z elementów, które definiują sposób warstwowego kanałów Windows Communication Foundation (WCF) w celu zapewnienia wymaganych funkcji komunikacyjnych. Powiązanie zawiera trzy typy elementów:  
  
- Elementy powiązania kanału protokołu, które określają zabezpieczenia, niezawodność, ustawienia przepływu kontekstu lub protokoły zdefiniowane przez użytkownika do użycia z komunikatami wysyłanymi do punktu końcowego.  
  
- Elementy powiązania kanału transportowego, które określają podstawowy protokół transportowy do użycia podczas wysyłania komunikatów do punktu końcowego, na przykład TCP lub HTTP.  
  
- Elementy powiązania kodowania komunikatów, które określają kodowanie sieci, które mają być używane w przypadku komunikatów wysyłanych do punktu końcowego, na przykład Metoda Text/XML, binary lub mechanizm optymalizacji transmisji wiadomości (MTOM).  
  
 W tym temacie przedstawiono wszystkie powiązania Windows Communication Foundation udostępnione przez system. Jeśli żaden z tych elementów nie spełnia dokładnie wymagań aplikacji, można utworzyć powiązanie przy użyciu <xref:System.ServiceModel.Channels.CustomBinding> klasy. Aby uzyskać więcej informacji na temat tworzenia powiązań niestandardowych, zobacz [powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
> [!IMPORTANT]
> Wybierz powiązanie z włączonymi zabezpieczeniami. Domyślnie wszystkie powiązania, z wyjątkiem <xref:System.ServiceModel.BasicHttpBinding> powiązania, mają włączone zabezpieczenia. Jeśli nie wybierzesz bezpiecznego powiązania lub w przypadku wyłączenia zabezpieczeń, upewnij się, że wymiana sieci jest chroniona w inny sposób, na przykład w zabezpieczonym centrum danych lub w sieci izolowanej.  
  
> [!IMPORTANT]
> Nie należy używać kontraktów dupleksowych z powiązaniami, które nie obsługują zabezpieczeń lub które mają wyłączone zabezpieczenia, chyba że wymiana sieciowa jest zabezpieczona za pomocą innych metod.  
  
## <a name="system-provided-bindings"></a>Wiązania dostarczane przez system  
 Poniższe powiązania są dostarczane z usługą WCF.  
  
|Wiązanie|Element konfiguracji|Opis|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Powiązanie odpowiednie do komunikacji z usługami sieci Web zgodnymi z profilem WS-Basic, na przykład usługi ASP.NET Web Services (ASMX). To powiązanie używa protokołu HTTP jako transportu i tekstu/XML jako domyślnego kodowania wiadomości.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Bezpieczne i interoperacyjne powiązanie odpowiednie dla kontraktów usługi non-Duplex.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Bezpieczne i interoperacyjne powiązanie, które zapewnia obsługę prawidłowych wersji <xref:System.ServiceModel.WSHttpBinding.Security%2A>elementów, <xref:System.ServiceModel.ReliableSession>i <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> powiązań.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Bezpieczne i interoperacyjne powiązanie odpowiednie dla kontraktów usługi dupleksowej lub komunikacji za pośrednictwem pośredników SOAP.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Bezpieczne i interoperacyjne powiązanie obsługujące protokół WS-Federation, umożliwiając organizacjom, które znajdują się w Federacji, wydajne uwierzytelnianie i Autoryzowanie użytkowników.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|Bezpieczne i interoperacyjne powiązanie, które wynika z <xref:System.ServiceModel.WS2007HttpBinding> i obsługuje zabezpieczenia federacyjne.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Bezpieczne i zoptymalizowane powiązanie odpowiednie dla komunikacji między aplikacjami w aplikacjach WCF.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Bezpieczne, niezawodne i zoptymalizowane powiązanie, które jest odpowiednie dla komunikacji na komputerze między aplikacjami WCF.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<> usługi Msmqbinding](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Umieszczone w kolejce powiązanie, które jest odpowiednie dla komunikacji między komputerami w aplikacjach WCF.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Powiązanie umożliwiające bezpieczną komunikację obejmującą wiele maszyn.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Powiązanie używane do konfigurowania punktów końcowych dla usług sieci Web WCF, które są udostępniane za pośrednictwem żądań HTTP zamiast komunikatów protokołu SOAP.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Powiązanie, które jest odpowiednie dla komunikacji między komputerami między aplikacją WCF a istniejącymi aplikacjami usługi kolejkowania komunikatów (znanymi także jako MSMQ).|  
  
## <a name="binding-features"></a>Funkcje powiązań  
 W następnej tabeli przedstawiono niektóre z najważniejszych funkcji, które zostały dostarczone przez poszczególne powiązania dostarczone przez system. Powiązania są wymienione w pierwszej kolumnie, a informacje dotyczące funkcji są opisane w tabeli. Poniższa tabela zawiera klucz dla użytych skrótów wiązania. Aby wybrać powiązanie, ustal, która kolumna spełnia wszystkie potrzebne funkcje wiersza.  
  
|Wiązanie|Współdziałanie|Tryb zabezpieczeń (wartość domyślna)|Sesja<br /><br /> (Domyślnie)|Transakcje|Dupleks|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Profil podstawowy 1,1|(Brak), transport, komunikat, mieszany|Brak, (brak)|Dawaj|n/d|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|Brak, transport, (wiadomość), mieszany|(Brak), transport, sesja niezawodna|(Brak), tak|n/d|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-Security, WS-Trust, WS-SecureConversation, WS-SecurityPolicy|Brak, transport, (wiadomość), mieszany|(Brak), transport, sesja niezawodna|(Brak), tak|n/d|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|Brak, (komunikat)|(Niezawodna sesja)|(Brak), tak|Tak|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|Brak, (komunikat), mieszany|(Brak), sesja niezawodna|(Brak), tak|Nie|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|WS-Federation|Brak, (komunikat), mieszany|(Brak), sesja niezawodna|(Brak), tak|Nie|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|Brak, (transport), komunikat:<br /><br /> Mieszana|Niezawodna sesja, (transport)|(Brak), tak|Tak|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|Dawaj<br /><br /> Transportu|Brak, (transport)|(Brak), tak|Tak|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Brak, komunikat, (transport), oba|Dawaj|(Brak), tak|Nie|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Równorzędn|Brak, komunikat, (transport), mieszany|Dawaj|Dawaj|Tak|  
|<xref:System.ServiceModel.WebHttpBinding>|.Net|None, Transport, TransportCredentialOnly|Dawaj|Dawaj|n/d|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|Usługa MSMQ|Brak, (transport)|Dawaj|(Brak), tak|n/d|  
  
 W poniższej tabeli objaśniono funkcje Znalezione w poprzedniej tabeli.  
  
|Funkcja|Opis|  
|-------------|-----------------|  
|Typ współdziałania|Nazwa protokołu lub technologii, za pomocą których powiązanie zapewnia międzyoperacyjność.|  
|Zabezpieczenia|Określa sposób zabezpieczania kanału:<br /><br /> Dawaj Komunikat protokołu SOAP nie jest zabezpieczony i klient nie jest uwierzytelniony.<br />Transportu Wymagania dotyczące zabezpieczeń są spełnione w warstwie transportowej.<br />Pojawi Wymagania dotyczące zabezpieczeń są spełnione w warstwie komunikatów.<br />Mieszana Ten tryb zabezpieczeń jest znany jako `TransportWithMessageCredentials`. Obsługuje ona poświadczenia na poziomie komunikatu, a wymagania dotyczące integralności i poufności są spełnione przez warstwę transportu.<br />Jedn Używane są zarówno zabezpieczenia na poziomie komunikatów, jak i na poziomie transportu. Ta możliwość jest unikatowa dla <xref:System.ServiceModel.NetMsmqBinding>.|  
|Sesja|Określa, czy to powiązanie obsługuje kontrakty sesji.|  
|Transakcje|Określa, czy transakcje są włączone.|  
|Dupleks|Określa, czy są obsługiwane umowy dupleksowe. Uwaga Ta funkcja wymaga obsługi sesji w powiązaniu.|  
|Przesyłanie strumieniowe|Określa, czy przesyłanie strumieniowe komunikatów jest obsługiwane.|  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd tworzenia punktów końcowych](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
