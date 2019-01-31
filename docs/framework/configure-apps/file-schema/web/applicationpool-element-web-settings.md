---
title: <applicationPool> — Element (Ustawienia sieci Web)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: b1afd6227444828c58b6dbb44de24fe82af9f8b2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271983"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool >, Element (ustawienia sieci Web)
Określa ustawienia konfiguracyjne, które są używane przez program ASP.NET do zarządzania zachowaniem całego procesu, gdy aplikacja ASP.NET działa w trybie zintegrowanym z [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowszej.  
  
> [!IMPORTANT]
>  Ten element i funkcja obsługuje działają tylko, jeśli Twoja aplikacja ASP.NET jest hostowana w [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub nowszej wersji.  
  
 \<Konfiguracja >  
\<System.Web >, Element (ustawienia sieci Web)  
\<applicationPool >, Element (ustawienia sieci Web)  
  
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
|`maxConcurrentRequestsPerCPU`|Określa liczbę równoczesnych żądań ASP.NET umożliwia dla każdego procesora CPU.|  
|`maxConcurrentThreadsPerCPU`|Określa, jak wiele wątków jednocześnie może być uruchomiony dla puli aplikacji dla każdego Procesora. Zapewnia alternatywny sposób sterowania współbieżnością ASP.NET, ponieważ pozwala ograniczyć liczbę zarządzanych wątkach, których można użyć na procesor CPU, aby obsłużyć żądania. Domyślnie to ustawienie jest 0, co oznacza, że ASP.NET nie ogranicza liczbę wątków, które mogą być tworzone dla każdego Procesora, mimo że ogranicza liczbę wątków, które można utworzyć puli wątków CLR.|  
|`requestQueueLimit`|Określa maksymalną liczbę żądań, które można umieścić w kolejce dla platformy ASP.NET w pojedynczym procesie. Po uruchomieniu co najmniej dwóch aplikacji ASP.NET w jednej puli aplikacji zbiorczego zestawu żądań wysyłanych do dowolnej aplikacji w puli podlega tego ustawienia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Zawiera informacje na temat współdziałania platformy ASP.NET z aplikacją hosta.|  
  
## <a name="remarks"></a>Uwagi  
 Po uruchomieniu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] lub jego nowsza wersja w trybie zintegrowanym tej kombinacji elementu umożliwia skonfigurowanie, jak ASP.NET zarządza żądaniami wątków i kolejki, gdy aplikacja jest obsługiwana w puli aplikacji usług IIS. Jeśli uruchomienie usług IIS 6 lub uruchomiony [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] w trybie klasycznym lub trybu ISAPI, te ustawienia są ignorowane.  
  
 `applicationPool` Ustawienia mają zastosowanie do wszystkich pul aplikacji działających w określonej wersji programu .NET Framework. Ustawienia są zawarte w plikach aspnet.config. Dostępna jest wersja tego pliku dla wersji 2.0 i 4.0 programu .NET Framework. (W wersji 3.0 i 3.5 programu .NET Framework Udostępnij plik aspnet.config w wersji 2.0).  
  
> [!IMPORTANT]
>  Jeśli uruchamiasz [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] na [!INCLUDE[win7](../../../../../includes/win7-md.md)], można skonfigurować plik aspnet.config osobne dla każdej puli aplikacji. Dzięki temu można dostosować wydajność wątków dla każdej puli aplikacji.  
  
 Aby uzyskać `maxConcurrentRequestsPerCPU` ustawienie domyślne ustawienie "5000" [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] skutecznie wyłącza ograniczanie żądań, oznacza to kontrolowane przez platformę ASP.NET, chyba że faktycznie mieć co najmniej 5000 żądań na CPU. Domyślne ustawienie zależy od zamiast puli wątków CLR automatycznie zarządzać współbieżności dla każdego procesora CPU. Aplikacji, które składają się zwiększone użycie asynchronicznego przetwarzania żądania lub wiele długotrwałych żądań, zablokowane na We/Wy, sieci będą mogli korzystać z zwiększenia domyślnego limitu w [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]. Ustawienie `maxConcurrentRequestsPerCPU` na zero spowoduje wyłączenie korzystanie z zarządzanych wątków do przetwarzania żądań ASP.NET. Po uruchomieniu aplikacji w puli aplikacji usług IIS, żądań, pozostają w wątku usługi IIS operacji We/Wy i w związku z tym współbieżności jest ograniczany przez usługi IIS wątek ustawienia.  
  
 `requestQueueLimit` Ustawienie działa w taki sam sposób jak `requestQueueLimit` atrybutu [processModel](https://msdn.microsoft.com/library/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) element, który jest ustawiony w plikach Web.config dla aplikacji ASP.NET. Jednak `requestQueueLimit` zastępuje ustawienia w pliku konfigurację aspnet.config `requestQueueLimit` ustawienia w pliku Web.config. Innymi słowy Jeśli ustawiono obu atrybutów (domyślnie jest to wartość true,) `requestQueueLimit` pierwszeństwo ma ustawienie w pliku konfigurację aspnet.config.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonfigurować zachowanie całego procesu ASP.NET w pliku konfigurację aspnet.config w następujących okolicznościach:  
  
-   Aplikacja jest obsługiwana w [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] puli aplikacji.  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] działa w trybie zintegrowanym.  
  
-   Aplikacja używa [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] lub nowszej.  
  
 Wartości w przykładzie są wartości domyślne.  
  
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
|Plik walidacji||  
|Może być pusta||  
  
## <a name="see-also"></a>Zobacz także
- [\<System.Web >, Element (ustawienia sieci Web)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
