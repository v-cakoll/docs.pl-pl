---
title: Elementy dyrektyw środowiska uruchomieniowego
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b4e8f0902e0d3ebd010ff639b329707881c29fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398017"
---
# <a name="runtime-directive-elements"></a>Elementy dyrektyw środowiska uruchomieniowego
Format pliku dyrektyw (rd.xml) środowiska uruchomieniowego obsługuje następujące elementy dyrektyw środowiska uruchomieniowego. Zobacz [dyrektyw środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) reprezentacji hierarchicznej.  
  
 [\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)  
 Zastosowanie zasad wykonywania odbicia do wszystkich typów, używany przez aplikację i służy jako kontener dla całej aplikacji typy i elementy członkowskie typu, w których metadane są dostępne w celu odbicia w czasie wykonywania. To jest elementem podrzędnym [ \<dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md) elementu.  
  
 [\<zestaw >](../../../docs/framework/net-native/assembly-element-net-native.md)  
 Stosuje runnntime zasady do wszystkich typów w zestawie. To jest elementem podrzędnym [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) i [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementów.  
  
 [\<AttributeImplies >](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 Jeśli jego zawierający [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) dyrektywa jest atrybutu, elementy kodu, do których zastosowano ten atrybut ma zastosowanie zasad wykonywania.  
  
 [\<Dyrektywy >](../../../docs/framework/net-native/directives-element-net-native.md)  
 W każdym pliku dyrektyw środowiska uruchomieniowego dla elementu głównego [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Jego elementy podrzędne są [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) i [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md).  
  
 [\<Zdarzenie >](../../../docs/framework/net-native/event-element-net-native.md)  
 Zastosowanie zasad wykonywania na zdarzenie. To jest elementem podrzędnym [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.  
  
 [\<Pole >](../../../docs/framework/net-native/field-element-net-native.md)  
 Zastosowanie zasad wykonywania do pola. To jest elementem podrzędnym [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.  
  
 [\<GenericParameter >](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 Zastosowanie zasad wykonywania na typ parametru typu ogólnego lub metody.  
  
 [\<ImpliesType >](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 W przypadku zasad wykonywania na typ, że zasady zostały zastosowane do typu zawierającego lub metody.  
  
 [\<Biblioteka >](../../../docs/framework/net-native/library-element-net-native.md)  
 Dotyczy wszystkich typów w zestawie zasad wykonywania. To jest elementem podrzędnym [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) i [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementów.  
  
 [\<Metoda >](../../../docs/framework/net-native/method-element-net-native.md)  
 Zastosowanie zasad wykonywania do metody. To jest elementem podrzędnym [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.  
  
 [\<MethodInstantiation >](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do skonstruowanego metody rodzajowej. To jest elementem podrzędnym [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.  
  
 [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 Zastosowanie zasad wykonywania dla wszystkich typów w przestrzeni nazw.  
  
 [\<Parametr >](../../../docs/framework/net-native/parameter-element-net-native.md)  
 Zastosowanie zasad wykonywania na typ argumentu przekazanego do metody.  
  
 [\<Właściwość >](../../../docs/framework/net-native/property-element-net-native.md)  
 Zastosowanie zasad wykonywania na właściwość. To jest elementem podrzędnym [ \<typu >](../../../docs/framework/net-native/type-element-net-native.md) i [ \<TypeInstantiation >](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) elementów.  
  
 [\<Subtypes >](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 Zastosowanie zasad wykonywania dla wszystkich klas dziedziczony z typu zawierającego.  
  
 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md)  
 Zastosowanie zasad wykonywania do typu.  
  
 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 Stosuje zasady środowiska uruchomieniowego do skonstruowanego typu ogólnego.  
  
 [\<TypeParameter >](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 Zastosowanie zasad wykonywania na typ reprezentowany przez <xref:System.Type> argument przekazany do metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja pliku RD.XML konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
