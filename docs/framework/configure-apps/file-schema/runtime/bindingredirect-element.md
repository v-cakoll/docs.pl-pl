---
title: "&lt;w parametrze bindingRedirect&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f8cd497871d8a58504cf790f84cc7e5a1d4e39b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltbindingredirectgt-element"></a>&lt;w parametrze bindingRedirect&gt; — Element
Przekierowuje jedną wersję zestawu do innej.  
  
 \<Konfiguracja >  
\<Runtime >  
\<assemblybinding — >  
\<dependentAssembly >  
\<w parametrze bindingRedirect >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`oldVersion`|Atrybut wymagany.<br /><br /> Określa pierwotnie żądaną wersję zestawu. Format numeru wersji zestawu jest *główna.pomocnicza.kompilacja.poprawka*. Prawidłowe wartości każdej części tego numeru wersji należą do zakresu od 0 do 65535.<br /><br /> Można również określić zakres wersji w następującym formacie:<br /><br /> *n.n.n.n - n.n.n.n*|  
|`newVersion`|Atrybut wymagany.<br /><br /> Określa wersję zestawu do użycia zamiast pierwotnie żądanej wersji w formacie: *n.n.n.n*<br /><br /> Tę wartość można określić wersji starszej niż `oldVersion`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Brak||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`assemblyBinding`|Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`dependentAssembly`|Hermetyzuje zasady powiązań oraz lokalizację zestawu dla każdego zestawu. Dla każdego zestawu należy użyć jednego elementu dependentAssembly.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku skompilowania aplikacji programu .NET Framework z użyciem zestawu o silnej nazwie aplikacja domyślnie używa tej wersji w czasie działania, nawet jeśli jest dostępna nowa wersja. Można jednak skonfigurować aplikację do działania z użyciem nowszej wersji zestawu. Szczegółowe informacje dotyczące sposobu środowiska uruchomieniowego używa tych plików w celu określenia wersji zestawu do użycia, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Można przekierować więcej niż jedną wersję zestawu przez dołączenie wielu `bindingRedirect` elementów w `dependentAssembly` elementu. Można również wykonać przekierowanie z nowszej wersji zestawu do starszej.  
  
 Jawne przekierowanie powiązań zestawu w pliku konfiguracji aplikacji wymaga uprawnienia zabezpieczeń. Dotyczy to przekierowań zestawów programu .NET Framework i zestawów firm trzecich. Uprawnienie zostanie udzielone przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> Flaga na <xref:System.Security.Permissions.SecurityPermission>. Aby uzyskać więcej informacji, zobacz [uprawnienie zabezpieczeń przekierowania powiązania zestawu](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób przekierowywania wersji zestawu.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Przekierowywanie wersji zestawu](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
