---
title: 'Instrukcje: dostosowywanie zasad pamięci podręcznej na podstawie czasu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: d4a35882d99a87ca5bf22fb386a87158e3c2d664
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154573"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a>Instrukcje: dostosowywanie zasad pamięci podręcznej na podstawie czasu
Podczas tworzenia zasad pamięci podręcznej na podstawie czasu, można dostosować zachowanie buforowania, określając wartości maksymalny wiek, minimalna świeżość, maksymalna nieaktualność lub Data synchronizacji pamięci podręcznej. <xref:System.Net.Cache.HttpRequestCachePolicy> Obiekt zawiera kilka konstruktorów, które pozwalają na określenie prawidłowe kombinacje tych wartości.  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Aby utworzyć zasady na podstawie czasu pamięci podręcznej, który używa Data synchronizacji pamięci podręcznej  
  
-   Utwórz zasadę pamięci podręcznej na podstawie czasu, która używa Data synchronizacji pamięci podręcznej, przekazując <xref:System.DateTime> obiekt <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktora.  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(when);  
        Console.WriteLine("When: {0}", when);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy([when])  
        Console.WriteLine("When: {0}", [when])  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 Rezultat jest podobny do następującego:  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Aby utworzyć zasady na podstawie czasu pamięci podręcznej, które opiera się na minimalna świeżość  
  
-   Tworzenie zasad pamięci podręcznej na podstawie czasu, który opiera się na minimalna świeżość, określając <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> jako `cacheAgeControl` wartość parametru i przekazywanie <xref:System.TimeSpan> obiekt <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktora.  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 Następujące wywołania:  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>Aby utworzyć zasady na podstawie czasu pamięci podręcznej, które jest na podstawie świeżości minimalny i maksymalny wiek  
  
-   Utwórz zasadę pamięci podręcznej na podstawie czasu, która opiera się na świeżości minimalny i maksymalny wiek, określając <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> jako `cacheAgeControl` wartość parametru i przekazywanie dwóch <xref:System.TimeSpan> obiekty do <xref:System.Net.Cache.HttpRequestCachePolicy> Konstruktor, aby określić maksymalny wiek zasoby i chwilę, aby określić minimalna świeżość dozwolony dla obiektu zwróconego z pamięci podręcznej.  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)  
    {  
        HttpRequestCachePolicy policy =   
        new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);  
        Console.WriteLine(policy.ToString());  
        return policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy  
        Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)  
        Console.WriteLine(policy.ToString())  
        Return policy  
    End Function  
    ```  
  
 Następujące wywołania:  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [\<requestCaching — >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
