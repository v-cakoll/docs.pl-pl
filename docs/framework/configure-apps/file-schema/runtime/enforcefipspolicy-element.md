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
ms.openlocfilehash: 0bffe72a4bcadb4a36a9ac54263d55e242ffc4d4
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612013"
---
# <a name="ltenforcefipspolicygt-element"></a>&lt;enforcefipspolicy —&gt; — Element
Określa, czy do wymuszania wymagań konfiguracji komputera, że algorytmy kryptograficzne musi być zgodne z przetwarzania standardów FIPS (Federal Information).  
  
 \<Konfiguracja > Element  
\<środowisko uruchomieniowe > Element  
\<enforcefipspolicy — > Element  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Włączone|Atrybut wymagany.<br /><br /> Określa, czy włączyć wymuszanie wymagań konfiguracji komputera, że algorytmy kryptograficzne musi być zgodna z trybem FIPS.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`true`|Jeśli komputer jest skonfigurowany do wymagają algorytmów kryptograficznych jako zgodny ze standardem FIPS, wymóg ten jest wymuszany. Jeśli klasa implementuje algorytm, który nie jest zgodna z trybem FIPS, konstruktory lub `Create` metody tej klasy zgłaszają wyjątki, gdy są uruchamiane na tym komputerze. Domyślnie włączone.|  
|`false`|Algorytmy kryptograficzne, które są używane przez aplikację nie są wymagane do zapewnienia zgodności ze standardem FIPS, niezależnie od konfiguracji komputera.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od programu .NET Framework 2.0, tworzenie klas, które implementują algorytmy kryptograficzne, zależy od konfiguracji komputera. Jeśli komputer jest skonfigurowany do żądania algorytmów do zapewnienia zgodności ze standardem FIPS, a klasa implementuje algorytm, który nie jest zgodna z trybem FIPS, wszelkie próby utworzenia wystąpienia tej klasy zgłasza wyjątek. Konstruktory throw <xref:System.InvalidOperationException> wyjątek, i `Create` metod generują <xref:System.Reflection.TargetInvocationException> wyjątek z wewnętrznego <xref:System.InvalidOperationException> wyjątku.  
  
 Jeśli aplikacja działa na komputerach, na których konfiguracje wymagają zgodności z trybem FIPS, a Twoja aplikacja używa algorytmu, który nie jest zgodna z trybem FIPS, można użyć tego elementu w pliku konfiguracji aby zapobiec środowisko uruchomieniowe języka wspólnego (CLR) z Wymuszanie zgodności ze standardem FIPS. Ten element został wprowadzony w [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak uniemożliwić CLR Wymuszanie zgodności ze standardem FIPS.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [Model kryptografii](../../../../../docs/standard/security/cryptography-model.md)
