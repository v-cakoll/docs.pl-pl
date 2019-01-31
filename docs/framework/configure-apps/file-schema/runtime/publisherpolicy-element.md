---
title: <publisherPolicy>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be87c91b798256f3913779bdbe36f3548066018b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55253941"
---
# <a name="publisherpolicy-element"></a>\<publisherPolicy> Element
Określa, czy środowisko uruchomieniowe mają zastosowanie zasady wydawcy.  
  
 \<Konfiguracja >  
\<runtime>  
\<assemblybinding — >  
\<dependentAssembly>  
\<publisherPolicy>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`apply`|Określa, czy zastosować zasad wydawcy.|  
  
## <a name="apply-attribute"></a>Zastosuj atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`yes`|Zastosowanie zasad wydawcy. To jest ustawienie domyślne.|  
|`no`|Nie ma zastosowania zasad wydawcy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli dostawcy składników udostępnia nową wersję zestawu, dostawcy mogą być zasad wydawcy, dzięki czemu aplikacje, które używają starej wersji teraz używać nowej wersji. Aby określić, czy do zastosowania zasad wydawcy dla określonego zestawu, należy umieścić  **\<publisherPolicy >** element  **\<dependentAssembly >** elementu.  
  
 Ustawieniem domyślnym dla **zastosować** atrybut jest **tak**. Ustawienie **zastosować** atrybutu **nie** zastępuje wszystkie poprzednie **tak** ustawienia zestawu.  
  
 Uprawnienie jest wymagane dla aplikacji, aby jawnie Ignoruj przy użyciu zasad wydawcy [ \<zastosować publisherPolicy = "no" / >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elementu w pliku konfiguracyjnym aplikacji. To uprawnienie jest przydzielane przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> flagą <xref:System.Security.Permissions.SecurityPermission>. Aby uzyskać więcej informacji, zobacz [uprawnienie zabezpieczeń przekierowania powiązania zestawu](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje wyłączenie zasad wydawcy dla zestawu, `myAssembly`.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Przekierowywanie wersji zestawu](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
