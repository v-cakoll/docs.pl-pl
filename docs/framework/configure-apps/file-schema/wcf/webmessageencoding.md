---
title: '&lt;webMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9629ecbe744ac1f4bbd44e22ac42a3e81fff27a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebmessageencodinggt"></a>&lt;webMessageEncoding&gt;
Włącza zwykłego tekstu XML, kodowania wiadomości notacji obiektu JavaScript (JSON) i "nieprzetworzonej" zawartości binarnej na odczyt i zapis w [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] powiązania.  
  
 \<system.serviceModel >  
\<powiązania >  
\<customBinding >  
\<Powiązanie >  
\<webMessageEncoding >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webMessageEncoding   
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`maxReadPoolSize`|Liczba wiadomości, które można jednocześnie odczytać bez przydziału nowych czytników. Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy. Wartość domyślna to 64 czytników dla każdego wewnętrzny koderów (tekst JSON i "nieprzetworzonej").<br /><br /> Zwiększenie tego numeru zużycie pamięci wzrośnie, ale przygotowuje kodera do postępowania w przypadku nagłego Seria wiadomości przychodzących, ponieważ jest w stanie używać czytników z puli, które zostały już utworzone, zamiast tworzyć nowe.|  
|`maxWritePoolSize`|Liczba wiadomości, które można jednocześnie wysłać bez przydziału nowych modułów zapisujących. Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy. Wartość domyślna to 16 autorów dla każdego wewnętrzny koderów (tekst JSON i "nieprzetworzonej").<br /><br /> Zwiększenie tego numeru zużycie pamięci wzrośnie, ale przygotowuje kodera do postępowania w przypadku nagłego seria wychodzących wiadomości, ponieważ jest w stanie używać autorów z puli, które zostały już utworzone, zamiast tworzyć nowe.|  
|`writeEncoding`|Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków. Prawidłowe wartości to:<br /><br /> -UnicodeFffeTextEncoding: Big Endian kodowanie Unicode.<br />-Utf16TextEncoding: Kodowanie Unicode.<br />-Utf8TextEncoding: 8-bitowego kodowania.<br /><br /> Wartość domyślna to Utf8TextEncoding. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Kodowanie jest procesem przekształcania komunikat do sekwencji bajtów. Dekodowanie jest procesu. Te procesy wymagają specyfikacji kodowania znaków.  
  
 `webMessageEncoding` Element działa przez delegowanie do serii wewnętrzny koderów na kodowań XML i JSON zwykłego tekstu, a "" dane binarne. To Delegowanie jest realizowane przez koder komunikatów złożonego.  
  
 Ten element powiązania i jego encoder złożone są używane do kontrolowania, kodowania w scenariuszach, które nie korzystają z protokołu SOAP wiadomości używanych przez `webHttpBinding` elementu. Te scenariusze obejmują "XML starego zwykły" (POX), Representational State (Transfer REST), zespolonego naprawdę proste Syndication (RSS) i Atom i asynchronicznego JavaScript i XML (AJAX). Koder komunikatów złożonego nie obsługuje protokołu SOAP lub WS-Addressing.  
  
 Element powiązania można skonfigurować za pomocą znaku zapisu przy użyciu kodowania `writeEncoding` atrybutu. Podana <xref:System.Text.Encoding> wartość określa zachowanie podczas zapisu w przypadkach, JSON i XML tekstową. Na odczyt wszelkie kodowanie prawidłowego elementu message i kodowanie tekstu jest rozpoznawany.  
  
 `maxReadPoolSize`i `maxWritePoolSize` można również ustawić maksymalną liczbę czytelników i zapisywania odpowiednio przydzielone. Domyślnie są przydzielane 64 czytelników i 16 modułów zapisujących.  
  
 Domyślne ograniczenia złożoności są również ustawiane przy użyciu [ \<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) elementu, aby zapewnić ochronę przed klasą odmowa usługi (DOS) przed atakami opartymi na tym próbę użycia złożoności wiadomości wiązać przetwarzania punktu końcowego zasoby.  
  
## <a name="example"></a>Przykład  
  
```xml  
<webMessageEncoding   
    maxReadPoolSize="256"  
    maxWritePoolSize="128"  
    messageVersion="None"  
    textEncoding="utf-8"   
/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [Kodowanie komunikatu](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Wybieranie kodera komunikatów](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
