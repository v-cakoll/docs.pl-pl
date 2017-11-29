---
title: "&lt;Usesmallinternalthreadstacks —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2558423b412333a4d6ac9f650ad8ff3dab449d74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a>&lt;Usesmallinternalthreadstacks —&gt; — Element
Użyj żądania, że środowisko uruchomieniowe języka wspólnego (CLR) Zmniejsz pamięci, określając rozmiary jawne stosu podczas tworzenia niektórych wątków, które jest używana wewnętrznie, zamiast domyślny rozmiar stosu dla tych wątków.  
  
 \<Konfiguracja > — Element  
\<środowisko uruchomieniowe > — Element  
\<Usesmallinternalthreadstacks — > — Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|włączone|Atrybut wymagany.<br /><br /> Określa, czy żądanie rozmiary CLR Użyj jawnego stosu zamiast domyślny rozmiar stosu podczas tworzenia niektórych wątków, które jest używana wewnętrznie. Rozmiar stosu jawne są mniejsze niż domyślny rozmiar stosu 1 MB.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|true|Żądanie rozmiary jawne stosu.|  
|false|Użyj domyślnego rozmiaru stosu. Jest to wartość domyślna dla [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji jest używane do żądania użyj ograniczoną ilość pamięci wirtualnej w ramach procesu, ponieważ rozmiary jawne wątku, używane przez środowisko CLR do wewnętrznego wątków, jeśli żądanie jest honorowane, są mniejsze niż domyślny rozmiar.  
  
> [!IMPORTANT]
>  Ten element konfiguracji jest to żądanie do środowiska CLR, zamiast być bezwzględnie spełniony. W [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], żądanie jest honorowane tylko w przypadku x86 architektury. Ten element może być całkowicie ignorowane w przyszłych wersjach środowiska CLR lub zastępuje rozmiary jawne stosu, które są zawsze używane dla wybranych wątków wewnętrzny.  
  
 Określanie, czy ten element konfiguracji zamienia niezawodności mniejsze zużycie pamięci wirtualnej Jeśli środowisko CLR będzie honorować żądania, ponieważ stos mniejszych może sprawić stosu najprawdopodobniej przepełnienie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak żądania CLR stosu jawne użyj rozmiarów niektórych wątków, które jest używana wewnętrznie.  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
