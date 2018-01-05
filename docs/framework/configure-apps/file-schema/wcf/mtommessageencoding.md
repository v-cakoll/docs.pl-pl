---
title: '&lt;mtomMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc7db79f25e2ab202f79f7f4ab5cc2a0e5eb0242
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltmtommessageencodinggt"></a>&lt;mtomMessageEncoding&gt;
Określa kodowanie i wersjonowanie wiadomości używanych dla wiadomości protokołu SOAP wiadomości transmisji optymalizacji mechanizmu (MTOM) na podstawie.  
  
 \<system.serviceModel >  
\<powiązania >  
\<customBinding >  
\<Powiązanie >  
\<mtomMessageEncoding >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<mtomMessageEncoding   
   maxBufferSize="Integer"  
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing1/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|wartość maxBufferSize|Liczba całkowita określająca maksymalny rozmiar buforu, który może być używany.|  
|MaxReadPoolSize|Liczba całkowita określająca ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników. Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy. Wartość domyślna to 64.|  
|MaxWritePoolSize|Liczba całkowita określająca ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących. Większe rozmiary puli powoduje, że system bardziej odporne na działanie nagłego kosztem większy zestaw roboczy. Wartość domyślna to 16.|  
|Element MessageVersion|Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania. Prawidłowe wartości to<br /><br /> -Soap11Addressing1<br />-Soap12Addressing10<br /><br /> Wartość domyślna to Soap12Addressing10. Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków. Prawidłowe wartości to<br /><br /> -UnicodeFffeTextEncoding: Kodowanie Unicode BigEndian<br />-Utf16TextEncoding: Kodowanie Unicode<br />-Utf8TextEncoding: 8-bitowego kodowania o<br /><br /> Wartość domyślna to Utf8TextEncoding. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Kodowanie jest procesem przekształcania komunikat do sekwencji bajtów. Dekodowanie jest procesu. Windows Communication Foundation (WCF) obejmuje trzy rodzaje kodowania protokołu SOAP wiadomości: tekst, dane binarne i mechanizmu optymalizacji transmisji wiadomości (MTOM).  
  
 `MtomMessageEncoding` Element określa znak kodowanie i wersjonowanie wiadomości i inne ustawienia używane do wiadomości przy użyciu kodowania mechanizmu optymalizacji transmisji wiadomości (MTOM). MTOM jest technologią wydajne przekazywania danych binarnych w wiadomości WCF. Koder MTOM podejmuje próbę utworzenia równowagi między wydajności i współdziałanie. Kodowanie MTOM przesyła większości XML w postaci tekstowej, ale optymalizuje dużych bloków danych binarnych, przekazując je jako — jest bez użycia konwersji do formatu ich kodowany w standardzie base64.  
  
## <a name="example"></a>Przykład  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap11Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
 [Kodowanie komunikatu](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Wybieranie kodera komunikatów](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
