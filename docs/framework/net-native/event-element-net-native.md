---
title: <Event>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 60da48d5872d7ce61afcffa7977411bc6e1efc7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181037"
---
# <a name="event-element-net-native"></a>\<Element> zdarzenia (.NET Native)
Stosuje zasady odbicia środowiska uruchomieniowego do zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Typ atrybutu|Opis|  
|---------------|--------------------|-----------------|  
|`Name`|Ogólne|Atrybut wymagany. Określa nazwę zdarzenia.|  
|`Browse`|Odbicie|Atrybut opcjonalny. Steruje wykonywaniem zapytań o informacje o zdarzeniu lub wyliczaniu, ale nie włącza dostępu dynamicznego w czasie wykonywania.|  
|`Dynamic`|Odbicie|Atrybut opcjonalny. Steruje dostępem środowiska wykonawczego do zdarzenia, aby włączyć programowanie dynamiczne. Ta zasada gwarantuje, że zdarzenie może być obsługiwane dynamicznie w czasie wykonywania.|  
  
## <a name="name-attribute"></a>Atrybut Nazwa  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*method_name*|Nazwa zdarzenia. Typ zdarzenia jest zdefiniowany przez [ \<](type-element-net-native.md) element nadrzędny Type>lub [ \<TypeInstantiation>](typeinstantiation-element-net-native.md) element.|  
  
## <a name="all-other-attributes"></a>Wszystkie inne atrybuty  
  
|Wartość|Opis|  
|-----------|-----------------|  
|*policy_setting*|Ustawienie, które ma zastosowanie do tego typu zasad dla zdarzenia. Możliwe wartości `Auto` `Excluded`to `Included`, `Required`, i . Aby uzyskać więcej informacji, zobacz [Ustawienia zasad dyrektywy środowiska wykonawczego](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Typ>](type-element-net-native.md)|Stosuje zasady odbicia do typu i wszystkich jego członków.|  
|[\<>typu>](typeinstantiation-element-net-native.md)|Stosuje zasady odbicia do skonstruowanego typu ogólnego i wszystkich jego elementów członkowskich.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zasady zdarzenia nie jest jawnie zdefiniowane, dziedziczy zasady środowiska wykonawczego jego elementu nadrzędnego.  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
- [Ustawienia zasad dyrektyw środowiska uruchomieniowego](runtime-directive-policy-settings.md)
