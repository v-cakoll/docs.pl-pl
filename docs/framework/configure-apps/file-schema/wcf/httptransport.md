---
title: '&lt;httpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
ms.openlocfilehash: ddce1053a7494a84d0266c7ad14f6b1937365fa5
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316431"
---
# <a name="lthttptransportgt"></a>&lt;httpTransport&gt;
Określa protokół transportu HTTP przekazywania wiadomości SOAP do niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<httpTransport>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<httpTransport  
    allowCookies=Boolean"  
    authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"  
    bypassProxyOnLocal=Boolean"  
    hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
    keepAliveEnabled="Boolean"  
    maxBufferSize="Integer"  
    proxyAddress="Uri"  
    proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"  
IntegratedWindowsAuthentication: Specifies Windows authentication"  
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
|allowCookies|Wartość logiczna określająca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań. Wartość domyślna to `false`.<br /><br /> Podczas interakcji z usługami sieci Web ASMX, które używają plików cookie, można użyć tego atrybutu. W ten sposób można się upewnić, że pliki cookie, zwrócona z serwera są automatycznie kopiowane do wszystkich przyszłych żądań za daną usługę.|  
|authenticationScheme|Określa protokół używany do uwierzytelniania żądań klienta przetwarzanych przez odbiornik HTTP. Prawidłowe wartości są następujące:<br /><br /> -Podsumowanie: Określa uwierzytelnianie szyfrowane.<br />-Negocjowania: Negocjuje z klientem, aby określić schemat uwierzytelniania. Jeśli zarówno klient, jak i serwer obsługują protokół Kerberos, jest używany; w przeciwnym razie uwierzytelnianie NTLM jest używany.<br />-Ntlm: Określa uwierzytelniania NTLM.<br />-Podstawowa: Określa podstawowego uwierzytelniania.<br />-Anonimowe: Określa uwierzytelnianie anonimowe.<br /><br /> Wartość domyślna to anonimowe. Ten atrybut jest typu <xref:System.Net.AuthenticationSchemes>. Ten atrybut można ustawić tylko raz.|  
|bypassProxyOnLocal|Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.<br /><br /> Lokalny adres jest taki, który znajduje się w lokalnej sieci LAN albo sieci intranet.<br /><br /> Windows Communication Foundation (WCF) zawsze ignoruje serwera proxy, jeśli adres usługi zaczyna się od `http://localhost`.<br /><br /> Należy używać nazwy hosta zamiast nazwy localhost, gdy klienci mają go za pośrednictwem serwera proxy w przypadku usług na tym samym komputerze.|  
|hostnameComparisonMode|Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI. Prawidłowe wartości to,<br /><br /> -StrongWildcard: ("+") jest zgodna wszystkich możliwych nazw hostów w kontekście określony schemat, port i względną identyfikatora URI.<br />— Dokładnie: bez symboli wieloznacznych<br />-WeakWildcard: ("\*") jest zgodna wszystkich możliwych nazwą hosta w kontekście określony schemat, port i względną UIR, które nie zostały jawnie dopasowany lub za pośrednictwem mechanizmu silny symbol wieloznaczny.<br /><br /> Wartość domyślna to StrongWildcard. Ten atrybut jest typu `System.ServiceModel.HostnameComparisonMode`.|  
|keepAliveEnabled|Wartość logiczna określająca, czy ustanowić trwałe połączenie z zasobem internetowym.|  
|wartość maxBufferSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar buforu. Wartość domyślna to 524288|  
|proxyAddress|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useSystemWebProxy` jest `true`, to ustawienie musi być `null`. Wartość domyślna to `null`.|  
|proxyAuthenticationScheme|Określa protokół używany do uwierzytelniania żądań klienta przetwarzanych przez serwer proxy HTTP. Prawidłowe wartości są następujące:<br /><br /> -Brak: Uwierzytelnianie nie jest wykonywane.<br />-Podsumowanie: Określa uwierzytelnianie szyfrowane.<br />-Negocjowania: Negocjuje z klientem, aby określić schemat uwierzytelniania. Jeśli zarówno klient, jak i serwer obsługują protokół Kerberos, jest używany; w przeciwnym razie uwierzytelnianie NTLM jest używany.<br />-Ntlm: Określa uwierzytelniania NTLM.<br />-Podstawowa: Określa podstawowego uwierzytelniania.<br />-Anonimowe: Określa uwierzytelnianie anonimowe.<br />-Opcji IntegratedWindowsAuthentication: Określa uwierzytelniania Windows.<br /><br /> Wartość domyślna to anonimowe. Ten atrybut jest typu <xref:System.Net.AuthenticationSchemes>.|  
|obszar|Ciąg, który określa obszar na użycie na proxy/serwerze. Wartość domyślna to ciąg pusty.<br /><br /> Serwery używają obszary do partycjonowania chronionych zasobów. Każda partycja może mieć własny schemat i/lub autoryzacji bazy danych uwierzytelniania. Obszarów są używane tylko w przypadku podstawowe i uwierzytelnianie szyfrowane. Po klient pomyślnie uwierzytelnia, uwierzytelniania jest prawidłowy dla wszystkich zasobów w danego obszaru. Aby uzyskać szczegółowy opis obszarów, zobacz RFC 2617 na [IETF witryny sieci Web](https://www.ietf.org).|  
|Tryb transferu|Określa, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi. Prawidłowe wartości są następujące:<br /><br /> -Buforowane: Komunikatów żądań i odpowiedzi są buforowane.<br />-Strumieniowo: Komunikatów żądań i odpowiedzi są przesyłane strumieniowo.<br />-StreamedRequest: Komunikat żądania są przesyłane strumieniowo, a komunikat odpowiedzi są buforowane.<br />-StreamedResponse: Komunikat żądania są buforowane, a komunikat odpowiedzi są przesyłane strumieniowo.<br /><br /> Domyślnie są buforowane. Ten atrybut jest typu <xref:System.ServiceModel.TransferMode> .|  
|unsafeConnectionNtlmAuthentication|Wartość logiczna określająca, czy na serwerze włączone jest niebezpieczne udostępnianie połączenia internetowego. Wartość domyślna to `false`. Jeśli włączona, uwierzytelnianie NTLM jest wykonywana raz na każde połączenie TCP.|  
|useDefaultWebProxy|Wartość logiczna określająca, czy ustawienia serwera proxy dla komputera są używane zamiast ustawień użytkownika. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 `httpTransport` Element jest punktem wyjścia do tworzenia niestandardowego powiązania, który implementuje protokół transportu HTTP. Protokół HTTP jest transportu podstawowego, używane do celów współpracy. Transport jest obsługiwany przez Windows Communication Foundation (WCF) w celu zapewnienia współdziałania z innymi stosów usługi internetowej WCF.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.HttpTransportElement>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Transporty](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Wybieranie transportu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
