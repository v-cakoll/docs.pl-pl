---
title: '&lt;applicationPool&gt; elementu (ustawienia sieci Web)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 70119b3067342dc9bc93e0fb8a43a3242f2dacc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltapplicationpoolgt-element-web-settings"></a>&lt;applicationPool&gt; elementu (ustawienia sieci Web)
Określa ustawienia konfiguracji, które są używane przez program ASP.NET do zarządzania zachowanie całego procesu, gdy aplikacja ASP.NET działa w trybie zintegrowanym z [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowszym.  
  
> [!IMPORTANT]
>  Ten element i funkcji obsługuje działa tylko, jeśli aplikacja ASP.NET jest hostowany na [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowszy.  
  
 \<Konfiguracja >  
\<System.Web > elementu (ustawienia sieci Web)  
\<applicationPool > elementu (ustawienia sieci Web)  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|Określa liczbę jednoczesnych żądań ASP.NET umożliwia dla każdego procesora CPU.|  
|`maxConcurrentThreadsPerCPU`|Określa, jak wiele wątków jednoczesnych może być uruchomiony dla każdego procesora CPU dla puli aplikacji. Zapewnia to alternatywny sposób sterowania współbieżnością ASP.NET, ponieważ można ograniczyć liczbę wątków zarządzanych, których można użyć dla każdego procesora CPU do obsługi żądań. Domyślnie to ustawienie jest 0, co oznacza, że ASP.NET nie ogranicza liczbę wątków, które mogą zostać utworzone dla każdego Procesora, mimo że pula wątków CLR również ogranicza liczbę wątków, które mogą zostać utworzone.|  
|`requestQueueLimit`|Określa maksymalną liczbę żądań, które można umieścić w kolejce dla ASP.NET w ramach jednego procesu. Uruchomienie dwóch lub więcej aplikacji ASP.NET w jednej puli aplikacji zbiorczego zestawu żądań wysyłanych do aplikacji w puli podlega to ustawienie.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<System.Web >](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Zawiera informacje na temat współdziałania ASP.NET z aplikacji hosta.|  
  
## <a name="remarks"></a>Uwagi  
 Po uruchomieniu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowszym w trybie zintegrowanym tej kombinacji elementu umożliwia skonfigurowanie, jak ASP.NET zarządza żądaniami wątków i kolejek, kiedy aplikacja znajduje się w puli aplikacji usług IIS. Jeśli uruchomienie programu IIS 6 lub uruchomiony [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] w trybie klasycznym lub trybu ISAPI, te ustawienia są ignorowane.  
  
 `applicationPool` Ustawienia mają zastosowanie do wszystkich pul aplikacji uruchomionych w określonej wersji programu .NET Framework. Ustawienia są zawarte w pliku konfigurację aspnet.config. Dostępna jest wersja tego pliku w wersjach 2.0 i 4.0 programu .NET Framework. (W wersji 3.0 i 3.5 programu .NET Framework udostępnianie pliku konfigurację aspnet.config w wersji 2.0).  
  
> [!IMPORTANT]
>  Po uruchomieniu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] na [!INCLUDE[win7](../../../../../includes/win7-md.md)], można skonfigurować plik konfigurację aspnet.config osobne dla każdej puli aplikacji. Dzięki temu można dostosować wydajność wątków dla każdej puli aplikacji.  
  
 Aby uzyskać `maxConcurrentRequestsPerCPU` ustawienie domyślne ustawienie "5000" [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] skutecznie wyłącza ograniczanie żądań, który jest kontrolowany przez platformę ASP.NET, chyba że masz faktycznie 5000 lub więcej żądań dla każdego procesora CPU. Domyślne ustawienie zależy od zamiast puli wątków CLR automatycznie zarządzać współbieżności dla każdego procesora CPU. Aplikacji, który należy zwiększone użycie asynchronicznego przetwarzania żądania lub wiele żądań długotrwałe zablokowane w sieci We/Wy, będą korzystać z zwiększenia domyślnego limitu w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]. Ustawienie `maxConcurrentRequestsPerCPU` na zero spowoduje wyłączenie używanie zarządzanych wątków do przetwarzania żądań ASP.NET. Po uruchomieniu aplikacji w puli aplikacji usług IIS żądań pozostać w wątku usługi IIS we/wy i w związku z tym współbieżności jest ograniczany przez usługi IIS ustawienia wątku.  
  
 `requestQueueLimit` Ustawienie działa tak samo jak `requestQueueLimit` atrybutu [processModel](http://msdn.microsoft.com/en-us/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) element, który jest ustawiony w plikach Web.config dla aplikacji ASP.NET. Jednak `requestQueueLimit` zastępuje ustawienia w pliku konfigurację aspnet.config `requestQueueLimit` ustawienia w pliku Web.config. Innymi słowy Jeśli oba atrybuty są ustawiane (domyślnie jest to wartość true,) `requestQueueLimit` pierwszeństwo ma ustawienie w pliku konfigurację aspnet.config.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób skonfigurować działanie całego procesu ASP.NET w pliku konfigurację aspnet.config w następujących okolicznościach:  
  
-   Aplikacja jest hostowana w [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] puli aplikacji.  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)]działa w trybie zintegrowanym.  
  
-   Aplikacja używa [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] lub nowszym.  
  
 Wartości w tym przykładzie są wartościami domyślnymi.  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>Informacje o elementach  
  
|||  
|-|-|  
|Przestrzeń nazw||  
|Nazwa schematu||  
|Sprawdzanie poprawności pliku||  
|Może być pusta||  
  
## <a name="see-also"></a>Zobacz też  
 [\<System.Web > elementu (ustawienia sieci Web)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
