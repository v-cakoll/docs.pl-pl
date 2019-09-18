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
ms.openlocfilehash: 0aaa26f67ef1ef191060e682690fa14de328b812
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048094"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>Instrukcje: określanie zasad pamięci podręcznej na podstawie czasu domyślnego dla aplikacji
Domyślne zasady pamięci podręcznej oparte na czasie umożliwiają aplikacji zachowanie pamięci podręcznej zdefiniowanej przez nagłówki wysyłane z buforowanym zasobem, a zachowanie pamięci podręcznej zdefiniowane w sekcjach 13 i 14 RFC 2616, dostępne w [sieci Internet Engineering Task Force (IETF)](https://www.ietf.org/) producenta. Jest to odpowiednie zachowanie pamięci podręcznej dla większości aplikacji.  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>Aby ustawić domyślne zasady automatyczne dla aplikacji  
  
1. Utwórz domyślny obiekt zasad oparty na czasie.  
  
2. Ustaw obiekt zasad jako domyślny dla domeny aplikacji.  
  
## <a name="example"></a>Przykład  
 Dwa przykłady w tej sekcji generują identyczne zasady.  
  
 Poniższy przykład tworzy domyślne zasady oparte na czasie i ustawia je jako domyślne dla domeny aplikacji.  
  
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
  
 Możesz również utworzyć domyślne zasady pamięci podręcznej oparte na czasie za <xref:System.Net.Cache.RequestCachePolicy> pomocą klasy, jak pokazano w następującym przykładzie:  
  
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

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [\<requestCaching >, element (Ustawienia sieci)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
