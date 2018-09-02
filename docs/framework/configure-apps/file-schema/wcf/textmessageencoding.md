---
title: '&lt;textMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: e684c21c0b1360a9b270214ebe7b3ad00b42657f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417798"
---
# <a name="lttextmessageencodinggt"></a>&lt;textMessageEncoding&gt;
Określa kodowanie znaków i wiadomości versioning używany dla wiadomości tekstowych XML.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<textMessageEncoding >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing10/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|maxReadPoolSize|Liczba całkowita określająca ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników. Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy. Wartość domyślna to 64.|  
|maxWritePoolSize|Liczba całkowita określająca ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących. Większe rozmiary pul powoduje, że system bardziej odporne na skoki działania kosztem większy zestaw roboczy. Wartość domyślna to 16.|  
|Element messageVersion|Określa wersję SOAP komunikatów wysyłanych za pomocą tego powiązania. Prawidłowe wartości to:<br /><br /> -Soap11Addressing10<br />-Soap12Addressing10<br /><br /> Wartość domyślna to Soap12Addressing10. Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków. Prawidłowe wartości to:<br /><br /> -UnicodeFffeTextEncoding: Unicode BigEndian kodowanie<br />-Utf16TextEncoding: Kodowanie Unicode<br />-Utf8TextEncoding: 8-bitowego kodowania<br /><br /> Wartość domyślna to Utf8TextEncoding. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie funkcje powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Kodowanie jest procesem przekształcania wiadomość do sekwencji bajtów. Dekodowanie jest procesu. Windows Communication Foundation (WCF) zawiera trzy typy kodowania dla wiadomości SOAP: tekst, dane binarne i komunikat transmisji optymalizacji mechanizm (MTOM).  
  
 Kodowanie tekstu reprezentowany przez `textMessageEncoding` element jest najbardziej elementy mogły współdziałać, ale co najmniej wydajne kodera komunikatów XML.  Koder tekstu tworzy oparte na tekście wiadomości na łączu. Komunikaty generowane przez ten koder nadają się dla protokołu WS-* na podstawie międzyoperacyjności. Klient usługi sieci Web lub usługa sieci Web zazwyczaj może zrozumieć tekstowych XML. Jednak przesyłania dużych bloków danych binarnych jako tekst jest najmniej efektywną metodę kodowania wiadomości XML.  
  
## <a name="example"></a>Przykład  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap12Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 [Wybieranie kodera komunikatów](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Kodowanie komunikatu](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
