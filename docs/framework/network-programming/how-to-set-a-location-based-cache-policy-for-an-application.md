---
title: 'Instrukcje: określanie zasad pamięci podręcznej na podstawie lokalizacji dla aplikacji'
ms.date: 03/30/2017
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
ms.openlocfilehash: 06d458828c77f61e03d18f635ec00f6a7267bab8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341871"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a>Instrukcje: określanie zasad pamięci podręcznej na podstawie lokalizacji dla aplikacji
Zasady pamięci podręcznej oparte na lokalizacji zezwolić aplikacji na jawne zdefiniowanie zachowania buforowania na podstawie lokalizacji żądanego zasobu. W tym temacie przedstawiono programowe Ustawianie zasad pamięci podręcznej. Aby uzyskać informacje na temat ustawiania zasad dla aplikacji za pomocą plików konfiguracji, zobacz [ \<requestCaching — >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a>Aby ustawić zasady oparte na lokalizacji pamięci podręcznej dla aplikacji  
  
1. Tworzenie <xref:System.Net.Cache.RequestCachePolicy> lub <xref:System.Net.Cache.HttpRequestCachePolicy> obiektu.  
  
2. Obiekt zasad należy ustawić jako domyślne dla domeny aplikacji.  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a>Aby ustawić zasady, która przyjmuje żądanych zasobów z pamięci podręcznej  
  
-   Utworzyć zasadę, która przyjmuje żądanych zasobów z pamięci podręcznej, jeśli jest dostępny, a w przeciwnym razie wysyła żądania do serwera, przez ustawienie poziomie do pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>. Żądanie może być spełnione przez wszelkie pamięci między klientem i serwerem, w tym zdalnego pamięci podręcznych.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a>Aby ustawić zasady, który uniemożliwia dostarczanie zasobów wszelkie pamięci  
  
-   Tworzenie zasad, który uniemożliwia dostarczanie żądanych zasobów przez ustawienie poziomie do pamięci podręcznej wszelkie pamięci <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>. Ten poziom zasad Usuwa zasób z lokalnej pamięci podręcznej, jeśli jest obecny i wskazuje zdalnego pamięci podręcznych, że należy również usunąć zasób.  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a>Aby ustawić zasady, które zwraca żądanych zasobów tylko wtedy, gdy znajdują się w lokalnej pamięci podręcznej  
  
-   Utwórz zasadę, która zwraca żądanych zasobów tylko wtedy, gdy znajdują się w lokalnej pamięci podręcznej przez ustawienie poziomie do pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>. Jeśli żądany zasób nie znajduje się w pamięci podręcznej, <xref:System.Net.WebException> wyjątku.  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a>Aby ustawić zasady, który uniemożliwia dostarczanie zasobów w lokalnej pamięci podręcznej  
  
-   Tworzenie zasad, który uniemożliwia dostarczanie żądanych zasobów przez ustawienie poziomie do pamięci podręcznej lokalnej pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>. Jeśli żądany zasób jest w pamięci podręcznej pośredniego, pomyślnie sprawdzony ponownie pośrednich pamięci podręcznej można podać żądanego zasobu.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a>Aby ustawić zasady, który uniemożliwia dostarczanie wszelkie pamięci żądana zasobów  
  
-   Tworzenie zasad, który uniemożliwia dostarczanie żądanych zasobów przez ustawienie poziomie do pamięci podręcznej wszelkie pamięci <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>. Zasób, zwracany przez serwer mogą być przechowywane w pamięci podręcznej.  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a>Aby skonfigurować zasady, które umożliwia dowolnym pamięci podręcznej, aby dostarczyć żądanych zasobów, jeśli zasobu na serwerze nie jest nowszy niż buforowana kopia  
  
-   Utworzyć zasadę, która zezwala na wszystkie pamięci podręcznej, aby dostarczyć żądanych zasobów, jeśli zasobu na serwerze nie jest nowszy niż pamięci podręcznej przez ustawienie poziomie do pamięci podręcznej <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [\<requestCaching — >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
