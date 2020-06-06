---
title: <etwEnable> Element
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 14cea171a4a25e148ea32f75a8ef09b83a4ec8ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117398"
---
# <a name="etwenable-element"></a>\<etwEnable> Element
Określa, czy włączyć śledzenie zdarzeń systemu Windows (ETW) dla zdarzeń środowiska uruchomieniowego języka wspólnego.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|enabled|Atrybut wymagany.<br /><br /> Określa, czy funkcja ETW powinna być włączona.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|true|Włącz funkcję ETW. Jest to wartość domyślna dla wersji systemu Windows, począwszy od systemów operacyjnych Windows Vista i Windows Server 2008.|  
|fałsz|Wyłącz funkcję ETW. Jest to wartość domyślna dla wcześniejszych wersji systemu Windows.|  
  
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
