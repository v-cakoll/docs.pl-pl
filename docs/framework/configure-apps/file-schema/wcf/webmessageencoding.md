---
title: '&lt;webMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: 90102c25c1c5b83af8f629d18b790af9297fa88c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640254"
---
# <a name="ltwebmessageencodinggt"></a>&lt;webMessageEncoding&gt;
Umożliwia zwykłego tekstu XML, kodowania wiadomości notacji obiektu JavaScript (JSON) i "nieprzetworzonej" zawartości binarnej Odczyt i zapis, gdy jest używana w powiązaniu usługi Windows Communication Foundation (WCF).  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<webMessageEncoding>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`maxReadPoolSize`|Liczba wiadomości, które można jednocześnie odczytać bez przydziału nowych czytników. Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy. Wartość domyślna to 64 czytelnicy dla każdego z wewnętrznego koderów (tekst JSON i "pierwotne").<br /><br /> Zwiększa to liczba zużycie pamięci zwiększa, ale przygotowuje kodera radzenia sobie z gwałtownym wzrostem wzrosty komunikaty przychodzące, ponieważ jest w stanie używać czytelnicy z puli, które zostały już utworzone, zamiast tworzyć nowe.|  
|`maxWritePoolSize`|Liczba wiadomości, które można jednocześnie wysłać bez przydziału nowych modułów zapisujących. Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy. Wartość domyślna to 16 autorzy dla każdego z wewnętrznego koderów (tekst JSON i "pierwotne").<br /><br /> Zwiększa to liczba zużycie pamięci zwiększa, ale przygotowuje kodera radzenia sobie z gwałtownym wzrostem wzrosty komunikaty wychodzące, ponieważ jest w stanie używać składników zapisywania z puli, które zostały już utworzone, zamiast tworzyć nowe.|  
|`writeEncoding`|Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków. Prawidłowe wartości to:<br /><br /> -   UnicodeFffeTextEncoding: Big Endian kodowanie Unicode.<br />-   Utf16TextEncoding: Kodowanie Unicode.<br />-   Utf8TextEncoding: 8-bitowego kodowania.<br /><br /> The default is Utf8TextEncoding. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Kodowanie jest procesem przekształcania wiadomość do sekwencji bajtów. Dekodowanie jest procesu. Procesy te wymagają specyfikację kodowania znaków.  
  
 `webMessageEncoding` Elementu działa przez delegowanie do szeregu wewnętrzny koderów obsługi kodowania XML i JSON zwykłego tekstu które "" dane binarne. To delegowanie odbywa się przez koder komunikat złożony.  
  
 Ten element powiązania i jego złożonego encoder, które są używane do kontrolowania, kodowania w scenariuszach, które nie korzystają z protokołu SOAP wiadomości, używane przez `webHttpBinding` elementu. Te scenariusze obejmują "Zwykłego starego kodu XML" (POX), technologii Representational State Transfer (REST), syndykacji naprawdę proste syndykacji (RSS) i Atom i asynchronicznego języka JavaScript i XML (technologia AJAX). Koder komunikatów złożonego nie obsługuje protokołu SOAP lub WS-Addressing.  
  
 Można skonfigurować elementu powiązania z kodowaniem znaków zapisu przy użyciu `writeEncoding` atrybutu. Podane <xref:System.Text.Encoding> wartość określa zachowanie podczas zapisu w przypadkach, JSON i XML tekstową. Podczas odczytu wszelkie kodowanie prawidłowy komunikat i kodowanie tekstu w zrozumieniu.  
  
 `maxReadPoolSize` i `maxWritePoolSize` można również ustawić maksymalną liczbę czytników i składników zapisywania do przydzielenia, odpowiednio. Domyślnie są przydzielane 64 czytników i składników zapisywania 16.  
  
 Domyślne ograniczenia złożoności również są ustawiane przy użyciu [ \<readerQuotas >](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) element, aby zapewnić ochronę przed klasą typu odmowa usługi (DOS) ataki taka próba blokując przetwarzania punktu końcowego za pomocą złożoności wiadomości zasoby.  
  
## <a name="example"></a>Przykład  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [Kodowanie komunikatu](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)
- [Wybieranie kodera komunikatów](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
