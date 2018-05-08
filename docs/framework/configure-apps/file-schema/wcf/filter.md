---
title: '&lt;Filtr&gt;'
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 93d47fc6b25a75eedae43cd70582abc863a74e6c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltergt"></a>&lt;Filtr&gt;

Określa filtr routingu, który określa typ Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również obsługujących danych lub parametrów wymaganych przez filtr.

\<system.serviceModel > \<routingu > \<Filtry > \<filtru >

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
| customtype — | Ciąg zawierający nazwę FQDN typu niestandardowego typu ma być używany jako filtr. Jeśli `filterType` ma ustawioną wartość `custom`, ten atrybut zawiera typu w pełni kwalifikowaną nazwę klasy w celu utworzenia.  `filterData` może również zawierać wartości, które mają być użyte podczas obliczania filtru typu niestandardowego. |
| danych filtru | Ciąg zawierający dane filtru. Aby uzyskać więcej informacji dotyczących sposobu określania tego atrybutu, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| filterType | Ciąg zawierający typ filtru. Ten atrybut jest <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.  Aby uzyskać więcej informacji na temat sposobu wykonywania z `filterData` atrybutów, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>. |
| nazwa       | Ciąg zawierający unikatową nazwę tego elementu filtru. |

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| ------- | ----------- |
| [\<Routing >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ obiektu Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących. |

## <a name="see-also"></a>Zobacz także

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
