---
title: <applicationPool>, element (ustawienia internetowe)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: d6c931ec904e9a7e58d5b747c74898208863b8e9
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486722"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool >, Element (ustawienia sieci Web)
Określa ustawienia konfiguracyjne, które są używane przez platformę ASP.NET do zarządzania zachowaniem całego procesu, gdy aplikacja ASP.NET działa w trybie zintegrowanym w usługach IIS 7.0 lub nowszej wersji.  
  
> [!IMPORTANT]
>  Ten element i funkcja obsługuje działają tylko w przypadku aplikacji ASP.NET znajduje się w usługach IIS 7.0 lub nowszy.  
  
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
 Po uruchomieniu usług IIS 7.0 lub nowszym w trybie zintegrowanym tej kombinacji elementu umożliwia skonfigurowanie, jak ASP.NET zarządza żądaniami wątków i kolejki, gdy aplikacja jest obsługiwana w puli aplikacji usług IIS. Jeśli uruchamianie usług IIS 6 lub uruchom usługi IIS 7.0 w trybie klasycznym lub w trybie ISAPI, te ustawienia są ignorowane.  
  
 `applicationPool` Ustawienia mają zastosowanie do wszystkich pul aplikacji działających w określonej wersji programu .NET Framework. Ustawienia są zawarte w plikach aspnet.config. Dostępna jest wersja tego pliku dla wersji 2.0 i 4.0 programu .NET Framework. (W wersji 3.0 i 3.5 programu .NET Framework Udostępnij plik aspnet.config w wersji 2.0).  
  
> [!IMPORTANT]
>  Po uruchomieniu usług IIS 7.0 na [!INCLUDE[win7](../../../../../includes/win7-md.md)], można skonfigurować plik aspnet.config osobne dla każdej puli aplikacji. Dzięki temu można dostosować wydajność wątków dla każdej puli aplikacji.  
  
 Aby uzyskać `maxConcurrentRequestsPerCPU` ustawienie domyślne ustawienie "5000" w programie .NET Framework 4 skutecznie wyłącza ograniczanie żądań, które są kontrolowane przez platformę ASP.NET, chyba że faktycznie mieć co najmniej 5000 żądań na CPU. Domyślne ustawienie zależy od zamiast puli wątków CLR automatycznie zarządzać współbieżności dla każdego procesora CPU. Aplikacji, które składają się zwiększone użycie asynchronicznego przetwarzania żądania lub wiele długotrwałych żądań, zablokowane na We/Wy, sieci będą mogli korzystać z zwiększenia domyślnego limitu w programie .NET Framework 4. Ustawienie `maxConcurrentRequestsPerCPU` na zero spowoduje wyłączenie korzystanie z zarządzanych wątków do przetwarzania żądań ASP.NET. Po uruchomieniu aplikacji w puli aplikacji usług IIS, żądań, pozostają w wątku usługi IIS operacji We/Wy i w związku z tym współbieżności jest ograniczany przez usługi IIS wątek ustawienia.  
  
 `requestQueueLimit` Ustawienie działa w taki sam sposób jak `requestQueueLimit` atrybutu [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, który jest ustawiony w plikach Web.config dla aplikacji ASP.NET. Jednak `requestQueueLimit` zastępuje ustawienia w pliku konfigurację aspnet.config `requestQueueLimit` ustawienia w pliku Web.config. Innymi słowy Jeśli ustawiono obu atrybutów (domyślnie jest to wartość true,) `requestQueueLimit` pierwszeństwo ma ustawienie w pliku konfigurację aspnet.config.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skonfigurować zachowanie całego procesu ASP.NET w pliku konfigurację aspnet.config w następujących okolicznościach:  
  
- Aplikacja jest obsługiwana w puli aplikacji usług IIS 7.0.  
  
- Usługi IIS 7.0 jest uruchomiony w trybie zintegrowanym.  
  
- Aplikacja używa .NET Framework 3.5 z dodatkiem SP1 lub nowszym.  
  
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
