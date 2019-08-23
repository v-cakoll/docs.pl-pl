---
title: <httpsTransport>
ms.date: 03/30/2017
ms.assetid: f6ed4bc0-7e38-4348-9259-30bf61eb9435
ms.openlocfilehash: b70236e8bba93a49ca5b53538333fa63283a5f0a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928522"
---
# <a name="httpstransport"></a>\<httpsTransport>
Określa transport HTTP do przesyłania komunikatów SOAP dla niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<httpsTransport>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<httpsTransport allowCookies="Boolean"
                authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"
                bypassProxyOnLocal="Boolean"
                hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                manualAddressing="Boolean"
                maxBufferPoolSize="Integer"
                maxBufferSize="Integer"
                maxReceivedMessageSize="Integer"
                proxyAddress="Uri"
                proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"
                realm="String"
                requireClientCertificate="Boolean"
                transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
                unsafeConnectionNtlmAuthentication="Boolean"
                useDefaultWebProxy="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|allowCookies|Wartość logiczna określająca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań. Wartość domyślna to `false`.<br /><br /> Tego atrybutu można używać podczas współpracy z usługami sieci Web ASMX, które używają plików cookie. W ten sposób można mieć pewność, że pliki cookie zwrócone z serwera są automatycznie kopiowane do wszystkich przyszłych żądań klientów dla tej usługi.|  
|authenticationScheme|Określa protokół używany do uwierzytelniania żądań klientów przetwarzanych przez odbiornik HTTP. Prawidłowe wartości to:<br /><br /> Szyfrowane Określa uwierzytelnianie szyfrowane.<br />Negocjować Negocjuje z klientem w celu określenia schematu uwierzytelniania. Jeśli zarówno klient, jak i serwer obsługują protokół Kerberos, jest używany; w przeciwnym razie jest używane uwierzytelnianie NTLM.<br />NTLM Określa uwierzytelnianie NTLM.<br />Prosty Określa podstawowe uwierzytelnianie.<br />Anonimowe Określa uwierzytelnianie anonimowe.<br /><br /> Wartość domyślna to anonimowe. Ten atrybut jest typu <xref:System.Net.AuthenticationSchemes>. Ten atrybut można ustawić tylko raz.|  
|bypassProxyOnLocal|Wartość logiczna wskazująca, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.<br /><br /> Adres lokalny to ten, który znajduje się w lokalnej sieci LAN lub intranecie.<br /><br /> Windows Communication Foundation (WCF) zawsze ignoruje serwer proxy, jeśli adres usługi zaczyna `http://localhost`się od.<br /><br /> Jeśli chcesz, aby klienci przechodzą przez serwer proxy podczas rozmowy z usługami na tym samym komputerze, należy użyć nazwy hosta zamiast hosta lokalnego.|  
|hostnameComparisonMode|Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI. Prawidłowe wartości to,<br /><br /> -StrongWildcard: ("+") dopasowuje wszystkie możliwe nazwy hostów w kontekście określonego schematu, portu i względnego identyfikatora URI.<br />-Exact: brak symboli wieloznacznych<br />-WeakWildcard: ("\*") dopasowuje wszystkie możliwe nazwy hosta w kontekście określonego schematu, portu i względnego UIR, które nie zostały dopasowane jawnie lub przez mechanizm silnego symbolu wieloznacznego.<br /><br /> Wartość domyślna to StrongWildcard. Ten atrybut jest typu `System.ServiceModel.HostnameComparison`.|  
|Opcję ManualAddressing|Wartość logiczna umożliwiająca użytkownikowi przejęcie kontroli nad adresowaniem komunikatów. Ta właściwość jest zwykle używana w scenariuszach routera, gdzie aplikacja określa, z której jednego z kilku miejsc docelowych ma być wysyłany komunikat.<br /><br /> Gdy jest ustawiona `true`na, kanał zakłada, że komunikat został już rozkierowany i nie dodaje do niego żadnych dodatkowych informacji. Użytkownik może następnie osobno rozwiązać każdy komunikat.<br /><br /> W przypadku ustawienia `false`opcji domyślny mechanizm adresowania Windows Communication Foundation (WCF) automatycznie tworzy adresy dla wszystkich komunikatów.<br /><br /> Wartość domyślna to `false`.|  
|maxBufferPoolSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar puli buforów. Wartość domyślna to 524288.<br /><br /> Wiele części usługi WCF korzysta z buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne. W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu. W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.|  
|maxBufferSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar buforu. Wartość domyślna to 524288|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny dopuszczalny rozmiar wiadomości, która może zostać odebrana. Wartość domyślna to 65536.|  
|proxyAddress|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useSystemWebProxy` `null`jest `true`, to ustawienie musi być. Wartość domyślna to `null`.|  
|proxyAuthenticationScheme|Określa protokół używany do uwierzytelniania żądań klientów przetwarzanych przez serwer proxy HTTP. Prawidłowe wartości to:<br /><br /> Dawaj Nie jest wykonywane żadne uwierzytelnianie.<br />Szyfrowane Określa uwierzytelnianie szyfrowane.<br />Negocjować Negocjuje z klientem w celu określenia schematu uwierzytelniania. Jeśli zarówno klient, jak i serwer obsługują protokół Kerberos, jest używany; w przeciwnym razie jest używane uwierzytelnianie NTLM.<br />NTLM Określa uwierzytelnianie NTLM.<br />Prosty Określa podstawowe uwierzytelnianie.<br />Anonimowe Określa uwierzytelnianie anonimowe.<br /><br /> Wartość domyślna to anonimowe. Ten atrybut jest typu <xref:System.Net.AuthenticationSchemes>. Należy pamiętać <xref:System.Net.AuthenticationSchemes.IntegratedWindowsAuthentication?displayProperty=nameWithType> , że nie jest to obsługiwane.|  
|obszarów|Ciąg określający obszar, który ma być używany na serwerze proxy/serwer. Wartość domyślna to pusty ciąg.<br /><br /> Serwery używają obszarów do partycjonowania chronionych zasobów. Każda partycja może mieć własny schemat uwierzytelniania i/lub bazę danych autoryzacji. Obszary są używane tylko do uwierzytelniania podstawowego i szyfrowanego. Po pomyślnym uwierzytelnieniu klienta uwierzytelnianie jest prawidłowe dla wszystkich zasobów w danym obszarze. Aby uzyskać szczegółowy opis obszarów, zobacz RFC 2617 w [witrynie IETF](https://www.ietf.org).|  
|requireClientCertificate|Wartość logiczna określająca, czy serwer wymaga od klienta podania certyfikatu klienta w ramach uzgadniania HTTPS. Wartość domyślna to `false`.|  
|transferMode|Określa, czy komunikaty są buforowane, czy przesyłane strumieniowo, czy z żądaniem lub odpowiedzią. Prawidłowe wartości to:<br /><br /> Grywać Komunikaty żądania i odpowiedzi są buforowane.<br />Przesyłane strumieniowo Komunikaty żądania i odpowiedzi są przesyłane strumieniowo.<br />- StreamedRequest: Komunikat żądania jest przesyłany strumieniowo, a komunikat odpowiedzi jest buforowany.<br />- StreamedResponse: Komunikat żądania jest buforowany, a komunikat odpowiedzi jest przesyłany strumieniowo.<br /><br /> Wartość domyślna jest buforowana. Ten atrybut jest typu <xref:System.ServiceModel.TransferMode>.|  
|unsafeConnectionNtlmAuthentication|Wartość logiczna określająca, czy na serwerze jest włączone bezpieczne udostępnianie połączenia. Wartość domyślna to `false`. Jeśli ta funkcja jest włączona, uwierzytelnianie NTLM jest wykonywane raz dla każdego połączenia TCP.|  
|useDefaultWebProxy|Wartość logiczna określająca, czy są używane ustawienia serwera proxy dla całego komputera, a nie ustawienia specyficzne dla użytkownika. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 `httpsTransport` Element jest punktem początkowym do tworzenia niestandardowego powiązania, które implementuje protokół transportowy https. HTTPS to podstawowy transport używany do celów bezpiecznego współdziałania. Protokół HTTPS jest obsługiwany przez Windows Communication Foundation (WCF) w celu zapewnienia współdziałania z innymi stosami usług sieci Web.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.HttpsTransportElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transporty](../../../wcf/feature-details/transports.md)
- [Wybieranie transportu](../../../wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
