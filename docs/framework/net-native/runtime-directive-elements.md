---
title: Elementy dyrektyw środowiska uruchomieniowego
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf692ff93a575858d1d1a89346611cb9c5957b3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137816"
---
# <a name="runtime-directive-elements"></a>Elementy dyrektyw środowiska uruchomieniowego
Format pliku (rd.xml) dyrektyw środowiska uruchomieniowego obsługuje następujące elementy dyrektyw środowiska uruchomieniowego. Zobacz [dyrektywy środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) dla hierarchiczną reprezentację.  
  
 [\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)  
 Zastosowanie zasad odbicia środowiska uruchomieniowego dla wszystkich typów używanych przez aplikację i służy jako kontener dla całej aplikacji, typów i elementów członkowskich typu, w których metadane są dostępne w celu odbicia w czasie wykonywania. To jest elementem podrzędnym [ \<dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md) elementu.  
  
 [\<Zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)  
 Dotyczy wszystkich typów w zestawie zasad wykonywania. To jest elementem podrzędnym [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) i [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementów.  
  
 [\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 Jeśli jego zawierający [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) dyrektywa jest atrybut, elementy kodu, do których zastosowano ten atrybut ma zastosowanie zasad wykonywania.  
  
 [\<Dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md)  
 Element główny w każdym pliku dyrektyw środowiska uruchomieniowego dla [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Jego elementy podrzędne są [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) i [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)  
 Zastosowanie zasad wykonywania na zdarzenie. To jest elementem podrzędnym [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.  
  
 [\<Field>](../../../docs/framework/net-native/field-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do pola. To jest elementem podrzędnym [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.  
  
 [\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 Stosuje zasady obsługi z typem parametru typu ogólnego lub metody.  
  
 [\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 W przypadku zasad środowiska uruchomieniowego do typu, że zasady zostały zastosowane do zawierający typ lub metoda.  
  
 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md)  
 Dotyczy wszystkich typów w zestawie zasad wykonywania. To jest elementem podrzędnym [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) i [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementów.  
  
 [\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)  
 Zastosowanie zasad wykonywania metody. To jest elementem podrzędnym [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.  
  
 [\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 Ma zastosowanie zasad środowiska uruchomieniowego do skonstruowanego metody rodzajowej. To jest elementem podrzędnym [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.  
  
 [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego dla wszystkich typów w przestrzeni nazw.  
  
 [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu argumentu przekazanego do metody.  
  
 [\<Property>](../../../docs/framework/net-native/property-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do właściwości. To jest elementem podrzędnym [ \<typ >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.  
  
 [\<Podtypy >](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego dla wszystkich klas dziedziczone z typu zawierającego.  
  
 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do typu.  
  
 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 Skonstruowany typ rodzajowy dotyczy zasad wykonywania.  
  
 [\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 Zastosowanie zasad wykonywania na typ reprezentowany przez <xref:System.Type> argument przekazywany do metody.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji RD.XML](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
