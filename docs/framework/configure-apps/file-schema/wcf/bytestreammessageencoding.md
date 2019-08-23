---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: b11f472c0e33003e50be4b45bb49196c64ecb70d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919731"
---
# <a name="bytestreammessageencoding"></a>\<byteStreamMessageEncoding>
Określa kodowanie komunikatu jako strumień bajtów z opcją określenia kodowania znaków.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<binaryMessageEncoding >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Element MessageVersion|Określa wersję SOAP komunikatów wysyłanych za pomocą powiązania. Dla tej właściwości można ustawić tylko wartość <xref:System.ServiceModel.Channels.MessageVersion.None%2A>wersji komunikatu. Koder komunikatów strumienia bajtów nie obsługuje żadnych innych wersji komunikatów.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [Kodowanie komunikatu](message-encoding.md)
- [Wybieranie kodera komunikatów](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
