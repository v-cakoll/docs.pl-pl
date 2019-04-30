---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: bff19f106d86c73dea80b8b57bb73442eaa2cf9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704040"
---
# <a name="filter"></a>\<Filtr >

Określa filtr routingu, który określa typ programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również obsługujących danych lub parametrów wymaganych przez filtr.

\<system.serviceModel> \<routing> \<filters> \<filter>
  
## <a name="syntax"></a>Składnia  
  
```xml  
<routing>
  <filters>
    <filter customType="String"
            filterData="String"
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath"
            name="String" />
  </filters>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

| Atrybut  | Opis |
| ---------- | ----------- |
| customType | Ciąg zawierający w pełni kwalifikowana nazwa typu niestandardowego typu ma być używany jako filtr. Jeśli `filterType` ustawiono `custom`, ten atrybut zawiera w pełni kwalifikowana nazwa typu klasy, aby utworzyć.  `filterData` może również zawierać wartości, które mają być używane podczas obliczania wartości filtru typu niestandardowego. |
| filterData | Ciąg zawierający dane filtru. Aby uzyskać więcej informacji na temat sposobu określania tego atrybutu, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| filterType | Ciąg zawierający typ filtru. Ten atrybut jest <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.  Aby uzyskać więcej informacji na temat działania z `filterData` atrybutów, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| nazwa       | Ciąg zawierający unikatową nazwę tego elementu filtru. |

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| ------- | ----------- |
| [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu programu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących. |

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
