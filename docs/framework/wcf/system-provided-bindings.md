---
title: powiązania dostarczane przez system
description: Informacje dotyczące wszystkich powiązań dostarczanych przez system Windows Communication Foundation (WCF).
ms.date: 06/05/2018
helpviewer_keywords:
- bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
ms.openlocfilehash: 3c6c6b628d208aede8c547dcfa66fc189a26ae01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569611"
---
# <a name="system-provided-bindings"></a>powiązania dostarczane przez system

Powiązania określić mechanizm komunikacji w przypadku do punktu końcowego i określają, jak połączyć się z punktem końcowym. Powiązanie zawiera następujące elementy:

- Określa stos protokołu, bezpieczeństwa, niezawodności i ustawienia przepływu kontekstu do użycia dla wiadomości wysyłanych do punktu końcowego.

- Transport Określa protokół transportowy podstawowy do użycia podczas wysyłania wiadomości do punktu końcowego, na przykład, TCP lub HTTP.

- Kodowanie Określa kodowanie do użycia dla wiadomości wysyłanych do punktu końcowego podczas transmisji. Na przykład tekstu/XML, binarne lub komunikat transmisji optymalizacji mechanizm (MTOM).

 Ten artykuł przedstawia wszystkie powiązania dostarczane przez system Windows Communication Foundation (WCF). Jeśli żadna z tych powiązań spełnia dokładnych kryteriów dla aplikacji, można utworzyć niestandardowego powiązania. Aby uzyskać więcej informacji na temat tworzenia powiązań niestandardowych, zobacz [powiązań niestandardowych](./extending/custom-bindings.md).

 Bezpieczne i interoperacyjne powiązanie, która obsługuje protokół WS-Federation umożliwia organizacjom, które znajdują się w Federacji, aby efektywnie uwierzytelnianie i autoryzowanie użytkowników.

> [!IMPORTANT]
> Zawsze wybierz powiązanie, które obejmuje zabezpieczeń. Domyślnie wszystkie powiązania z wyjątkiem [ \<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) elementu mieć włączoną obsługą zabezpieczeń. Jeśli nie wybierz bezpiecznego powiązania lub wyłączyć zabezpieczenia, pamiętaj chronić dane w inny sposób, takich jak przechowywanie w Centrum zabezpieczonych danych lub w sieci izolowanej.

> [!IMPORTANT]
> Nigdy nie używaj kontrakty dwukierunkowe powiązań, które nie obsługują zabezpieczeń lub które mają wyłączony do momentu zabezpieczyć dane za pomocą innych środków bezpieczeństwa.

Polecenia następujących powiązania są dostarczane z programem WCF:

|Powiązanie|Element konfiguracji|Opis|
|-------------|---------------------------|-----------------|
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md)|Powiązania, który jest odpowiedni do komunikowania się z usługami internetowymi zgodny profilu WS-Basic, na przykład usługi sieci Web platformy ASP.NET (ASMX)-na podstawie usług. To powiązanie korzysta z protokołu HTTP jako transportu i text/XML jako domyślne kodowanie komunikatu.|
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md)|Bezpieczne i interoperacyjne powiązanie odpowiednie dla kontraktów na usługę non-duplex.|
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Bezpieczne i interoperacyjne powiązanie odpowiednie dla kontraktów usługi duplex lub komunikacji za pośrednictwem pośredników SOAP.|
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Bezpieczne i interoperacyjne powiązanie obsługuje protokół WS-Federation, co umożliwia organizacjom, które znajdują się w Federacji, aby efektywnie uwierzytelnianie i autoryzowanie użytkowników.|
|<xref:System.ServiceModel.NetHttpBinding>|[\<netHttpBinding>](../configure-apps/file-schema/wcf/nethttpbinding.md)|Powiązanie przeznaczone do używania usług HTTP i WebSocket, który używa kodowania binarnego domyślnie.|
|<xref:System.ServiceModel.NetHttpsBinding>|[\<netHttpsBinding>](../configure-apps/file-schema/wcf/nethttpsbinding.md)|Bezpiecznego powiązania przeznaczone do używania usług HTTP i WebSocket, który używa kodowania binarnego domyślnie.|
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)|Bezpieczne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami między aplikacjami usług WCF.|
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../configure-apps/file-schema/wcf/netnamedpipebinding.md)|Bezpieczne, niezawodne i zoptymalizowane powiązanie odpowiednie dla komunikacji na maszynie między aplikacjami usług WCF.|
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../configure-apps/file-schema/wcf/netmsmqbinding.md)|Zakolejkowane powiązanie, które jest odpowiednie dla komunikacji między komputerami między aplikacjami usług WCF.|
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding>](../configure-apps/file-schema/wcf/netpeertcpbinding.md)|Powiązanie, która umożliwia bezpieczną, wiele komunikacji z komputerami.|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Powiązanie, które jest odpowiednie dla komunikacji między komputerami między aplikacji WCF i kolejkowania istniejące aplikacje.|
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<basicHttpContextBinding>](../configure-apps/file-schema/wcf/basichttpcontextbinding.md)|Powiązanie odpowiednie dla komunikacji z usługami sieci Web Zgodność profilu WS-Basic, który umożliwia plików cookie protokołu HTTP używanego do wymiany kontekstu.|
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding>](../configure-apps/file-schema/wcf/nettcpcontextbinding.md)|Bezpieczne i zoptymalizowane powiązanie odpowiednie dla komunikacji między komputerami między aplikacjami, WCF, który umożliwia nagłówków protokołu SOAP ma być używany do wymiany kontekstu.|
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../configure-apps/file-schema/wcf/webhttpbinding.md)|Wiązanie używane do konfigurowania punktów końcowych usługi sieci Web WCF, które są udostępniane za pośrednictwem żądania HTTP zamiast na wiadomości SOAP.|
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding>](../configure-apps/file-schema/wcf/wshttpcontextbinding.md)|Bezpieczne i interoperacyjne powiązanie odpowiednie dla kontraktów na usługę non-duplex umożliwiająca nagłówków protokołu SOAP ma być używany do wymiany kontekstu.|
|<xref:System.ServiceModel.UdpBinding>|[\<udpBinding>](../configure-apps/file-schema/wcf/udpbinding.md)|Wiązanie używane podczas wysyłania rozbiciem proste wiadomości do dużej liczby klientów jednocześnie.|

 W poniższej tabeli przedstawiono funkcje każdego powiązania dostarczane przez system. Powiązania znajdują się w kolumnach tabeli; funkcje są wymienione w wiersze i opisano w drugiej tabeli. Poniższa tabela zawiera klucz, wiązanie skrótów używanych. Aby wybrać powiązanie, określić kolumnę, która spełnia wszystkie funkcje wiersza, których potrzebujesz.

|Powiązanie|Współdziałanie|Zabezpieczenia (ustawienie domyślne)|Sesja<br />(Domyślnie)|Transakcje|Dupleks|Kodowania (ustawienie domyślne)|Przesyłanie strumieniowe<br />(Domyślnie)|
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|
|<xref:System.ServiceModel.BasicHttpBinding>|1.1 profilu podstawowego|(Brak), mieszane transportu, wiadomości,|(Brak)|(Brak)|n/d|Tekst (MTOM)|Tak<br />(buforowanej)|
|<xref:System.ServiceModel.WSHttpBinding>|WS|Mieszane transportu, (komunikat)|(Brak), niezawodnej sesji, sesja zabezpieczeń|Tak (Brak)|n/d|(Tekst), MTOM|Nie|
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(Komunikat), Brak|(Niezawodnej sesji), sesja zabezpieczeń|Tak (Brak)|Tak|(Tekst), MTOM|Nie|
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|(Komunikat) mieszany, Brak|(Brak), niezawodnej sesji, sesja zabezpieczeń|Tak (Brak)|Nie|(Tekst), MTOM|Nie|
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(Brak), Transport, komunikat o błędzie, TransportWithMessageCredential, TransportCredentialOnly|Zobacz Uwaga poniżej|Brak|Zobacz Uwaga poniżej|(Plik binarny), tekst, MTOM|Tak (buforowanej)|
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(Transportu) TransportWithMessageCredential|Zobacz Uwaga poniżej|Brak|Zobacz Uwaga poniżej|(Plik binarny), tekst, MTOM|Tak<br />(buforowanej)|
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(Transportu), wiadomości, None, mieszanego|(Transportu), niezawodnej sesji, sesja zabezpieczeń|Tak (Brak)|Tak|plików binarnych|Tak<br />(buforowanej)|
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(Transportu), Brak|Brak (transportu)|Tak (Brak)|Tak|plików binarnych|Tak<br />(buforowanej)|
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Komunikat (transportu), Brak|(Brak), transportu|Brak (tak)|Nie|plików binarnych|Nie|
|<xref:System.ServiceModel.NetPeerTcpBinding>|Elementu równorzędnego|(Transportu)|(Brak)|(Brak)|Tak||Nie|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|Usługa MSMQ|(Transportu)|(Brak)|Brak (tak)|n/d|n/d|Nie|
|<xref:System.ServiceModel.BasicHttpContextBinding>|1.1 profilu podstawowego|(Brak), mieszane transportu, wiadomości,|(Brak)|(Brak)|n/d|Tekst (MTOM)|Tak<br />(buforowanej)|
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(Transportu), wiadomości, None, mieszanego|(Transportu), niezawodnej sesji, sesja zabezpieczeń|Tak (Brak)|Tak|plików binarnych|Tak<br />(buforowanej)|
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|Mieszane transportu, (komunikat)|(Brak), niezawodnej sesji, sesja zabezpieczeń|Tak (Brak)|n/d|Tekst (MTOM)|Nie|
|<xref:System.ServiceModel.UdpBinding> <br /><br /> **Uwaga:**  Można osiągnąć współdziałanie, implementując standard Specyfikacja SOAP-over-UDP, która implementuje tego powiązania.|.NET|(Brak)|(Brak)|(Brak)|n/d|(Tekst)|Nie|

> [!IMPORTANT]
> <xref:System.ServiceModel.NetHttpBinding> jest przeznaczony dla korzystanie z usług HTTP i WebSocket powiązanie i używa kodowania binarnego domyślnie. <xref:System.ServiceModel.NetHttpBinding> wykrywa, czy jest on używany za pomocą kontraktu dwukierunkowego lub kontraktu "żądanie odpowiedź" i zmianę zachowania sobie odpowiadać; używa protokołu HTTP "żądanie-odpowiedź" i technologia WebSockets drukowania dwustronnego. To zachowanie można przesłonić przy użyciu <xref:System.ServiceModel.Channels.WebSocketTransportUsage> powiązanie ustawienia: WhenDuplex — jest to wartość domyślna i zachowuje się zgodnie z powyższym opisem. Nigdy nie - zapobiega to Websocket używana. Podjęto próbę pomocą kontraktu dwukierunkowego powoduje wyjątek to ustawienie. Zawsze — wymusza WebSockets ma być używany, nawet w przypadku kontraktów "żądanie odpowiedź". NetHttpBinding obsługuje niezawodne sesje zarówno w trybie HTTP, jak i w trybie protokołu WebSocket. W WebSocket trybu sesji są dostarczane przez transportu.

 W poniższej tabeli opisano funkcje wymienione w powyższej tabeli.

|Funkcja|Opis|
|-------------|-----------------|
|Typ elementu|Nazwy protokołu lub technologii, z którym powiązanie zapewnia współdziałanie.|
|Zabezpieczenia|Określa, jak jest zabezpieczony kanał:<br />-Brak: Komunikat protokołu SOAP nie jest zabezpieczony, a klient nie jest uwierzytelniony.<br />-Transport: Wymagania dotyczące zabezpieczeń są spełnione w warstwie transportowej.<br />-Komunikat o błędzie: W warstwie komunikat spełnione są wymagania dotyczące zabezpieczeń.<br />-Mieszane: Oświadczenia są przenoszone w message; wymagania dotyczące integralności i poufności informacji są spełnione przez warstwy transportowej.|
|Sesja|Określa, czy to powiązanie obsługuje kontraktów sesji.|
|Transakcje|Określa, czy włączono transakcji.|
|Dupleks|Określa, czy kontrakty dwukierunkowe są obsługiwane. Pamiętaj, że ta funkcja wymaga pomocy technicznej dla sesji w powiązaniu.|
|Kodowanie|Określa format przewodowy wiadomości. Dopuszczalne wartości obejmują:<br />-Text: na przykład UTF-8.<br />-Binarne<br />— Mechanizmu optymalizacji transmisji wiadomości (MTOM): Metoda efektywne kodowanie binarne elementy XML w kontekście koperty protokołu SOAP.|
|Przesyłanie strumieniowe|Określa, czy przesyłania strumieniowego jest obsługiwane dla komunikatów przychodzących i wychodzących. Użyj `TransferMode` właściwości powiązania, które można ustawić wartości. Dopuszczalne wartości obejmują:<br />- <xref:System.ServiceModel.TransferMode.Buffered>: Komunikaty żądań i odpowiedzi zarówno buforowana.<br />- <xref:System.ServiceModel.TransferMode.Streamed>: Komunikaty żądań i odpowiedzi zarówno strumieniowo.<br />- <xref:System.ServiceModel.TransferMode.StreamedRequest>: Komunikat żądania są przesyłane strumieniowo, a komunikat odpowiedzi są buforowane.<br />- <xref:System.ServiceModel.TransferMode.StreamedResponse>: Komunikat żądania są buforowane, a komunikat odpowiedzi są przesyłane strumieniowo.|

## <a name="see-also"></a>Zobacz także

- [Przegląd tworzenia punktów końcowych](endpoint-creation-overview.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](using-bindings-to-configure-services-and-clients.md)
- [Podstawy programowania przy użyciu programu WCF](basic-wcf-programming.md)
