---
title: <etwEnable>, element
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb4d0ed5b33170c40aacb32bebbf1b59ca659be4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252617"
---
# <a name="etwenable-element"></a>\<etwEnable, element >
Określa, czy włączyć śledzenie zdarzeń systemu Windows (ETW) dla zdarzeń środowiska uruchomieniowego języka wspólnego.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<etwEnabled >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|dostępny|Atrybut wymagany.<br /><br /> Określa, czy funkcja ETW powinna być włączona.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|true|Włącz funkcję ETW. Jest to wartość domyślna dla wersji systemu Windows, począwszy od systemów operacyjnych Windows Vista i Windows Server 2008.|  
|false|Wyłącz funkcję ETW. Jest to wartość domyślna dla wcześniejszych wersji systemu Windows.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od systemu Windows Vista, funkcja ETW jest domyślnie włączona. Użyj tego elementu, aby wyłączyć funkcję ETW dla aplikacji. We wcześniejszych wersjach systemu Windows Użyj tego elementu, aby włączyć funkcję ETW dla aplikacji.  
  
> [!NOTE]
> Funkcję ETW można włączyć lub wyłączyć globalnie na serwerze przy użyciu ustawienia rejestru. Zobacz [kontrolowanie rejestrowania .NET Framework](../../../performance/controlling-logging.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak włączyć śledzenie ETW dla aplikacji.  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Kontrolowanie logowania w programie .NET Framework](../../../performance/controlling-logging.md)
