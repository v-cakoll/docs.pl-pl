---
title: '&lt;generatePublisherEvidence&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f56bbef6ed6decf6be4246f649665db4cf0f766
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltgeneratepublisherevidencegt-element"></a>&lt;generatePublisherEvidence&gt; — Element
Określa, czy środowisko uruchomieniowe utworzy <xref:System.Security.Policy.Publisher> dowodów zabezpieczeń dostępu kodu (CAS).  
  
 \<Konfiguracja >  
\<runtime>  
\<generatePublisherEvidence >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe utworzy <xref:System.Security.Policy.Publisher> dowód.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie tworzy <xref:System.Security.Policy.Publisher> dowód.|  
|`true`|Tworzy <xref:System.Security.Policy.Publisher> dowód. Domyślnie włączone.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  W [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] i później, ten element nie ma wpływu na czas ładowania zestawu. Aby uzyskać więcej informacji, zobacz sekcję "Uproszczenia zasad zabezpieczeń" w [zmiany zabezpieczeń](../../../../../docs/framework/security/security-changes.md).  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) próbuje zweryfikować podpisu Authenticode w czasie ładowania, aby utworzyć <xref:System.Security.Policy.Publisher> dowody dla zestawu. Domyślnie większość aplikacji muszą jednak <xref:System.Security.Policy.Publisher> dowód. Standardowe zasady CAS nie bazuje na <xref:System.Security.Policy.PublisherMembershipCondition>. Należy unikać koszt uruchamiania niepotrzebnych związany z weryfikowanie podpisu wydawcy, chyba że aplikacja wykonuje na komputerze z niestandardowych zasad CAS lub mają zostać do zaspokojenia potrzeb <xref:System.Security.Permissions.PublisherIdentityPermission> w środowisku z częściowym zaufaniem. (Wymagania dotyczące uprawnień tożsamości zawsze powiedzie się w pełni zaufanym środowisku).  
  
> [!NOTE]
>  Zaleca się, że usługi użyj `<generatePublisherEvidence>` elementu, aby poprawić wydajność uruchamiania.  Za pomocą tego elementu może również pomóc uniknąć opóźnienia, które mogą spowodować limit czasu i anulowania uruchomienia usługi.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `<generatePublisherEvidence>` element, aby wyłączyć sprawdzanie urzędów certyfikacji zasad wydawcy aplikacji.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
