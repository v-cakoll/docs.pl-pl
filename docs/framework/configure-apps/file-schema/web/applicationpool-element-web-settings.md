---
title: <applicationPool>, element (ustawienia internetowe)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152857"
---
# <a name="applicationpool-element-web-settings"></a>\<Element> aplikacji (ustawienia sieci Web)
Określa ustawienia konfiguracji używane przez ASP.NET do zarządzania zachowaniem całego procesu, gdy aplikacja ASP.NET działa w trybie zintegrowanym w serwisach IIS 7.0 lub nowszej.  
  
> [!IMPORTANT]
> Ten element i funkcja, która obsługuje, działają tylko wtedy, gdy aplikacja ASP.NET jest hostowana w systemach IIS 7.0 lub nowszych wersjach.  
  
[**\<>konfiguracyjne**](../configuration-element.md)  
&nbsp;&nbsp;[**\<>system.web**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<aplikacja>**  
  
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
|`maxConcurrentRequestsPerCPU`|Określa, ile jednoczesnych żądań ASP.NET zezwala na procesor.|  
|`maxConcurrentThreadsPerCPU`|Określa, ile jednoczesnych wątków może być uruchomionych dla puli aplikacji dla każdego procesora CPU. Zapewnia to alternatywny sposób kontrolowania współbieżności ASP.NET, ponieważ można ograniczyć liczbę zarządzanych wątków, które mogą być używane na procesor do obsługi żądań. Domyślnie to ustawienie jest 0, co oznacza, że ASP.NET nie ogranicza liczbę wątków, które mogą być tworzone na procesor CPU, chociaż pula wątków CLR ogranicza również liczbę wątków, które mogą być tworzone.|  
|`requestQueueLimit`|Określa maksymalną liczbę żądań, które mogą być umieszczane w kolejce do ASP.NET w jednym procesie. Gdy dwie lub więcej ASP.NET aplikacji są uruchamiane w jednej puli aplikacji, skumulowany zestaw żądań składanych do dowolnej aplikacji w puli aplikacji podlega temu ustawieniu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>system.web](system-web-element-web-settings.md)|Zawiera informacje o tym, jak ASP.NET współdziała z aplikacją hosta.|  
  
## <a name="remarks"></a>Uwagi  

Po uruchomieniu usług IIS 7.0 lub nowszej wersji w trybie zintegrowanym ta kombinacja elementów umożliwia skonfigurowanie sposobu zarządzania ASP.NET żądaniami wątków i kolejek, gdy aplikacja jest hostowana w puli aplikacji usług IIS. Jeśli uruchomisz usługi IIS 6 lub uruchomisz usługi IIS 7.0 w trybie klasycznym lub ISAPI, te ustawienia zostaną zignorowane.  
  
Ustawienia `applicationPool` dotyczą wszystkich pul aplikacji, które są uruchamiane w określonej wersji programu .NET Framework. Ustawienia znajdują się w pliku aspnet.config. Istnieje wersja tego pliku dla wersji 2.0 i 4.0 programu .NET Framework. (Wersje 3.0 i 3.5 programu .NET Framework udostępniają plik aspnet.config w wersji 2.0).  
  
> [!IMPORTANT]
> Po uruchomieniu usług IIS 7.0 w systemie Windows 7 można skonfigurować oddzielny plik aspnet.config dla każdej puli aplikacji. Dzięki temu można dostosować wydajność wątków dla każdej puli aplikacji.  
  
Dla `maxConcurrentRequestsPerCPU` tego ustawienia domyślne ustawienie "5000" w .NET Framework 4 skutecznie wyłącza ograniczanie żądań, które jest kontrolowane przez ASP.NET, chyba że faktycznie masz 5000 lub więcej żądań na procesor. Ustawienie domyślne zależy od puli wątków CLR do automatycznego zarządzania współbieżności na procesor CPU. Aplikacje, które szeroko korzystają z przetwarzania żądań asynchronicznych lub które mają wiele długotrwałych żądań zablokowanych na we/wy sieci, skorzystają ze zwiększonego limitu domyślnego w programie .NET Framework 4. Ustawienie `maxConcurrentRequestsPerCPU` na zero wyłącza użycie wątków zarządzanych do przetwarzania żądań ASP.NET. Gdy aplikacja jest uruchamiana w puli aplikacji usług IIS, żądania pozostają w wątku we/wy usług IIS i w związku z tym współbieżność jest ograniczana przez ustawienia wątku usług IIS.  
  
Ustawienie `requestQueueLimit` działa w taki `requestQueueLimit` sam sposób jak atrybut [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, który jest ustawiony w plikach Web.config dla aplikacji ASP.NET. Jednak `requestQueueLimit` ustawienie w pliku aspnet.config zastępuje `requestQueueLimit` ustawienie w pliku Web.config. Innymi słowy, jeśli oba atrybuty są ustawione (domyślnie jest to prawda), `requestQueueLimit` ustawienie w pliku aspnet.config ma pierwszeństwo.  
  
## <a name="example"></a>Przykład  

W poniższym przykładzie pokazano, jak skonfigurować zachowanie ASP.NET całego procesu w pliku aspnet.config w następujących okolicznościach:  
  
- Aplikacja jest hostowana w puli aplikacji usług IIS 7.0.  
  
- Program IIS 7.0 działa w trybie zintegrowanym.  
  
- Aplikacja korzysta z dodatku SP1 programu .NET Framework 3.5 lub nowszej.  
  
Wartości w przykładzie są wartościami domyślnymi.  
  
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
|Plik sprawdzania poprawności||  
|Może być pusty||  
  
## <a name="see-also"></a>Zobacz też

- [\<element> system.web (ustawienia sieci Web)](system-web-element-web-settings.md)
