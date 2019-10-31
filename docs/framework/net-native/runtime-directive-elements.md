---
title: Elementy dyrektyw środowiska uruchomieniowego
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128167"
---
# <a name="runtime-directive-elements"></a>Elementy dyrektyw środowiska uruchomieniowego
Format pliku dyrektyw środowiska uruchomieniowego (RD. xml) obsługuje następujące elementy dyrektywy środowiska uruchomieniowego. Zobacz sekcję [dyrektywy środowiska uruchomieniowego informacje o pliku konfiguracyjnym](runtime-directives-rd-xml-configuration-file-reference.md) dla reprezentacji hierarchicznej.  
  
 [\<> aplikacji](application-element-net-native.md)  
 Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów używanych przez aplikację i służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania. Jest to element podrzędny [> dyrektywy\<](directives-element-net-native.md) .  
  
 [\<zestawu >](assembly-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do wszystkich typów w zestawie. Jest to element podrzędny [\<> aplikacji](application-element-net-native.md) i [biblioteki\<](library-element-net-native.md) elementów.  
  
 [\<AttributeImplies >](attributeimplies-element-net-native.md)  
 Jeśli > dyrektywy zawierającej [typ\<](type-element-net-native.md) jest atrybut, stosuje zasady środowiska uruchomieniowego do elementów kodu, do których ten atrybut jest stosowany.  
  
 [Dyrektywy \<](directives-element-net-native.md)  
 Element główny w każdym pliku dyrektywy środowiska uruchomieniowego dla .NET Native. Jego elementy podrzędne są [\<> aplikacji](application-element-net-native.md) i [biblioteki\<](library-element-net-native.md).  
  
 [> zdarzeń \<](event-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do zdarzenia. Jest to element podrzędny [typu\<](type-element-net-native.md) i [\<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.  
  
 [\<pole >](field-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do pola. Jest to element podrzędny [typu\<](type-element-net-native.md) i [\<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.  
  
 [\<GenericParameter >](genericparameter-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu parametru typu ogólnego lub metody.  
  
 [\<ImpliesType >](impliestype-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu, jeśli te zasady zostały zastosowane do zawierającego go typu lub metody.  
  
 [Biblioteka \<](library-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do wszystkich typów w zestawie. Jest to element podrzędny [\<> aplikacji](application-element-net-native.md) i [biblioteki\<](library-element-net-native.md) elementów.  
  
 [> metody\<](method-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do metody. Jest to element podrzędny [typu\<](type-element-net-native.md) i [\<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.  
  
 [\<MethodInstantiation >](methodinstantiation-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do skonstruowanej metody ogólnej. Jest to element podrzędny [typu\<](type-element-net-native.md) i [\<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.  
  
 [\<przestrzeni nazw >](namespace-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do wszystkich typów w przestrzeni nazw.  
  
 [\<parametr >](parameter-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu argumentu przesłanego do metody.  
  
 [\<Właściwość >](property-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do właściwości. Jest to element podrzędny [typu\<](type-element-net-native.md) i [\<TypeInstantiation >](typeinstantiation-element-net-native.md) elementów.  
  
 [podtypy \<](subtypes-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do wszystkich klas dziedziczonych z typu zawierającego.  
  
 [Typ\<](type-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu.  
  
 [\<TypeInstantiation >](typeinstantiation-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do skonstruowanego typu ogólnego.  
  
 [\<TypeParameter >](typeparameter-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu reprezentowanego przez argument <xref:System.Type> przekazaną do metody.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji usług Rd. XML](runtime-directives-rd-xml-configuration-file-reference.md)
