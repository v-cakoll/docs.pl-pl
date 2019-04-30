---
title: <generatePublisherEvidence>, element
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09a12f062b2fe3ad6e5ac90f0d268bbbeab44876
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674145"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> Element
Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowodów dla zabezpieczeń dostępu kodu (CAS).  
  
 \<Konfiguracja >  
\<runtime>  
\<generatePublisherEvidence>  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowodów.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie powoduje utworzenia <xref:System.Security.Policy.Publisher> dowodów.|  
|`true`|Tworzy <xref:System.Security.Policy.Publisher> dowodów. Domyślnie włączone.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  W [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] i nowszym, ten element nie ma wpływu na krótszy czas ładowania zestawu. Aby uzyskać więcej informacji, zobacz sekcję "Uproszczenia zasad zabezpieczeń" w [zmiany zabezpieczeń](../../../../../docs/framework/security/security-changes.md).  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) próbuje zweryfikować podpisu Authenticode w czasie ładowania, aby utworzyć <xref:System.Security.Policy.Publisher> dowodu dla zestawu. Jednak domyślnie większość aplikacji nie ma potrzeby <xref:System.Security.Policy.Publisher> dowodów. Standardowe zasady CAS nie zależą od <xref:System.Security.Policy.PublisherMembershipCondition>. Należy unikać koszt uruchamiania niepotrzebnych związany z weryfikacji podpisu wydawcy, chyba że aplikacja wykonuje na komputerze za pomocą zasad niestandardowych urzędów certyfikacji lub zamierzający spełniają wymagania dla <xref:System.Security.Permissions.PublisherIdentityPermission> w środowisku częściowego zaufania. (Wymagania dotyczące uprawnień tożsamości zawsze powiedzie się w środowisku pełnego zaufania).  
  
> [!NOTE]
>  Firma Microsoft zaleca, usługi, użyj `<generatePublisherEvidence>` element, aby zwiększyć wydajność uruchamiania.  Przy użyciu tego elementu może również pomóc uniknąć opóźnień, które mogą powodować upływu limitu czasu i anulowania uruchomienia usługi.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `<generatePublisherEvidence>` elementu, aby wyłączyć sprawdzanie urzędów certyfikacji zasad wydawcy dla aplikacji.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
