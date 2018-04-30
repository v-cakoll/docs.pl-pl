---
title: Konfigurowanie powiązań dostarczanych przez system
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
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9bbf04f549c492ddc392b429edf3a703f3c307a0
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-system-provided-bindings"></a>Konfigurowanie powiązań dostarczanych przez system
Powiązania Określ mechanizm komunikacji po rozmowie z punktu końcowego i określić sposób nawiązywania połączenia z punktem końcowym. Powiązania składają się z elementów, które definiują sposób [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kanały są warstwie się zapewnienie funkcje wymagane komunikacji. Powiązanie zawiera trzy rodzaje elementów:  
  
-   Elementy powiązania kanału protokołu, które określają zabezpieczeń, niezawodności, ustawień przepływu kontekstu lub protokołów zdefiniowane przez użytkownika do użycia z wiadomości, które są wysyłane do punktu końcowego.  
  
-   Elementy powiązania kanałów, które określają podstawowy protokół transportu podczas wysyłania komunikatów do punktu końcowego, np. TCP lub HTTP transportu.  
  
-   Elementy powiązania, które określają przewodowy kodowanie do użycia dla komunikatów wysyłanych do punktu końcowego, na przykład, text/XML, binarne, kodowania komunikatu lub mechanizmu optymalizacji transmisji wiadomości (MTOM).  
  
 W tym temacie przedstawiono wszystkie dostarczane przez system [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] powiązania. Jeśli nie spełnia żadnego z tych dokładne wymagania dotyczące aplikacji, można utworzyć powiązania za pomocą <xref:System.ServiceModel.Channels.CustomBinding> klasy. Aby uzyskać więcej informacji o tworzeniu niestandardowych powiązań, zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
> [!IMPORTANT]
>  Wybierz powiązania z włączonymi zabezpieczeniami. Domyślnie wszystkie powiązania z wyjątkiem <xref:System.ServiceModel.BasicHttpBinding> powiązanie, mają włączoną obsługą zabezpieczeń. Jeśli nie wybierzesz bezpiecznego powiązania lub wyłączenie zabezpieczeń, upewnij się, że Twoje wymiany sieci są chronione w inny sposób, na przykład w Centrum zabezpieczonych danych lub w sieci izolowanej.  
  
> [!IMPORTANT]
>  Nie należy używać kontrakty dwukierunkowe z powiązaniami, które nie obsługują zabezpieczeń lub mają zabezpieczeń wyłączone, chyba że sieci exchange jest zabezpieczone przy użyciu innych metod.  
  
## <a name="system-provided-bindings"></a>Powiązania dostarczane przez system  
 Dołączone są następujące powiązania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
|Powiązanie|Element konfiguracji|Opis|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Powiązanie, które jest odpowiednie dla komunikacji z profilu WS-Basic zgodność usług sieci Web, na przykład usługi sieci Web platformy ASP.NET (ASMX) — na podstawie usług. To powiązanie korzysta z protokołu HTTP jako transportu i tekstu/XML jako domyślne kodowanie komunikatu.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Bezpieczne i interoperacyjne powiązanie odpowiednie dla kontraktów na usługę non-duplex.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Bezpieczne i interoperacyjne powiązanie, która zapewnia obsługę dla poprawnych wersji <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, i <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementów wiązania.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Bezpieczne i interoperacyjne powiązanie odpowiednie dla kontraktów usługi duplex lub komunikacji za pośrednictwem pośredników SOAP.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Bezpieczne i interoperacyjne powiązanie obsługuje protokół WS-Federation, włączanie organizacji, które znajdują się w Federacji, aby wydajnie uwierzytelniania i autoryzacji użytkowników.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|Bezpieczne i interoperacyjne powiązanie, która jest pochodną <xref:System.ServiceModel.WS2007HttpBinding> i obsługuje zabezpieczeń.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Bezpieczne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Bezpieczne, niezawodne i zoptymalizowane powiązanie, które jest odpowiednie dla komunikacji na komputerze między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Zakolejkowane powiązanie, które jest odpowiednie dla komunikacji między komputerami między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Powiązanie, które umożliwia komunikację bezpiecznego, obejmujących wiele maszyn.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Wiązanie używane do konfigurowania punktów końcowych dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług, które są dostępne za pośrednictwem żądania HTTP zamiast na wiadomości SOAP sieci Web.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Powiązanie, które jest odpowiednie dla komunikacji między komputerami między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji i istniejące aplikacje usługi kolejkowania komunikatów (MSMQ).|  
  
## <a name="binding-features"></a>Powiązanie funkcji  
 W następnej tabeli przedstawiono niektóre najważniejsze funkcje każdego powiązania dostarczane przez system, pod warunkiem. Powiązania są wyświetlane w pierwszej kolumnie i informacje dotyczące funkcji jest opisany w tabeli. Poniższa tabela zawiera klucz, skróty powiązanie użyte. Aby wybrać powiązanie, określić kolumnę, która spełnia wszystkie potrzebne funkcje wiersza.  
  
|Powiązanie|Współdziałanie|Tryb zabezpieczeń (ustawienie domyślne)|Sesja<br /><br /> (Domyślnie)|Transakcje|Dupleks|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(Brak), Transport, wiadomości, mieszany|Brak, (Brak)|(Brak)|n/d|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|Brak, Transport, (komunikat) mieszany|(Brak), Transport, niezawodnej sesji|Tak (Brak)|n/d|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-Security WS-Trust, WS-SecureConversation WS SecurityPolicy|Brak, Transport, (komunikat) mieszany|(Brak), Transport, niezawodnej sesji|Tak (Brak)|n/d|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|Brak (komunikat)|(Niezawodnej sesji)|Tak (Brak)|Tak|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|Brak (komunikat) mieszany|(Brak), niezawodnej sesji|Tak (Brak)|Nie|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|WS-Federation|Brak (komunikat) mieszany|(Brak), niezawodnej sesji|Tak (Brak)|Nie|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|Brak, (transportu), wiadomości<br /><br /> Mieszane|Niezawodnej sesji, (transportu)|Tak (Brak)|Tak|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|Brak,<br /><br /> (Transportu)|Brak (transportu)|Tak (Brak)|Tak|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Brak, wiadomości (transportu), zarówno|(Brak)|Tak (Brak)|Nie|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|elementów równorzędnych|Mieszane None, wiadomości (transportu)|(Brak)|(Brak)|Tak|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|Usługa MSMQ|Brak (transportu)|(Brak)|Tak (Brak)|n/d|  
  
 W poniższej tabeli przedstawiono funkcje znalezione w poprzedniej tabeli.  
  
|Funkcja|Opis|  
|-------------|-----------------|  
|Typ współdziałanie|Nazwy protokołu lub technologii, z którym powiązania zapewnia współdziałanie.|  
|Zabezpieczenia|Określa, jak chronione są kanału:<br /><br /> -Brak: Wiadomości protokołu SOAP nie jest zabezpieczony, a klient nie jest uwierzytelniony.<br />-Transport: Spełnione są wymagania dotyczące zabezpieczeń w warstwie transportowej.<br />-Komunikat o błędzie: Spełnione są wymagania dotyczące zabezpieczeń w warstwie wiadomości.<br />-Mieszane: Ten tryb zabezpieczeń nosi nazwę `TransportWithMessageCredentials`. Obsługuje on poświadczeń na poziomie komunikatu i spełnione są wymagania dotyczące integralności i poufności przez warstwę transportu.<br />-Oba: Zarówno komunikat zabezpieczeń na poziomie poziomu i transportu są używane. Ta możliwość jest unikatowy dla <xref:System.ServiceModel.NetMsmqBinding>.|  
|Sesja|Określa, czy to powiązanie obsługuje kontrakty sesji.|  
|Transakcje|Określa, czy transakcje są włączone.|  
|Dupleks|Określa, czy kontrakty dwukierunkowe są obsługiwane. Należy zauważyć, że ta funkcja wymaga obsługi sesji w powiązaniu.|  
|przesyłanie strumieniowe|Określa, czy przesyłanie strumieniowe wiadomości jest obsługiwane.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd tworzenia punktów końcowych](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Konfigurowanie usług i klientów za pomocą powiązań](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
