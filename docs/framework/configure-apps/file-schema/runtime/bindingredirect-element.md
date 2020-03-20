---
title: <bindingRedirect>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: d96585b397f75dcb9fac7e7fce93799cc95e7c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154299"
---
# <a name="bindingredirect-element"></a>\<element> bindingRedirect
Przekierowuje jedną wersję zestawu do innej.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>montażowy**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>bindingRedirect**  
  
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
|`oldVersion`|Atrybut wymagany.<br /><br /> Określa pierwotnie żądaną wersję zestawu. Format numeru wersji zestawu to *major.minor.build.revision*. Prawidłowe wartości każdej części tego numeru wersji należą do zakresu od 0 do 65535.<br /><br /> Można również określić zakres wersji w następującym formacie:<br /><br /> *n.n.n.n - n.n.n.n*|  
|`newVersion`|Atrybut wymagany.<br /><br /> Określa wersję zestawu, która ma być używana zamiast pierwotnie żądanej wersji w formacie: *n.n.n.n*<br /><br /> Ta wartość może określić `oldVersion`wcześniejszą wersję niż .|  
  
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
 W przypadku skompilowania aplikacji programu .NET Framework z użyciem zestawu o silnej nazwie aplikacja domyślnie używa tej wersji w czasie działania, nawet jeśli jest dostępna nowa wersja. Można jednak skonfigurować aplikację do działania z użyciem nowszej wersji zestawu. Aby uzyskać szczegółowe informacje na temat sposobu, w jaki środowisko wykonawcze używa tych plików do określenia, której wersji zestawu użyć, zobacz [Jak środowisko wykonawcze lokalizuje zestawy](../../../deployment/how-the-runtime-locates-assemblies.md).  
  
 Można przekierować więcej niż jedną `bindingRedirect` wersję zestawu, dołączając wiele elementów w elemencie. `dependentAssembly` Można również wykonać przekierowanie z nowszej wersji zestawu do starszej.  
  
 Jawne przekierowanie powiązań zestawu w pliku konfiguracji aplikacji wymaga uprawnienia zabezpieczeń. Dotyczy to przekierowań zestawów programu .NET Framework i zestawów firm trzecich. Uprawnienie jest przyznawane <xref:System.Security.Permissions.SecurityPermissionFlag> przez ustawienie <xref:System.Security.Permissions.SecurityPermission>flagi na pliku . Aby uzyskać więcej informacji, zobacz [Uprawnienie zabezpieczeń przekierowania powiązania zestawu](../../assembly-binding-redirection-security-permission.md).  
  
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

- [Schemat ustawień środowiska uruchomieniowego](index.md)
- [Schemat pliku konfiguracji](../index.md)
- [Przekierowywanie wersji zestawu](../../redirect-assembly-versions.md)
