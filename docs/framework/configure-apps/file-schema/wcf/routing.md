---
title: <routing>
ms.date: 03/30/2017
ms.assetid: a210c209-3940-4288-9a8e-39b1e62606bc
ms.openlocfilehash: fcf2d4eec93fd7127c6f800e1c739ad1fac49203
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399971"
---
# \<routing>

Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu, które definiują docelowe punkty końcowe do wysyłania komunikatów, gdy filtr jest zgodny.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**
  
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
| [**\<filters>**](filters-of-routing.md) | Zawiera zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF), który będzie używany podczas oceniania wiadomości przychodzących. |
| [**\<filterTables>**](filtertables.md) | Zawiera mapowania między filtrami routingu i docelowymi punktami końcowymi, aby określić, który punkt końcowy ma być używany, gdy filtr jest zgodny. |

### <a name="parent-elements"></a>Elementy nadrzędne

|     | Opis |
| --- | ----------- |
| **\<system.ServiceModel>** | Element główny wszystkich elementów konfiguracji WCF. |

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
