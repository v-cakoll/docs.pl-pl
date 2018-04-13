---
title: '&lt;httpsTransport&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f6ed4bc0-7e38-4348-9259-30bf61eb9435
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 78b0cc2dd260b773c29b8684ab94bfaa0afffff2
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="lthttpstransportgt"></a>&lt;httpsTransport&gt;
Określa protokół transportu HTTP przekazywania wiadomości SOAP do niestandardowego powiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<httpsTransport>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<httpsTransport  
    allowCookies=Boolean"  
    authenticationScheme="Digest/Negotiate/Ntlm/Basic/Anonymous"  
    bypassProxyOnLocal=Boolean"  
    hostnameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
    manualAddressing="Boolean"  
    maxBufferPoolSize="Integer"  
    maxBufferSize="Integer"  
    maxReceivedMessageSize="Integer"  
    proxyAddress="Uri"  
    proxyAuthenticationScheme="None/Digest/Negotiate/Ntlm/Basic/Anonymous"        realm="String"  
    requireClientCertificate=Boolean"  
    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
        unsafeConnectionNtlmAuthentication="Boolean"  
....useDefaultWebProxy="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|allowCookies|Wartość logiczna określająca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań. Wartość domyślna to `false`.<br /><br /> Ten atrybut można użyć w przypadku interakcji z usługami sieci Web ASMX, które używają plików cookie. W ten sposób można się upewnić, że pliki cookie zwrócony z serwera, automatycznie są kopiowane do wszystkich przyszłych żądań dla tej usługi.|  
|authenticationScheme|Określa protokół używany do uwierzytelniania żądań klientów przetwarzanych przez odbiornik HTTP. Prawidłowe wartości są następujące:<br /><br /> -Skrótu: Określa uwierzytelnianie szyfrowane.<br />-Negocjowania: Negocjuje z klienta w celu określenia schematu uwierzytelniania. Jeśli zarówno klient, jak i serwer obsługują protokół Kerberos, jest używany; w przeciwnym razie uwierzytelnianie NTLM jest używany.<br />-Ntlm: Określa uwierzytelniania NTLM.<br />-Basic: Określa uwierzytelnianie podstawowe.<br />-Anonimowe: Określa uwierzytelnianie anonimowe.<br /><br /> Wartość domyślna to anonimowe. Ten atrybut jest typu <xref:System.Net.AuthenticationSchemes>. Ten atrybut można ustawić tylko raz.|  
|bypassProxyOnLocal|Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.<br /><br /> Lokalny adres jest taki, który znajduje się w lokalnej sieci LAN lub intranet.<br /><br /> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Zawsze ignoruje serwera proxy, jeśli adres usługi rozpoczyna się od http://localhost.<br /><br /> Jeśli klienci mają przechodzić przez serwer proxy po rozmowie z usługi na tym samym komputerze, należy używać nazwy hosta zamiast localhost.|  
|hostnameComparisonMode|Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI. Prawidłowe wartości to,<br /><br /> -StrongWildcard: ("+") dopasowuje wszystkie możliwe nazwy hostów w kontekście określony schemat, port i względnym identyfikatorem URI.<br />-Dokładnie: bez symboli wieloznacznych<br />-WeakWildcard: ("*") zgodna wszystkie możliwe hosta w kontekście określony schemat, port i względną UIR, która nie została jawnie dopasowana lub za pośrednictwem mechanizmu silne symboli wieloznacznych.<br /><br /> Wartość domyślna to StrongWildcard. Ten atrybut jest typu `System.ServiceModel.HostnameComparison`.|  
|Opcję ManualAddressing|Wartość logiczna, która umożliwia użytkownikowi przejęcie kontroli nad adresowaniem komunikatów. Ta właściwość jest zwykle używana w scenariuszach router gdzie aplikacji Określa jedną z kilku miejsca docelowe, aby wysłać wiadomość.<br /><br /> Jeśli wartość `true`, zakłada kanału wiadomości już został rozwiązany i nie dodaje żadnych dodatkowych informacji do niego. Użytkownik może następnie indywidualnie adresów każdej wiadomości.<br /><br /> Jeśli wartość `false`, domyślny mechanizm adresowania Windows Communication Foundation (WCF) automatycznie tworzy adresy dla wszystkich wiadomości.<br /><br /> Wartość domyślna to `false`.|  
|maxBufferPoolSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar puli buforów. Wartość domyślna to 524288.<br /><br /> Wiele elementów WCF za pomocą buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna. Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe. W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.|  
|wartość maxBufferSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar buforu. Wartość domyślna to 524288|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny dopuszczalny rozmiar wiadomości, który może zostać odebrany. Wartość domyślna to 65536.|  
|proxyAddress|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useSystemWebProxy` jest `true`, to ustawienie musi być `null`. Wartość domyślna to `null`.|  
|proxyAuthenticationScheme|Określa protokół używany do uwierzytelniania żądań klientów przetwarzanych przez serwer proxy HTTP. Prawidłowe wartości są następujące:<br /><br /> -Brak: Uwierzytelnianie nie jest wykonywane.<br />-Skrótu: Określa uwierzytelnianie szyfrowane.<br />-Negocjowania: Negocjuje z klienta w celu określenia schematu uwierzytelniania. Jeśli zarówno klient, jak i serwer obsługują protokół Kerberos, jest używany; w przeciwnym razie uwierzytelnianie NTLM jest używany.<br />-Ntlm: Określa uwierzytelniania NTLM.<br />-Basic: Określa uwierzytelnianie podstawowe.<br />-Anonimowe: Określa uwierzytelnianie anonimowe.<br />-IntegratedWindowsAuthentication: Określa uwierzytelnianie systemu Windows.<br /><br /> Wartość domyślna to anonimowe. Ten atrybut jest typu <xref:System.Net.AuthenticationSchemes>.|  
|obszar|Ciąg określający obszar na użycie na proxy/serwerze. Wartość domyślna to ciąg pusty.<br /><br /> Serwery używają obszarów do partycjonowania chronionych zasobów. Każda partycja może mieć własną schematu i/lub autoryzacji bazy danych uwierzytelniania. Obszarów są używane tylko w przypadku basic i uwierzytelniania szyfrowanego. Po pomyślnym uwierzytelnieniu klient, uwierzytelnianie jest prawidłowa dla wszystkich zasobów w danym obszarze. Szczegółowy opis obszarów, zobacz dokument RFC 2617 na http://www.ietf.org.|  
|requireClientCertificate|Wartość logiczna określająca, czy serwer wymaga od klienta zapewnienia certyfikatu klienta jako część uzgadniania przez HTTPS. Wartość domyślna to `false`.|  
|Tryb transferu|Określa, czy komunikaty są buforowane lub przesyłane strumieniowo lub żądania lub odpowiedzi. Prawidłowe wartości są następujące:<br /><br /> -Buforowane: Komunikatów żądań i odpowiedzi są buforowane.<br />-Strumieniowego: Komunikatów żądań i odpowiedzi są przesyłane strumieniowo.<br />-StreamedRequest: Strumieniowego komunikatu żądania i komunikat odpowiedzi są buforowane.<br />-StreamedResponse: Komunikat żądania są buforowane, a komunikat odpowiedzi przesyłanej strumieniowo.<br /><br /> Wartość domyślna jest buforowana. Ten atrybut jest typu <xref:System.ServiceModel.TransferMode>.|  
|unsafeConnectionNtlmAuthentication|Wartość logiczna określająca, czy na serwerze włączone jest niebezpieczne udostępnianie połączenia. Wartość domyślna to `false`. Włączenie uwierzytelniania NTLM jest wykonywana raz na każde połączenie TCP.|  
|useDefaultWebProxy|Wartość logiczna określająca, czy ustawienia serwera proxy dla komputera są używane zamiast ustawień użytkownika. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 `httpsTransport` Element jest punkt początkowy do tworzenia niestandardowego powiązania, który implementuje ten protokół transportu HTTPS. HTTPS jest używana do celów współdziałania bezpiecznych transportu podstawowego. HTTPS jest obsługiwana przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] zapewnienie współdziałania z innymi sieci Web usług stosów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.HttpsTransportElement>  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Transporty](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Wybieranie transportu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
