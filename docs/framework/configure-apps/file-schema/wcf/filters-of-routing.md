---
title: <filters> dla <routing>
ms.date: 03/30/2017
ms.assetid: 7993cf90-9afd-4c3c-9608-184d5da1105c
ms.openlocfilehash: 8b2c735a19c4cece16dcb77e3ec548eb2d39ec18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701037"
---
# <a name="filters-of-routing"></a>\<Filtry > z \<routingu >

Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących.

[**\<system.serviceModel>**](system-servicemodel.md)   
&nbsp;&nbsp;[**\<routing>**](routing.md)   
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
| [**\<filter>**](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | Zawiera filtr routingu, który określa typ programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> będą używane podczas oceniania wiadomości przychodzących. |

### <a name="parent-elements"></a>Elementy nadrzędne

|     | Opis |
| --- | ----------- |
| [**\<routing>**](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych do tabel wysyłanie komunikatów do gdy kryteria filtru. |

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
