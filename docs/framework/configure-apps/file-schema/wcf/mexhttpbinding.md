---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8d5b9378bf7769754586d0b13f742659aee18f03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430910"
---
# <a name="mexhttpbinding"></a>\<mexHttpBinding >
Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTP.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpBinding >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`closeTimeout`|Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`name`|Ciąg zawierający nazwę konfiguracji powiązania. Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania. Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji otwierania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|`receiveTimeout`|Wartość <xref:System.TimeSpan>, która określa przedział czasu podanego na zakończenie operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:10:00.|  
|`sendTimeout`|Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[> powiązań \<](bindings.md)|Ten element zawiera kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 To powiązanie jest zasadniczo `WSHttpBinding` powiązań z wyłączonymi zabezpieczeniami. Obsługuje większość żądań metadanych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [Metadane](../../../wcf/feature-details/metadata.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [> powiązań \<](bindings.md)
