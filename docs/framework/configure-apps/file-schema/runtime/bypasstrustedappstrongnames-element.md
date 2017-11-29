---
title: "&lt;bypasstrustedappstrongnames —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2b3e1cb839e9e7fd81a5452c0e034c3552b230cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a>&lt;bypasstrustedappstrongnames —&gt; — Element
Określa, czy pominąć weryfikacji silnych nazw zestawów pełnego zaufania, które są ładowane do pełnego zaufania <xref:System.AppDomain>.  
  
 \<Konfiguracja >  
\<Runtime >  
\<bypasstrustedappstrongnames — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`enabled`|Atrybut wymagany.<br /><br /> Określa, czy jest włączona funkcja obejścia, która pozwala uniknąć weryfikacji silnej nazwy zestawów pełnego zaufania. Gdy ta funkcja jest włączona, silne nazwy nie zostaną sprawdzone pod kątem poprawności, gdy zestaw jest ładowany. Wartość domyślna to `true`.|  
  
## <a name="enabled-attribute"></a>Atrybut włączony  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`true`|Podpisy silnej nazwy zestawów pełnego zaufania nie są weryfikowane podczas zestawy są ładowane do pełnego zaufania <xref:System.AppDomain>. Domyślnie włączone.|  
|`false`|Podpisy silnej nazwy zestawów pełnego zaufania są weryfikowane podczas zestawy są ładowane do pełnego zaufania <xref:System.AppDomain>. Podpis silnej nazwy jest sprawdzany tylko pod kątem poprawności podpisu; nie była porównywana do innego silnej nazwy pod kątem dopasowania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`runtime`|Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 Funkcja pomijania silnej nazwy pozwala uniknąć obciążenie weryfikacji podpisu silnej nazwy zestawów pełnego zaufania.  
  
 Funkcja pomijania ma zastosowanie do dowolnego zestawu, który jest podpisany przy użyciu silnej nazwy i ma następujące cechy:  
  
-   Pełni zaufany bez <xref:System.Security.Policy.StrongName> dowód (na przykład `MyComputer` strefy dowód).  
  
-   Załadowane w pełni zaufany <xref:System.AppDomain>.  
  
-   Załadowane z lokalizacji w <xref:System.AppDomainSetup.ApplicationBase%2A> właściwości tego <xref:System.AppDomain>.  
  
-   Nie podpisywany z opóźnieniem.  
  
> [!NOTE]
>  Jeśli funkcja pomijania została wyłączona dla wszystkich aplikacji na komputerze przy użyciu klucza rejestru, to ustawienie pliku konfiguracji nie ma żadnego skutku. Aby uzyskać więcej informacji, zobacz [porady: wyłączanie funkcji pomijania silnej nazwy](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak do określania zachowania, która weryfikuje podpisu silnej nazwy zestawów pełnego zaufania.  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień środowiska uruchomieniowego](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Porady: wyłączanie funkcji pomijania silnej nazwy](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
