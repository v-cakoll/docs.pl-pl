---
title: '&lt;NetFx40_LegacySecurityPolicy&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d9312d25842ccfcdf84e678d34b9bfde3fe7dd0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltnetfx40legacysecuritypolicygt-element"></a>&lt;NetFx40_LegacySecurityPolicy&gt; — Element
Określa, czy środowisko uruchomieniowe używa zasady zabezpieczeń (CAS) starszego kodu dostępu.  
  
 \<Konfiguracja >  
\<runtime>  
< NetFx40_LegacySecurityPolicy >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe używa starszej wersji zasad CAS.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Środowisko uruchomieniowe nie używa starszej wersji zasad CAS. Domyślnie włączone.|  
|`true`|Środowisko uruchomieniowe używa starszej wersji zasad CAS.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
 W wersji .NET Framework 3.5 i wcześniejszymi wersjami urzędy certyfikacji zasad jest zawsze w obiekcie. W [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], należy włączyć zasady CAS.  
  
 Urzędy certyfikacji zasad jest określonej wersji. Zasady niestandardowe urzędy certyfikacji znajdujące się we wcześniejszych wersjach programu .NET Framework musi obowiązywać w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 Stosowanie `<NetFx40_LegacySecurityPolicy>` elementu [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] zestaw nie ma wpływu na [kod o przezroczystym poziomie bezpieczeństwa](../../../../../docs/framework/misc/security-transparent-code.md); nadal stosować zasady przezroczystość.  
  
> [!IMPORTANT]
>  Stosowanie `<NetFx40_LegacySecurityPolicy>` elementu może spowodować spadku wydajności istotne dla zestawów obrazu macierzystego utworzonych przez [Generator obrazu natywnego (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) nie są zainstalowane w [Globalna pamięć podręczna zestawów ](../../../../../docs/framework/app-domains/gac.md). Spadek wydajności jest spowodowany brakiem środowiska uruchomieniowego można załadować zestawów jako obrazów natywnych, gdy jest stosowany atrybut, co powoduje ich załadowanych zespołów jako just-in-time.  
  
> [!NOTE]
>  Jeśli określisz docelową wersję .NET Framework, która jest starsza niż [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] w ustawieniach projektu dla projektu programu Visual Studio, zasad CAS zostanie włączona, łącznie z urzędami certyfikacji zasad niestandardowych określony dla tej wersji. Jednak nie będzie mógł używać nowego [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] typy i składniki. Można także określić przy użyciu wcześniejszej wersji programu .NET Framework [ \<supportedRuntime > element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) w schemat ustawień uruchamiania w Twojej [pliku konfiguracji aplikacji](../../../../../docs/framework/configure-apps/index.md).  
  
> [!NOTE]
>  Składnia pliku konfiguracji jest rozróżniana wielkość liter. Należy użyć składni, co zostało opisane w sekcji składnię i przykład.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób Włącz starszą zasadę dla aplikacji.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
