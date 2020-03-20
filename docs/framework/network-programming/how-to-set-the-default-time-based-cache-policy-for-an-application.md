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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048094"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>Instrukcje: określanie zasad pamięci podręcznej na podstawie czasu domyślnego dla aplikacji
Domyślna zasada pamięci podręcznej oparta na czasie umożliwia aplikacji zdefiniowanie zachowania pamięci podręcznej przez nagłówki wysyłane za pomocą zasobu w pamięci podręcznej oraz zachowanie pamięci podręcznej zdefiniowane w sekcjach 13 i 14 RFC 2616, dostępne w witrynie internetowej [Internet Engineering Task Force (IETF).](https://www.ietf.org/) Jest to odpowiednie zachowanie pamięci podręcznej dla większości aplikacji.  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>Aby ustawić domyślną zasadę automatyczną dla aplikacji  
  
1. Utwórz domyślny obiekt zasad oparty na czasie.  
  
2. Ustaw obiekt zasad jako domyślny dla domeny aplikacji.  
  
## <a name="example"></a>Przykład  
 Dwa przykłady w tej sekcji tworzą identyczne zasady.  
  
 Poniższy przykład tworzy domyślną zasadę opartą na czasie i ustawia ją jako domyślną dla domeny aplikacji.  
  
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
  
 Można również utworzyć domyślne zasady pamięci <xref:System.Net.Cache.RequestCachePolicy> podręcznej oparte na czasie przy użyciu klasy, jak pokazano w poniższym przykładzie:  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](cache-management-for-network-applications.md)
- [Zasady pamięci podręcznej](cache-policy.md)
- [Zasady pamięci podręcznej oparte na lokalizacji](location-based-cache-policies.md)
- [Zasady pamięci podręcznej oparte na czasie](time-based-cache-policies.md)
- [\<requestCaching> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
