---
title: Elementy dyrektyw środowiska uruchomieniowego
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
ms.openlocfilehash: c900516382c8e526a6b0021bb2b681486283f3ab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128167"
---
# <a name="runtime-directive-elements"></a>Elementy dyrektyw środowiska uruchomieniowego
Format pliku dyrektyw środowiska uruchomieniowego (RD. xml) obsługuje następujące elementy dyrektywy środowiska uruchomieniowego. Zobacz sekcję [dyrektywy środowiska uruchomieniowego informacje o pliku konfiguracyjnym](runtime-directives-rd-xml-configuration-file-reference.md) dla reprezentacji hierarchicznej.  
  
 [\<Application>](application-element-net-native.md)  
 Stosuje zasady odbicia środowiska uruchomieniowego do wszystkich typów używanych przez aplikację i służy jako kontener dla typów i składowych dla całej aplikacji, których metadane są dostępne do odbicia w czasie wykonywania. Jest to element podrzędny [\<Directives>](directives-element-net-native.md) elementu.  
  
 [\<Assembly>](assembly-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do wszystkich typów w zestawie. Jest to element podrzędny [\<Application>](application-element-net-native.md) [\<Library>](library-element-net-native.md) elementów i.  
  
 [\<AttributeImplies>](attributeimplies-element-net-native.md)  
 Jeśli jego dyrektywa zawierająca [\<Type>](type-element-net-native.md) jest atrybutem, stosuje zasady środowiska uruchomieniowego do elementów kodu, do których ten atrybut jest stosowany.  
  
 [\<Directives>](directives-element-net-native.md)  
 Element główny w każdym pliku dyrektywy środowiska uruchomieniowego dla .NET Native. Jego elementy podrzędne są [\<Application>](application-element-net-native.md) i [\<Library>](library-element-net-native.md) .  
  
 [\<Event>](event-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do zdarzenia. Jest to element podrzędny [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elementów i.  
  
 [\<Field>](field-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do pola. Jest to element podrzędny [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elementów i.  
  
 [\<GenericParameter>](genericparameter-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu parametru typu ogólnego lub metody.  
  
 [\<ImpliesType>](impliestype-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu, jeśli te zasady zostały zastosowane do zawierającego go typu lub metody.  
  
 [\<Library>](library-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do wszystkich typów w zestawie. Jest to element podrzędny [\<Application>](application-element-net-native.md) [\<Library>](library-element-net-native.md) elementów i.  
  
 [\<Method>](method-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do metody. Jest to element podrzędny [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elementów i.  
  
 [\<MethodInstantiation>](methodinstantiation-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do skonstruowanej metody ogólnej. Jest to element podrzędny [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elementów i.  
  
 [\<Namespace>](namespace-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do wszystkich typów w przestrzeni nazw.  
  
 [\<Parameter>](parameter-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu argumentu przesłanego do metody.  
  
 [\<Property>](property-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do właściwości. Jest to element podrzędny [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) elementów i.  
  
 [\<Subtypes>](subtypes-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do wszystkich klas dziedziczonych z typu zawierającego.  
  
 [\<Type>](type-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu.  
  
 [\<TypeInstantiation>](typeinstantiation-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do skonstruowanego typu ogólnego.  
  
 [\<TypeParameter>](typeparameter-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu reprezentowanego przez <xref:System.Type> argument przesłany do metody.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji usług Rd. XML](runtime-directives-rd-xml-configuration-file-reference.md)
