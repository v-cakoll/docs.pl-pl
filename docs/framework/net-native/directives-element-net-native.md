---
title: <Directives> (Architektura .NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cfc9dc5c8122f9b1b1696cedcd5d9a8ceead403
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100226"
---
# <a name="directives-element-net-native"></a>\<Dyrektywy > (architektura .NET Native)
Element główny w każdym pliku dyrektyw środowiska uruchomieniowego dla platformy .NET Native.  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a>Składnia  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`xmlns`|Przestrzeń nazw XML. Jego wartość jest zawsze **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.|  
  
## <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Aplikacji >](../../../docs/framework/net-native/application-element-net-native.md)|Służy jako kontener dla całej aplikacji, typy i składowe typu, w których metadane są dostępne w celu odbicia.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Definiuje zestaw, w których typy podrzędne i elementy członkowskie typu wymagają metadanych w czasie wykonywania.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy plik dyrektywy środowiska uruchomieniowego może zawierać tylko jeden `<Directives>` elementu.  
  
 `<Directives>` Element może zawierać zero lub jeden [ \<aplikacji >](../../../docs/framework/net-native/application-element-net-native.md) elementu, a wartość zero, co najmniej jeden [ \<biblioteki >](../../../docs/framework/net-native/library-element-net-native.md) elementów.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](../../../docs/framework/net-native/runtime-directive-elements.md)
