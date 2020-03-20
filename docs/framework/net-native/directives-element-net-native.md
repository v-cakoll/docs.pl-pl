---
title: <Directives>Element (natywny.NET)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 49c1aaf005b80a6c1c1fa382eebc2cb0dbfa4be7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181044"
---
# <a name="directives-element-net-native"></a>\<Dyrektywy> element (.NET native)
Element główny w każdym pliku dyrektyw środowiska wykonawczego dla platformy .NET Native.  
  
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
|`xmlns`|Obszar nazw XML. Jego wartość jest zawsze **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.|  
  
## <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>aplikacji](application-element-net-native.md)|Służy jako kontener dla typów całej aplikacji i członków typu, których metadane są dostępne do odbicia.|  
|[\<>biblioteczna](library-element-net-native.md)|Definiuje zestaw, którego typy podrzędne i elementy członkowskie typu wymagają metadanych w czasie wykonywania.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy plik dyrektyw środowiska wykonawczego `<Directives>` może zawierać tylko jeden element.  
  
 Element `<Directives>` może zawierać zero [ \<](application-element-net-native.md) lub jeden element>aplikacji i zero, jeden lub więcej [ \<elementów>biblioteki.](library-element-net-native.md)  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementy dyrektyw środowiska uruchomieniowego](runtime-directive-elements.md)
