---
title: 'Instrukcje: określanie zasad pamięci podręcznej na podstawie czasu domyślnego dla aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: a50cfd60bb44dc4b4af3ffe8d2fc73f41e645c07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098607"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>Instrukcje: określanie zasad pamięci podręcznej na podstawie czasu domyślnego dla aplikacji
Domyślne zasady pamięci podręcznej na podstawie czasu umożliwia aplikacji jej zachowanie pamięci podręcznej, zdefiniowany przez nagłówki wysyłane z pamięci podręcznej zasobów i zachowanie pamięci podręcznej, zdefiniowane w sekcji 13 i 14 dokumencie RFC 2616, dostępne pod adresem [(Internet Engineering Task Force IETF)](https://www.ietf.org/) witryny sieci Web. Jest to zachowanie pamięci podręcznej odpowiedniej dla większości aplikacji.  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>Aby ustawić domyślną zasadę automatycznego dla aplikacji  
  
1.  Utwórz obiekt zasad na podstawie czasu domyślnego.  
  
2.  Obiekt zasad należy ustawić jako domyślne dla domeny aplikacji.  
  
## <a name="example"></a>Przykład  
 Dwa przykłady w tej sekcji produktu identycznymi zasadami.  
  
 Poniższy przykład tworzy domyślne zasady oparte na czasie i ustawia go jako domyślnej domeny aplikacji.  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 Możesz również tworzyć, używając zasad pamięci podręcznej na podstawie czasu domyślnego <xref:System.Net.Cache.RequestCachePolicy> klasy, jak pokazano w poniższym przykładzie:  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [\<requestCaching — >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
