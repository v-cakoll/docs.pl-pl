---
title: '&lt;httpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 8b30c065-b32a-4fa3-8eb4-5537a9c6b897
ms.openlocfilehash: 77400348e9adc31d8121fc75f46d75d757af270f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
|allowCookies|Wartość logiczna określająca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań. Wartość domyślna to `false`.<br /><br /> Ten atrybut można użyć w przypadku interakcji z usługami sieci Web ASMX, które używają plików cookie. W ten sposób można się upewnić, że pliki cookie zwrócony z serwera, automatycznie są kopiowane do wszystkich przyszłych żądań dla tej usługi.|  
|authenticationScheme|Określa protokół używany do uwierzytelniania żądań klientów przetwarzanych przez odbiornik HTTP. Prawidłowe wartości są następujące:<br /><br /> -Skrótu: Określa uwierzytelnianie szyfrowane.<br />-Negocjowania: Negocjuje z klienta w celu określenia schematu uwierzytelniania. Jeśli zarówno klient, jak i serwer obsługują protokół Kerberos, jest używany; w przeciwnym razie uwierzytelnianie NTLM jest używany.<br />-Ntlm: Określa uwierzytelniania NTLM.<br />-Basic: Określa uwierzytelnianie podstawowe.<br />-Anonimowe: Określa uwierzytelnianie anonimowe.<br /><br /> Wartość domyślna to anonimowe. Ten atrybut jest typu <xref:System.Net.AuthenticationSchemes>. Ten atrybut można ustawić tylko raz.|  
|bypassProxyOnLocal|Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.<br /><br /> Lokalny adres jest taki, który znajduje się w lokalnej sieci LAN lub intranet.<br /><br /> Windows Communication Foundation (WCF) zawsze ignoruje serwera proxy, jeśli zaczyna się od adresu usługi http://localhost.<br /><br /> Jeśli klienci mają przechodzić przez serwer proxy po rozmowie z usługi na tym samym komputerze, należy używać nazwy hosta zamiast localhost.|  
|hostnameComparisonMode|Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI. Prawidłowe wartości to,<br /><br /> -StrongWildcard: ("+") dopasowuje wszystkie możliwe nazwy hostów w kontekście określony schemat, port i względnym identyfikatorem URI.<br />-Dokładnie: bez symboli wieloznacznych<br />-WeakWildcard: ("*") zgodna wszystkie możliwe hosta w kontekście określony schemat, port i względną UIR, która nie została jawnie dopasowana lub za pośrednictwem mechanizmu silne symboli wieloznacznych.<br /><br /> Wartość domyślna to StrongWildcard. Ten atrybut jest typu `System.ServiceModel.HostnameComparisonMode`.|  
|KeepAliveEnabled|Wartość logiczna, która określa, czy ustanowić trwałe połączenie z zasobem internetowym.|  
|wartość maxBufferSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar buforu. Wartość domyślna to 524288|  
|proxyAddress|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useSystemWebProxy` jest `true`, to ustawienie musi być `null`. Wartość domyślna to `null`.|  
|proxyAuthenticationScheme|Określa protokół używany do uwierzytelniania żądań klientów przetwarzanych przez serwer proxy HTTP. Prawidłowe wartości są następujące:<br /><br /> -Brak: Uwierzytelnianie nie jest wykonywane.<br />-Skrótu: Określa uwierzytelnianie szyfrowane.<br />-Negocjowania: Negocjuje z klienta w celu określenia schematu uwierzytelniania. Jeśli zarówno klient, jak i serwer obsługują protokół Kerberos, jest używany; w przeciwnym razie uwierzytelnianie NTLM jest używany.<br />-Ntlm: Określa uwierzytelniania NTLM.<br />-Basic: Określa uwierzytelnianie podstawowe.<br />-Anonimowe: Określa uwierzytelnianie anonimowe.<br />-IntegratedWindowsAuthentication: Określa uwierzytelnianie systemu Windows.<br /><br /> Wartość domyślna to anonimowe. Ten atrybut jest typu <xref:System.Net.AuthenticationSchemes>.|  
|obszar|Ciąg określający obszar na użycie na proxy/serwerze. Wartość domyślna to ciąg pusty.<br /><br /> Serwery używają obszarów do partycjonowania chronionych zasobów. Każda partycja może mieć własną schematu i/lub autoryzacji bazy danych uwierzytelniania. Obszarów są używane tylko w przypadku basic i uwierzytelniania szyfrowanego. Po pomyślnym uwierzytelnieniu klient, uwierzytelnianie jest prawidłowa dla wszystkich zasobów w danym obszarze. Szczegółowy opis obszarów, zobacz dokument RFC 2617 na http://www.ietf.org.|  
|Tryb transferu|Określa, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi. Prawidłowe wartości są następujące:<br /><br /> -Buforowane: Komunikatów żądań i odpowiedzi są buforowane.<br />-Strumieniowego: Komunikatów żądań i odpowiedzi są przesyłane strumieniowo.<br />-StreamedRequest: Strumieniowego komunikatu żądania i komunikat odpowiedzi są buforowane.<br />-StreamedResponse: Komunikat żądania są buforowane, a komunikat odpowiedzi przesyłanej strumieniowo.<br /><br /> Wartość domyślna jest buforowana. Ten atrybut jest typu <xref:System.ServiceModel.TransferMode> .|  
|unsafeConnectionNtlmAuthentication|Wartość logiczna określająca, czy na serwerze włączone jest niebezpieczne udostępnianie połączenia. Wartość domyślna to `false`. Włączenie uwierzytelniania NTLM jest wykonywana raz na każde połączenie TCP.|  
|useDefaultWebProxy|Wartość logiczna określająca, czy ustawienia serwera proxy dla komputera są używane zamiast ustawień użytkownika. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 `httpTransport` Element jest punkt początkowy do tworzenia niestandardowego powiązania, który implementuje ten protokół transportu HTTP. HTTP jest transportu podstawowego używana do celów współdziałania. Ten transport jest obsługiwany przez Windows Communication Foundation (WCF), aby zapewnić współdziałanie z innymi stosy usług WCF Web.  
  
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
