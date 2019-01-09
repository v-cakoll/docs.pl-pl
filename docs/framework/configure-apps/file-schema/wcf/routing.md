---
title: '&lt;Routing&gt;'
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: 220c18ab8ea6222fcf7d9fb8a93950281c9de796
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145149"
---
# <a name="ltroutinggt"></a>&lt;Routing&gt;

Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu definiujące miejsce docelowe punktów końcowych do tabel wysyłanie komunikatów do gdy kryteria filtru.

[**\<system.serviceModel >**](system-servicemodel.md)   
&nbsp;&nbsp;**\<Routing >**
  
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
    <routingTables>
      <table name="String">
        <entries>
          <add endpoint="String"
               filterName="String"
               priority="Integer" />
        </entries>
      </table>
    </routingTables>
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
| [**\<Filtry >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md) | Zawiera zestaw filtrów routingu, które określają typ MessageFilter Windows Communication Foundation (WCF), będzie ono używane podczas oceniania wiadomości przychodzących. |
| [**\<filterTables >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) | Zawiera mapowania między filtrami i docelowymi punktami końcowymi, aby określić, który punkt końcowy do użycia podczas filtr dopasowuje wartość. |

### <a name="parent-elements"></a>Elementy nadrzędne

|     | Opis |
| --- | ----------- |
| **\<System. ServiceModel >** | Element główny wszystkich elementów konfiguracji programu WCF. |

## <a name="see-also"></a>Zobacz także

<xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
