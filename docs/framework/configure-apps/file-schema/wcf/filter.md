---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855255"
---
# \<filter>

Definiuje filtr routingu, który określa typ Windows Communication Foundation (WCF), który <xref:System.ServiceModel.Dispatcher.MessageFilter> ma być używany podczas oceniania wiadomości przychodzących, a także wszelkie dane pomocnicze lub parametry wymagane przez filtr.

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
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
| CustomType | Ciąg zawierający w pełni kwalifikowaną nazwę typu typu niestandardowego, który ma być używany jako filtr. Jeśli `filterType` jest ustawiona na `custom` , ten atrybut zawiera w pełni kwalifikowaną nazwę typu klasy do utworzenia.  `filterData`może również zawierać wartości, które mają być używane podczas oceny niestandardowego filtru typów. |
| Danych filtru | Ciąg zawierający dane filtru. Aby uzyskać więcej informacji na temat sposobu określania tego atrybutu, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> . |
| filterType | Ciąg zawierający typ filtru. Ten atrybut jest <xref:System.ServiceModel.Routing.Configuration.FilterType> typu.  Aby uzyskać więcej informacji na temat tego, jak to działa z `filterData` atrybutem, zobacz <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> . |
| name       | Ciąg zawierający unikatową nazwę tego elementu filtru. |

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| ------- | ----------- |
| [\<routing>](routing.md) | Sekcja konfiguracji służąca do definiowania zestawu filtrów routingu, które określają typ Windows Communication Foundation (WCF), który <xref:System.ServiceModel.Dispatcher.MessageFilter> ma być używany podczas oceniania wiadomości przychodzących. |

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
