---
title: <generatePublisherEvidence>, element
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 24a5ea02992a5bce681b5bab4fb7f75505bd225d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154117"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> Element
Określa, czy środowisko <xref:System.Security.Policy.Publisher> wykonawcze tworzy dowody zabezpieczeń dostępu do kodu (CAS).  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
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
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy środowisko <xref:System.Security.Policy.Publisher> wykonawcze tworzy dowody.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`false`|Nie tworzy <xref:System.Security.Policy.Publisher> dowodów.|  
|`true`|Tworzy <xref:System.Security.Policy.Publisher> dowody. Domyślnie włączone.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> W programie .NET Framework 4 i nowszych element ten nie ma wpływu na czasy ładowania zestawu. Aby uzyskać więcej informacji, zobacz sekcję "Uproszczenie zasad zabezpieczeń" w sekcji [Zmiany zabezpieczeń](../../../security/security-changes.md).  
  
 Środowisko wykonawcze języka wspólnego (CLR) próbuje zweryfikować authenticode <xref:System.Security.Policy.Publisher> podpisu w czasie ładowania, aby utworzyć dowody dla zestawu. Jednak domyślnie większość aplikacji nie <xref:System.Security.Policy.Publisher> potrzebuje dowodów. Standardowe zasady CAS nie <xref:System.Security.Policy.PublisherMembershipCondition>opierają się na . Należy unikać niepotrzebnych kosztów uruchamiania skojarzonych z weryfikacją podpisu wydawcy, chyba że aplikacja jest wykonywana <xref:System.Security.Permissions.PublisherIdentityPermission> na komputerze z niestandardowymi zasadami CAS lub zamierza zaspokoić wymagania w środowisku częściowego zaufania. (Wymagania dotyczące uprawnień tożsamości zawsze odnoszą sukces w środowisku pełnego zaufania).  
  
> [!NOTE]
> Zaleca się, że `<generatePublisherEvidence>` usługi używają tego elementu w celu zwiększenia wydajności uruchamiania.  Za pomocą tego elementu może również pomóc uniknąć opóźnień, które mogą spowodować limit czasu i anulowanie uruchamiania usługi.  
  
## <a name="configuration-file"></a>Plik konfiguracji  
 Ten element może być używany tylko w pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `<generatePublisherEvidence>` pokazano, jak użyć elementu, aby wyłączyć sprawdzanie zasad wydawcy CAS dla aplikacji.  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
