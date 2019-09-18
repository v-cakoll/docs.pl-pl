---
title: Elementy dyrektyw środowiska uruchomieniowego
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 062f13ad92f37bb7ae29ed34dcf88f99f98e7612
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049274"
---
# <a name="runtime-directive-elements"></a>Elementy dyrektyw środowiska uruchomieniowego
Format pliku dyrektyw środowiska uruchomieniowego (RD. xml) obsługuje następujące elementy dyrektywy środowiska uruchomieniowego. Zobacz sekcję [dyrektywy środowiska uruchomieniowego informacje o pliku konfiguracyjnym](runtime-directives-rd-xml-configuration-file-reference.md) dla reprezentacji hierarchicznej.  
  
 [\<> Aplikacji](application-element-net-native.md)  
 Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów używanych przez aplikację i służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania. Jest to element podrzędny [ \<dyrektyw >](directives-element-net-native.md) elementu.  
  
 [\<> Zestawu](assembly-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do wszystkich typów w zestawie. Jest to element podrzędny [ \<> aplikacji](application-element-net-native.md) i [ \<biblioteki >](library-element-net-native.md) elementy.  
  
 [\<AttributeImplies >](attributeimplies-element-net-native.md)  
 Jeśli typ zawierający [ \<>](type-element-net-native.md) dyrektywie jest atrybut, stosuje zasady środowiska uruchomieniowego do elementów kodu, do których ten atrybut jest stosowany.  
  
 [\<Dyrektywy >](directives-element-net-native.md)  
 Element główny w każdym pliku dyrektywy środowiska uruchomieniowego dla .NET Native. Jego elementami podrzędnymi są [ \<> aplikacji](application-element-net-native.md) i [ \<> biblioteki](library-element-net-native.md).  
  
 [\<> Zdarzeń](event-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do zdarzenia. Jest to element podrzędny [ \<typu >](type-element-net-native.md) i [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.  
  
 [\<> Pola](field-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do pola. Jest to element podrzędny [ \<typu >](type-element-net-native.md) i [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.  
  
 [\<GenericParameter >](genericparameter-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu parametru typu ogólnego lub metody.  
  
 [\<ImpliesType >](impliestype-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu, jeśli te zasady zostały zastosowane do zawierającego go typu lub metody.  
  
 [\<> Biblioteki](library-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do wszystkich typów w zestawie. Jest to element podrzędny [ \<> aplikacji](application-element-net-native.md) i [ \<biblioteki >](library-element-net-native.md) elementy.  
  
 [\<> Metody](method-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do metody. Jest to element podrzędny [ \<typu >](type-element-net-native.md) i [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.  
  
 [\<MethodInstantiation >](methodinstantiation-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do skonstruowanej metody ogólnej. Jest to element podrzędny [ \<typu >](type-element-net-native.md) i [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.  
  
 [\<Namespace>](namespace-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do wszystkich typów w przestrzeni nazw.  
  
 [\<> Parametru](parameter-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu argumentu przesłanego do metody.  
  
 [\<> Właściwości](property-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do właściwości. Jest to element podrzędny [ \<typu >](type-element-net-native.md) i [ \<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.  
  
 [\<Podtypy >](subtypes-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do wszystkich klas dziedziczonych z typu zawierającego.  
  
 [\<Type>](type-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu.  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do skonstruowanego typu ogólnego.  
  
 [\<TypeParameter >](typeparameter-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu reprezentowanego <xref:System.Type> przez argument przesłany do metody.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji usług Rd. XML](runtime-directives-rd-xml-configuration-file-reference.md)
