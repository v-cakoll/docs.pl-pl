---
title: '&lt;filters&gt; w &lt;routing&gt;'
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 9f0fa9bf51d264346738172f57a8efca7950fdb7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753118"
---
# <a name="ltfiltersgt-of-ltroutinggt"></a>&lt;filters&gt; w &lt;routing&gt;

Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących.

[**\<system.serviceModel >**](system-servicemodel.md)   
&nbsp;&nbsp;[**\<Routing >**](routing.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Filtry >**

## <a name="syntax"></a>Składnia

```xml
<system.serviceModel>
  <routing>
    <filters>
      <filter customType="String" 
              filterData="String" 
              filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
              name="String" />
    </filters>
  </routing>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

Brak

### <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [**\<Filtr >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | Zawiera filtr routingu, która określa typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> będą używane podczas oceniania wiadomości przychodzących. |

### <a name="parent-elements"></a>Elementy nadrzędne

|     | Opis |
| --- | ----------- |
| [**\<Routing >**](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu tabel docelowych punktów końcowych, aby zdefiniować wysyłanie komunikatów do gdy kryteria filtru. |

## <a name="see-also"></a>Zobacz także

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
