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
ms.openlocfilehash: cc206e584440778858e61fc0bab51fc8ffa2009a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252379"
---
# <a name="publisherpolicy-element"></a>\<publisherPolicy> Element
Określa, czy środowisko uruchomieniowe stosuje zasady wydawcy.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zestawubinding**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> dependentAssembly**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<publisherPolicy Apply >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`apply`|Określa, czy mają być stosowane zasady wydawcy.|  
  
## <a name="apply-attribute"></a>Zastosuj atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`yes`|Stosuje zasady wydawcy. To jest ustawienie domyślne.|  
|`no`|Nie stosuje zasad wydawcy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  

Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`assemblyBinding`|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`dependentAssembly`|Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu. Użyj jednego `<dependentAssembly>` elementu dla każdego zestawu.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy dostawca składnika zwalnia nową wersję zestawu, dostawca może uwzględnić zasady wydawcy, aby aplikacje używające starej wersji używały teraz nowej wersji. Aby określić, czy zastosować zasady wydawcy dla określonego zestawu, umieść  **\<element publisherPolicy Apply >** w  **\<elemencie dependentAssembly >** .  
  
 Ustawieniem domyślnym dla atrybutu **apply** jest **tak**. Ustawienie atrybutu **Zastosuj** do **nie** zastępuje żadnych poprzednich ustawień **tak** dla zestawu.  
  
 Uprawnienie jest wymagane, aby aplikacja jawnie ignorował zasady wydawcy przy użyciu [ \<elementu publisherPolicy Apply Apply = "No"/>](publisherpolicy-element.md) w pliku konfiguracyjnym aplikacji. Uprawnienie jest udzielane przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> flagi <xref:System.Security.Permissions.SecurityPermission>na. Aby uzyskać więcej informacji, zobacz [uprawnienia zabezpieczeń przekierowania powiązania zestawu](../../assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje wyłączenie zasad wydawcy dla zestawu `myAssembly`.  
  
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

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../deployment/how-the-runtime-locates-assemblies.md)
- [Przekierowywanie wersji zestawu](../../redirect-assembly-versions.md)
