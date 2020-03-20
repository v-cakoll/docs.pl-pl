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
ms.openlocfilehash: 6fe569e781b005461ea41e3d6b90859666f9601a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180780"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a>Instrukcje: określanie zasad pamięci podręcznej na podstawie lokalizacji dla aplikacji
Zasady pamięci podręcznej oparte na lokalizacji umożliwiają aplikacji jawne definiowanie zachowania buforowania na podstawie lokalizacji żądanego zasobu. W tym temacie przedstawiono programowe ustawianie zasad pamięci podręcznej. Aby uzyskać informacje na temat ustawiania zasad dla aplikacji przy użyciu plików konfiguracyjnych, zobacz [ \<requestCaching> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a>Aby ustawić zasadę pamięci podręcznej opartą na lokalizacji dla aplikacji  
  
1. Utwórz <xref:System.Net.Cache.RequestCachePolicy> <xref:System.Net.Cache.HttpRequestCachePolicy> obiekt lub obiekt.  
  
2. Ustaw obiekt zasad jako domyślny dla domeny aplikacji.  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a>Aby ustawić zasadę, która pobiera żądane zasoby z pamięci podręcznej  
  
- Utwórz zasadę, która pobiera żądane zasoby z pamięci podręcznej, jeśli są dostępne, a w przeciwnym razie wysyła żądania do serwera, ustawiając poziom pamięci podręcznej na <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>. Żądanie może zostać spełnione przez dowolną pamięć podręczną między klientem a serwerem, w tym zdalne pamięci podręczne.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a>Aby ustawić zasadę, która uniemożliwia dostarczanie zasobów przez pamięć podręczną  
  
- Utwórz zasadę, która uniemożliwia dostarczanie żądanych zasobów przez <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>pamięć podręczną, ustawiając poziom pamięci podręcznej na . Ten poziom zasad usuwa zasób z lokalnej pamięci podręcznej, jeśli jest obecny i wskazuje do zdalnych pamięci podręcznych, że należy również usunąć zasób.  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a>Aby ustawić zasadę, która zwraca żądane zasoby tylko wtedy, gdy znajdują się one w lokalnej pamięci podręcznej  
  
- Utwórz zasadę, która zwraca żądane zasoby tylko wtedy, gdy <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>znajdują się w lokalnej pamięci podręcznej, ustawiając poziom pamięci podręcznej na . Jeśli żądany zasób nie znajduje <xref:System.Net.WebException> się w pamięci podręcznej, zostanie zgłoszony wyjątek.  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a>Aby ustawić zasadę uniemożliwiającą lokalnej pamięci podręcznej dostarczanie zasobów  
  
- Utwórz zasadę, która uniemożliwia lokalnej pamięci podręcznej dostarczanie żądanych zasobów, ustawiając poziom pamięci podręcznej na <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>. Jeśli żądany zasób znajduje się w pośredniej pamięci podręcznej i zostanie pomyślnie ponownie zweryfikowany, pośrednia pamięć podręczna może dostarczyć żądany zasób.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a>Aby ustawić zasadę uniemożliwiającą dostarczanie żądanych zasobów przez pamięć podręczną  
  
- Utwórz zasadę, która uniemożliwia dostarczanie żądanych zasobów przez <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>pamięć podręczną, ustawiając poziom pamięci podręcznej na . Zasób zwracany przez serwer może być przechowywany w pamięci podręcznej.  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a>Aby ustawić zasadę, która umożliwia dowolnej pamięci podręcznej dostarczanie żądanych zasobów, jeśli zasób na serwerze nie jest nowszy niż kopia buforowana  
  
- Utwórz zasadę, która umożliwia każdej pamięci podręcznej dostarczanie żądanych zasobów, jeśli zasób na <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>serwerze nie jest nowszy niż kopia buforowana, ustawiając poziom pamięci podręcznej na .  
  
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

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [\<requestCaching> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
