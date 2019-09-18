---
title: 'Instrukcje: określanie zasad pamięci podręcznej na podstawie lokalizacji dla aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- explicitly defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 150198c2bda220e4b37981e461e19b8e4e30e483
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048121"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a>Instrukcje: określanie zasad pamięci podręcznej na podstawie lokalizacji dla aplikacji
Zasady pamięci podręcznej oparte na lokalizacji pozwalają aplikacji jawnie definiować zachowanie buforowania na podstawie lokalizacji żądanego zasobu. W tym temacie pokazano, jak skonfigurować zasady pamięci podręcznej. Aby uzyskać informacje na temat ustawiania zasad dla aplikacji przy użyciu plików konfiguracji, zobacz [ \<requestCaching > element (Ustawienia sieci)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a>Aby ustawić zasady pamięci podręcznej oparte na lokalizacji dla aplikacji  
  
1. Utwórz obiekt <xref:System.Net.Cache.HttpRequestCachePolicy>lub. <xref:System.Net.Cache.RequestCachePolicy>  
  
2. Ustaw obiekt zasad jako domyślny dla domeny aplikacji.  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a>Aby ustawić zasady, które pobierają żądane zasoby z pamięci podręcznej  
  
- Utwórz zasady, które żądają żądanych zasobów z pamięci podręcznej, jeśli są dostępne, a w przeciwnym razie wysyła żądania do serwera, <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>ustawiając poziom pamięci podręcznej na. Żądanie może być spełnione przez dowolną pamięć podręczną klienta i serwera, w tym zdalnych pamięci podręcznych.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a>Aby ustawić zasady, które uniemożliwiają dostarczenie zasobów przez żadną pamięć podręczną  
  
- Utwórz zasady, które uniemożliwiają każdej pamięci podręcznej dostarczenie żądanych zasobów przez ustawienie <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>poziomu pamięci podręcznej na wartość. Ten poziom zasad usuwa zasób z lokalnej pamięci podręcznej, jeśli jest obecny, i wskazuje na zdalne pamięci podręczne, które powinny również usunąć zasób.  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a>Aby ustawić zasady zwracające żądane zasoby tylko wtedy, gdy znajdują się w lokalnej pamięci podręcznej  
  
- Utwórz zasady zwracające żądane zasoby tylko wtedy, gdy znajdują się w lokalnej pamięci podręcznej, ustawiając <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>poziom pamięci podręcznej na. Jeśli żądany zasób nie znajduje się w pamięci podręcznej <xref:System.Net.WebException> , zostanie zgłoszony wyjątek.  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a>Aby ustawić zasady, które uniemożliwiają lokalnej pamięci podręcznej dostarczanie zasobów  
  
- Utwórz zasady, które uniemożliwiają lokalnej pamięci podręcznej dostarczenie żądanych zasobów przez ustawienie poziomu <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>pamięci podręcznej na wartość. Jeśli żądany zasób znajduje się w pośredniej pamięci podręcznej i zostanie pomyślnie ponownie zweryfikowany, pośrednia pamięć podręczna może dostarczyć żądany zasób.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a>Aby ustawić zasady, które uniemożliwiają dostarczenie żądanych zasobów przez żadną pamięć podręczną  
  
- Utwórz zasady, które uniemożliwiają każdej pamięci podręcznej dostarczenie żądanych zasobów przez ustawienie <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>poziomu pamięci podręcznej na wartość. Zasób zwrócony przez serwer może być przechowywany w pamięci podręcznej.  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a>Aby ustawić zasady zezwalające każdej pamięci podręcznej na dostarczenie żądanych zasobów, jeśli zasób na serwerze nie jest nowszy niż w pamięci podręcznej  
  
- Utwórz zasady, które zezwalają dowolnej pamięci podręcznej na dostarczenie żądanych zasobów, jeśli zasób na serwerze nie jest nowszy niż w pamięci podręcznej, ustawiając poziom bufora na <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.  
  
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

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [\<requestCaching >, element (Ustawienia sieci)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
