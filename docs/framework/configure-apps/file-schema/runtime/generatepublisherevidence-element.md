---
title: <generatePublisherEvidence>, element
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caec297f8d0f6febad5cf46adb0a2658960c6bb1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663672"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> Element
Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowód dla zabezpieczeń dostępu kodu (CAS).  
  
 \<> konfiguracji  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowód.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie tworzy <xref:System.Security.Policy.Publisher> dowodów.|  
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
>  W .NET Framework 4 i nowszych ten element nie ma wpływu na czasy ładowania zestawu. Aby uzyskać więcej informacji, zobacz sekcję "uproszczenie zasad zabezpieczeń" w temacie [zmiany zabezpieczeń](../../../security/security-changes.md).  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) próbuje zweryfikować podpis Authenticode w czasie ładowania, aby <xref:System.Security.Policy.Publisher> utworzyć dowód dla zestawu. Jednak domyślnie większość aplikacji nie potrzebuje <xref:System.Security.Policy.Publisher> dowodu. Standardowe zasady CAS nie bazują na <xref:System.Security.Policy.PublisherMembershipCondition>. Należy unikać niepotrzebnego kosztu uruchomienia związanego z weryfikacją podpisu wydawcy, chyba że aplikacja jest wykonywana na komputerze z niestandardowymi zasadami CAS lub nie spełnia wymagań dotyczących <xref:System.Security.Permissions.PublisherIdentityPermission> w środowisku częściowego zaufania. (Wymagania dotyczące uprawnień tożsamości zawsze powiodło się w środowisku pełnego zaufania).  
  
> [!NOTE]
>  Zalecamy, aby usługi korzystały `<generatePublisherEvidence>` z elementu, aby zwiększyć wydajność uruchamiania.  Za pomocą tego elementu można także uniknąć opóźnień, które mogą spowodować przekroczenie limitu czasu i anulowanie uruchamiania usługi.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Tego elementu można używać tylko w pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak użyć elementu, `<generatePublisherEvidence>` aby wyłączyć sprawdzanie zasad wydawcy CAS dla aplikacji.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
