---
title: '&lt;enforcefipspolicy —&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9040bf2548964cf6df5f4fd87ee9f6d979c7df1e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746218"
---
# <a name="ltenforcefipspolicygt-element"></a>&lt;enforcefipspolicy —&gt; — Element
Określa, czy można wymusić wymagania konfiguracji komputera, że algorytmy kryptograficzne musi być zgodne z przetwarzania standardami FIPS (Federal Information).  
  
 \<Konfiguracja > — Element  
\<środowisko uruchomieniowe > — Element  
\<enforcefipspolicy — > — Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|włączone|Atrybut wymagany.<br /><br /> Określa, czy włączyć wymuszania wymaganie konfiguracji komputera, że algorytmy kryptograficzne muszą być zgodne z trybem FIPS.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`true`|Gdy komputer jest skonfigurowany do żądania algorytmów kryptograficznych za zgodny ze standardem FIPS, ten wymóg jest wymuszana. Jeśli klasa implementuje algorytmu, który nie jest zgodna z trybem FIPS, konstruktorów lub `Create` metody tej klasy zgłaszają wyjątki, gdy są uruchamiane na tym komputerze. Domyślnie włączone.|  
|`false`|Algorytmy kryptograficzne, które są używane przez aplikację nie są wymagane, aby było zgodne z trybem FIPS, niezależnie od konfiguracji komputera.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od programu .NET Framework 2.0, tworzenie klas implementujących algorytmów kryptograficznych jest kontrolowana przez konfiguracji komputera. Jeśli komputer jest skonfigurowany do żądania algorytmów, aby było zgodne z trybem FIPS, a klasa implementuje algorytmu, który nie jest zgodna z trybem FIPS, wszelkie próby utworzenia wystąpienia tej klasy zgłasza wyjątek. Konstruktory throw <xref:System.InvalidOperationException> wyjątek, i `Create` metod generują <xref:System.Reflection.TargetInvocationException> wyjątek z wewnętrznego <xref:System.InvalidOperationException> wyjątku.  
  
 W przypadku aplikacja działa na komputerach, na których konfiguracje wymagają zgodności z trybem FIPS, a aplikacja używa algorytmu, który nie jest zgodna z trybem FIPS, można użyć tego elementu w pliku konfiguracji, aby zapobiec środowisko uruchomieniowe języka wspólnego (CLR) z Wymuszanie zgodności ze standardem FIPS. Ten element został wprowadzony w [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zapobiec CLR Wymuszanie zgodności ze standardem FIPS.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Model kryptografii](../../../../../docs/standard/security/cryptography-model.md)
