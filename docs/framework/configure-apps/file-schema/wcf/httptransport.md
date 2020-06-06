---
title: <httpTransport>
ms.date: 03/30/2017
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
ms.openlocfilehash: b3558db6018d79f0fad27ff28657bfadb5637467
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736768"
---
# \<httpTransport>
Określa transport HTTP do przesyłania komunikatów SOAP dla niestandardowego powiązania.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpTransport>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<httpTransport allowCookies="Boolean"
               authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"
               bypassProxyOnLocal="Boolean"
               hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"
               keepAliveEnabled="Boolean"
               maxBufferSize="Integer"
               proxyAddress="Uri"
               proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"
               realm="String"
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
|authenticationScheme|Określa protokół używany do uwierzytelniania żądań klientów przetwarzanych przez odbiornik HTTP. Prawidłowe wartości to:<br /><br /> -Digest: Określa uwierzytelnianie szyfrowane.<br />-Negocjuj: negocjuje z klientem w celu określenia schematu uwierzytelniania. Jeśli zarówno klient, jak i serwer obsługują protokół Kerberos, jest używany; w przeciwnym razie jest używane uwierzytelnianie NTLM.<br />-NTLM: Określa uwierzytelnianie NTLM.<br />-Basic: określa podstawowe uwierzytelnianie.<br />-Anonymous: Określa uwierzytelnianie anonimowe.<br /><br /> Wartość domyślna to anonimowe. Ten atrybut jest typu <xref:System.Net.AuthenticationSchemes> . Ten atrybut można ustawić tylko raz.|  
|bypassProxyOnLocal|Wartość logiczna wskazująca, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.<br /><br /> Adres lokalny to ten, który znajduje się w lokalnej sieci LAN lub intranecie.<br /><br /> Windows Communication Foundation (WCF) zawsze ignoruje serwer proxy, jeśli adres usługi zaczyna się od `http://localhost` .<br /><br /> Jeśli chcesz, aby klienci przechodzą przez serwer proxy podczas rozmowy z usługami na tym samym komputerze, należy użyć nazwy hosta zamiast hosta lokalnego.|  
|hostnameComparisonMode|Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI. Prawidłowe wartości to,<br /><br /> -StrongWildcard: ("+") dopasowuje wszystkie możliwe nazwy hostów w kontekście określonego schematu, portu i względnego identyfikatora URI.<br />-Exact: brak symboli wieloznacznych<br />-WeakWildcard: (" \* ") dopasowuje wszystkie możliwe nazwy hosta w kontekście określonego schematu, portu i względnego UIR, które nie zostały dopasowane jawnie lub przez mechanizm silnego symbolu wieloznacznego.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode> . Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>.|  
|keepAliveEnabled|Wartość logiczna określająca, czy należy nawiązać trwałe połączenie z zasobem internetowym.|  
|maxBufferSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar buforu. Wartość domyślna to 524288|  
|proxyAddress|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useSystemWebProxy` jest `true` , to ustawienie musi być `null` . Wartość domyślna to `null`.|  
|proxyAuthenticationScheme|Określa protokół używany do uwierzytelniania żądań klientów przetwarzanych przez serwer proxy HTTP. Prawidłowe wartości to:<br /><br /> -Brak: nie jest wykonywane żadne uwierzytelnianie.<br />-Digest: Określa uwierzytelnianie szyfrowane.<br />-Negocjuj: negocjuje z klientem w celu określenia schematu uwierzytelniania. Jeśli zarówno klient, jak i serwer obsługują protokół Kerberos, jest używany; w przeciwnym razie jest używane uwierzytelnianie NTLM.<br />-NTLM: Określa uwierzytelnianie NTLM.<br />-Basic: określa podstawowe uwierzytelnianie.<br />-Anonymous: Określa uwierzytelnianie anonimowe.<br /><br /> Wartość domyślna to anonimowe. Ten atrybut jest typu <xref:System.Net.AuthenticationSchemes> . Należy pamiętać, że <xref:System.Net.AuthenticationSchemes.IntegratedWindowsAuthentication?displayProperty=nameWithType> nie jest to obsługiwane.|  
|obszarów|Ciąg określający obszar, który ma być używany na serwerze proxy/serwer. Wartość domyślna to pusty ciąg.<br /><br /> Serwery używają obszarów do partycjonowania chronionych zasobów. Każda partycja może mieć własny schemat uwierzytelniania i/lub bazę danych autoryzacji. Obszary są używane tylko do uwierzytelniania podstawowego i szyfrowanego. Po pomyślnym uwierzytelnieniu klienta uwierzytelnianie jest prawidłowe dla wszystkich zasobów w danym obszarze. Aby uzyskać szczegółowy opis obszarów, zobacz RFC 2617 w [witrynie IETF](https://www.ietf.org).|  
|Elementy TransferMode|Określa, czy komunikaty są buforowane, czy przesyłane strumieniowo, czy z żądaniem lub odpowiedzią. Prawidłowe wartości to:<br /><br /> -Buffered: komunikaty żądania i odpowiedzi są buforowane.<br />Przesyłane strumieniowo: komunikaty żądania i odpowiedzi są przesyłane strumieniowo.<br />-StreamedRequest: komunikat żądania jest przesyłany strumieniowo, a komunikat odpowiedzi jest buforowany.<br />-StreamedResponse: komunikat żądania jest buforowany, a komunikat odpowiedzi jest przesyłany strumieniowo.<br /><br /> Wartość domyślna jest buforowana. Ten atrybut jest typu <xref:System.ServiceModel.TransferMode> .|  
|unsafeConnectionNtlmAuthentication|Wartość logiczna określająca, czy na serwerze jest włączone bezpieczne udostępnianie połączenia. Wartość domyślna to `false`. Jeśli ta funkcja jest włączona, uwierzytelnianie NTLM jest wykonywane raz dla każdego połączenia TCP.|  
|useDefaultWebProxy|Wartość logiczna określająca, czy są używane ustawienia serwera proxy dla całego komputera, a nie ustawienia specyficzne dla użytkownika. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 `httpTransport`Element jest punktem początkowym do tworzenia niestandardowego powiązania, które implementuje protokół transportu HTTP. Protokół HTTP to podstawowy transport używany do celów współdziałania. Ten transport jest obsługiwany przez Windows Communication Foundation (WCF) w celu zapewnienia współdziałania z innymi stosami usług sieci Web innych niż WCF.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.HttpTransportElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Transporty](../../../wcf/feature-details/transports.md)
- [Wybieranie transportu](../../../wcf/feature-details/choosing-a-transport.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
