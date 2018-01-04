---
title: "Porady: Ustawianie zasad na podstawie lokalizacji pamięci podręcznej dla aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expliciting defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9d54a34b5d7cf40a6eaa9d777b9b05a1be34f177
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a>Porady: Ustawianie zasad na podstawie lokalizacji pamięci podręcznej dla aplikacji
Zasady oparte na lokalizacji pamięci podręcznej zezwolić aplikacji na jawnie zdefiniuj zachowanie buforowania w oparciu o lokalizację żądanego zasobu. W tym temacie przedstawiono programowo ustawienie zasady pamięci podręcznej. Aby uzyskać informacje na temat ustawiania zasad dla aplikacji za pomocą plików konfiguracji, zobacz [ \<requestCaching — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a>Aby ustawić zasady oparte na lokalizacji pamięci podręcznej dla aplikacji  
  
1.  Utwórz <xref:System.Net.Cache.RequestCachePolicy> lub <xref:System.Net.Cache.HttpRequestCachePolicy> obiektu.  
  
2.  Ustaw ten obiekt zasad jako domyślnej domeny aplikacji.  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a>Aby ustawić zasady, które przyjmuje żądanych zasobów z pamięci podręcznej  
  
-   Utwórz zasadę, która przyjmuje żądanych zasobów z pamięci podręcznej, jeśli jest dostępny, a w przeciwnym razie wysyła żądania do serwera, ustawiając poziomu do pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>. Żądania mogą być spełnione przez dowolnego pamięci podręcznej między klientem a serwerem, w tym zdalnego pamięci podręcznych.  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a>Aby ustawić zasady, która uniemożliwia dostarczanie zasobów żadnych pamięci podręcznej  
  
-   Utwórz zasadę, która uniemożliwia dostarczanie żądanych zasobów przez ustawienie poziomu do pamięci podręcznej żadnych pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>. Ten poziom zasad Usuwa zasób z lokalnej pamięci podręcznej, jeśli jest obecny oraz wskazuje zdalnego pamięci podręcznych, czy należy również usunąć zasób.  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a>Aby ustawić zasady, która zwraca żądanych zasobów tylko wtedy, gdy znajdują się w lokalnej pamięci podręcznej  
  
-   Utwórz zasadę, która zwraca żądanych zasobów tylko wtedy, gdy znajdują się w lokalnej pamięci podręcznej przez ustawienie poziomu do pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>. Jeśli żądany zasób nie jest w pamięci podręcznej, <xref:System.Net.WebException> wyjątku.  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a>Aby skonfigurować zasady, która uniemożliwia dostarczanie zasobów w lokalnej pamięci podręcznej  
  
-   Tworzenie zasad, który uniemożliwia dostarczanie żądanych zasobów przez ustawienie poziomu do pamięci podręcznej w lokalnej pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>. Żądany zasób w pośrednim pamięci podręcznej, jest pomyślnie ponownie sprawdzić poprawności pośredniego pamięci podręcznej można podać żądanego zasobu.  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a>Aby ustawić zasady, która uniemożliwia dostarczanie żadnych pamięci podręcznej zażądał zasobów  
  
-   Utwórz zasadę, która uniemożliwia dostarczanie żądanych zasobów przez ustawienie poziomu do pamięci podręcznej żadnych pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>. Zasób zwrócony przez serwer mogą być przechowywane w pamięci podręcznej.  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a>Aby ustawić zasady, które umożliwia żadnych pamięci podręcznej, aby dostarczyć żądanych zasobów, jeśli nie jest nowszy niż buforowanej kopii zasobu na serwerze  
  
-   Utwórz zasadę, która umożliwia żadnych pamięci podręcznej, aby dostarczyć żądanych zasobów, jeśli zasobu na serwerze nie jest nowsza niż kopia pamięci podręcznej przez ustawienie poziomu do pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [\<requestCaching — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
