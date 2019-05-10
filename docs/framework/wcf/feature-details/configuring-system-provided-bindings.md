---
title: Konfigurowanie powiązań dostarczanych przez system
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
ms.openlocfilehash: 49aacdc7db6bc9e8b951f69bcd880835bb9182f2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654506"
---
# <a name="configuring-system-provided-bindings"></a>Konfigurowanie powiązań dostarczanych przez system
Powiązania określić mechanizm komunikacji w przypadku do punktu końcowego i określają, jak połączyć się z punktem końcowym. Powiązania składają się z elementów, które określają, jak kanałów Windows Communication Foundation (WCF) są warstwowe się zapewnienie funkcji na wymaganą komunikację. Powiązanie zawiera trzy rodzaje elementów:  
  
- Elementy powiązania kanału protokołu, które określają zabezpieczeń, niezawodności, ustawieniach przepływu kontekstu lub protokołów zdefiniowanych przez użytkownika za pomocą wiadomości, które są wysyłane do punktu końcowego.  
  
- Kanał elementy powiązania transportu, które określają podstawową transport protokół do użycia podczas wysyłania wiadomości do punktu końcowego, na przykład, TCP lub HTTP.  
  
- Elementy powiązania, które określają kodowanie o komunikacji sieciowej na potrzeby wiadomości, które są wysyłane do punktu końcowego, na przykład, text/XML, binarne, kodowania komunikatu lub komunikat transmisji optymalizacji mechanizm (MTOM).  
  
 W tym temacie przedstawiono wszystkie powiązania dostarczane przez system Windows Communication Foundation (WCF). Jeśli nie spełnia żadnego z tych dokładnych wymaganiach dla aplikacji, można utworzyć powiązania za pomocą <xref:System.ServiceModel.Channels.CustomBinding> klasy. Aby uzyskać więcej informacji na temat tworzenia powiązań niestandardowych, zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
> [!IMPORTANT]
>  Wybierz powiązanie z włączonymi zabezpieczeniami. Domyślnie wszystkie powiązania z wyjątkiem <xref:System.ServiceModel.BasicHttpBinding> powiązania ma włączoną obsługą zabezpieczeń. Jeśli nie zaznaczysz bezpiecznego powiązania lub wyłączyć zabezpieczenia, upewnij się, że Twoje wymiany sieci są chronione w inny sposób, na przykład w Centrum zabezpieczonych danych lub w sieci izolowanej.  
  
> [!IMPORTANT]
>  Nie należy używać kontrakty dwukierunkowe powiązań, które nie obsługują zabezpieczeń lub mają zabezpieczeń wyłączona, chyba że exchange sieci jest zabezpieczony za pomocą innych środków.  
  
## <a name="system-provided-bindings"></a>Wiązania dostarczane przez system  
 Następujące powiązania są dostarczane z programem WCF.  
  
|Wiązanie|Element konfiguracji|Opis|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Powiązania, który nadaje się do komunikowania się z profilu WS-Basic zgodność usług sieci Web, na przykład usługi sieci Web platformy ASP.NET (ASMX)-na podstawie usług. To powiązanie korzysta z protokołu HTTP jako transportu i text/XML jako domyślne kodowanie komunikatu.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Bezpieczne i interoperacyjne powiązanie odpowiednie dla kontraktów na usługę non-duplex.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Bezpieczne i interoperacyjne powiązanie, które zapewnia obsługę dla poprawnych wersji <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, i <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementów wiązania.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Bezpieczne i interoperacyjne powiązanie odpowiednie dla kontraktów usługi duplex lub komunikacji za pośrednictwem pośredników SOAP.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Bezpieczne i interoperacyjne powiązanie obsługuje protokół WS-Federation, umożliwiając organizacjom, które znajdują się w Federacji, aby efektywnie uwierzytelnianie i autoryzowanie użytkowników.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|Bezpieczne i interoperacyjne powiązanie pochodzi od klasy <xref:System.ServiceModel.WS2007HttpBinding> i obsługuje federacyjnego zabezpieczenia.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Bezpieczne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami między aplikacjami usług WCF.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji na maszynie między aplikacjami usług WCF.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Zakolejkowane powiązanie, które jest odpowiednie dla komunikacji między komputerami między aplikacjami usług WCF.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Wiązanie, która umożliwia komunikację bezpieczne, obejmujących wiele maszyn.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Wiązanie używane do konfigurowania punktów końcowych usługi sieci Web WCF, które są udostępniane za pośrednictwem żądania HTTP zamiast na wiadomości SOAP.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Powiązanie, które jest odpowiednie dla komunikacji między komputerami między aplikacji WCF i istniejące usługi kolejkowania komunikatów (MSMQ) aplikacji.|  
  
## <a name="binding-features"></a>Powiązanie funkcji  
 W następnej tabeli przedstawiono niektóre najważniejsze funkcje każdego powiązania dostarczane przez system, pod warunkiem. Powiązania znajdują się w pierwszej kolumnie, a informacje dotyczące funkcji są opisane w tabeli. Poniższa tabela zawiera klucz, wiązanie skrótów używanych. Aby wybrać powiązanie, określić kolumnę, która spełnia wszystkie funkcje wiersza, których potrzebujesz.  
  
|Wiązanie|Współdziałanie|Tryb zabezpieczeń (ustawienie domyślne)|Sesja<br /><br /> (Domyślnie)|Transakcje|Dupleks|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|1.1 profilu podstawowego|(Brak), mieszane transportu, wiadomości,|Brak, (Brak)|(Brak)|n/d|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|Brak, Transport, (komunikat) mieszane|(Brak), Transport, niezawodnej sesji|Tak (Brak)|n/d|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-Security, WS-Trust, WS-SecureConversation, WS-SecurityPolicy|Brak, Transport, (komunikat) mieszane|(Brak), Transport, niezawodnej sesji|Tak (Brak)|n/d|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|Brak (komunikat)|(Niezawodnej sesji)|Tak (Brak)|Yes|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|Brak (komunikat) mieszane|(Brak), niezawodnej sesji|Tak (Brak)|Nie|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|WS-Federation|Brak (komunikat) mieszane|(Brak), niezawodnej sesji|Tak (Brak)|Nie|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|Brak, (transportu), wiadomości,<br /><br /> Mieszane|Sesja niezawodna (transportu)|Tak (Brak)|Yes|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|Brak,<br /><br /> (Transportu)|Brak (transportu)|Tak (Brak)|Tak|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Brak, komunikat (transportu), zarówno|(Brak)|Tak (Brak)|Nie|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Elementu równorzędnego|Mieszane None, komunikat (transportu)|(Brak)|(Brak)|Tak|  
|<xref:System.ServiceModel.WebHttpBinding>|.Net|None, Transport, TransportCredentialOnly|(Brak)|(Brak)|n/d|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|Usługa MSMQ|Brak (transportu)|(Brak)|Tak (Brak)|n/d|  
  
 W poniższej tabeli opisano funkcje w powyższej tabeli.  
  
|Funkcja|Opis|  
|-------------|-----------------|  
|Typ elementu|Nazwy protokołu lub technologii, z którym powiązanie zapewnia współdziałanie.|  
|Zabezpieczenia|Określa, jak jest zabezpieczony kanał:<br /><br /> -Brak: Komunikat protokołu SOAP nie jest zabezpieczony, a klient nie jest uwierzytelniony.<br />-Transport: Wymagania dotyczące zabezpieczeń są spełnione w warstwie transportowej.<br />-Komunikat o błędzie: W warstwie komunikat spełnione są wymagania dotyczące zabezpieczeń.<br />-Mieszane: Ten tryb zabezpieczeń jest znany jako `TransportWithMessageCredentials`. Obsługuje on poświadczenia na poziomie komunikatu i wymagania dotyczące integralności i poufności informacji są spełnione przez warstwy transportowej.<br />-Zarówno: Używane są oba poziom i mechanizm transportu zabezpieczeniami na poziomie wiadomości. Ta możliwość jest unikatowy dla <xref:System.ServiceModel.NetMsmqBinding>.|  
|Sesja|Określa, czy to powiązanie obsługuje kontraktów sesji.|  
|Transakcje|Określa, czy włączono transakcji.|  
|Dupleks|Określa, czy kontrakty dwukierunkowe są obsługiwane. Należy pamiętać, że ta funkcja wymaga obsługi sesji w powiązaniu.|  
|Przesyłanie strumieniowe|Określa, czy wiadomości, przesyłania strumieniowego jest obsługiwane.|  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd tworzenia punktów końcowych](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
