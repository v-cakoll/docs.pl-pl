---
title: "&lt;webRequestModules —&gt; — Element (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ac20d3da42b150734abbbd36c4ec9fc2e60b6216
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a>&lt;webRequestModules —&gt; — Element (ustawienia sieciowe)
Określa moduły służące do żądania informacji z hostów w sieci.  
  
 \<Konfiguracja >  
\<System.NET >  
\<webRequestModules — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Dodaj](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|Dodaje niestandardowego modułu żądania sieci Web do aplikacji.|  
|[Wyczyść](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|Usuwa wszystkie zarejestrowane moduły żądania sieci Web z aplikacji.|  
|[Usuń](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|Usuwa niestandardowego modułu żądania sieci Web z aplikacji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.|  
  
## <a name="remarks"></a>Uwagi  
 `webRequestModules` Element rejestruje elementów podrzędnych <xref:System.Net.WebRequest> klasy do obsługi żądań informacji do hostów w sieci. Moduły żądania sieci Web musi implementować <xref:System.Net.IWebRequestCreate> interfejsu.  
  
 .NET Framework zawiera identyfikatory URI, które rozpoczynają się od http://, https:// i file:// modułów żądania sieci Web. Można zastąpić domyślne moduły tylko poprzez zarejestrowanie niestandardowego modułu w pliku konfiguracji.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje domyślny moduł HTTP. Wartości należy zastąpić wersję i PublicKeyToken przy użyciu prawidłowych wartości dla określonego modułu.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.IWebRequestCreate>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
