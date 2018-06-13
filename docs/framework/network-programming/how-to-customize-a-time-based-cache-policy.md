---
title: 'Porady: Dostosowywanie zasad na podstawie czasu pamięci podręcznej'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fd2856ffcf6b21ba34771c231f608ad725b21763
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390968"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a>Porady: Dostosowywanie zasad na podstawie czasu pamięci podręcznej
Podczas tworzenia zasady na podstawie czasu pamięci podręcznej, można dostosować zachowanie buforowania, określając wartości maksymalny wiek, minimalna świeżości, maksymalna nieaktualności lub Data synchronizacji pamięci podręcznej. <xref:System.Net.Cache.HttpRequestCachePolicy> Obiektu zawiera kilka konstruktorów, które pozwalają określić prawidłową kombinację tych wartości.  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>Aby utworzyć zasady na podstawie czasu pamięci podręcznej, który używa Data synchronizacji pamięci podręcznej  
  
-   Utwórz zasadę na podstawie czasu pamięci podręcznej, która używa Data synchronizacji pamięci podręcznej przez przekazanie <xref:System.DateTime> do obiektu <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktora.  
  
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
  
 Wynik jest podobny do następującego:  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>Aby utworzyć zasady na podstawie czasu pamięci podręcznej, która jest oparta na minimalną świeżości  
  
-   Utwórz zasadę na podstawie czasu pamięci podręcznej, która jest oparta na minimalną świeżości, określając <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> jako `cacheAgeControl` wartość parametru i przekazywanie <xref:System.TimeSpan> do obiektu <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktora.  
  
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
  
 Aby uzyskać następujące wywołanie:  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>Aby utworzyć zasady na podstawie czasu pamięci podręcznej, która na podstawie świeżości minimalny i maksymalny wiek  
  
-   Utwórz zasadę na podstawie czasu pamięci podręcznej, która na podstawie świeżości minimalny i maksymalny wiek, określając <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> jako `cacheAgeControl` wartość parametru i przekazywanie dwa <xref:System.TimeSpan> obiekty do <xref:System.Net.Cache.HttpRequestCachePolicy> konstruktora, aby określić okres ważności zasoby oraz określ minimalną świeżości drugiego dozwolony dla obiektu zwróconego z pamięci podręcznej.  
  
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
  
 Aby uzyskać następujące wywołanie:  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [\<requestCaching — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
