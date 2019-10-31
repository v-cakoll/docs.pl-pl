---
title: <generatePublisherEvidence> Element
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: b04ef53d6e9c3d954b0925ea8634b3d220b36af7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116578"
---
# <a name="generatepublisherevidence-element"></a>\<element > generatePublisherEvidence
Określa, czy środowisko uruchomieniowe tworzy <xref:System.Security.Policy.Publisher> dowody dla zabezpieczeń dostępu kodu (CAS).  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<generatePublisherEvidence >**  
  
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
> W .NET Framework 4 i nowszych ten element nie ma wpływu na czasy ładowania zestawu. Aby uzyskać więcej informacji, zobacz sekcję "uproszczenie zasad zabezpieczeń" w temacie [zmiany zabezpieczeń](../../../security/security-changes.md).  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) próbuje zweryfikować podpis Authenticode w czasie ładowania, aby utworzyć <xref:System.Security.Policy.Publisher> dowód dla zestawu. Jednak domyślnie większość aplikacji nie potrzebuje <xref:System.Security.Policy.Publisher> dowodu. Standardowe zasady CAS nie bazują na <xref:System.Security.Policy.PublisherMembershipCondition>. Należy unikać niepotrzebnego kosztu uruchomienia związanego z weryfikacją podpisu wydawcy, chyba że aplikacja jest wykonywana na komputerze z niestandardowymi zasadami CAS lub ma zamiarować wymagania dotyczące <xref:System.Security.Permissions.PublisherIdentityPermission> w środowisku częściowego zaufania. (Wymagania dotyczące uprawnień tożsamości zawsze powiodło się w środowisku pełnego zaufania).  
  
> [!NOTE]
> Zalecamy, aby usługi używały elementu `<generatePublisherEvidence>`, aby zwiększyć wydajność uruchamiania.  Za pomocą tego elementu można także uniknąć opóźnień, które mogą spowodować przekroczenie limitu czasu i anulowanie uruchamiania usługi.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Tego elementu można używać tylko w pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać elementu `<generatePublisherEvidence>`, aby wyłączyć sprawdzanie zasad wydawcy CAS dla aplikacji.  
  
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
