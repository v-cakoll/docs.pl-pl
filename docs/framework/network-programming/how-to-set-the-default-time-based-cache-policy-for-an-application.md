---
title: "Porady: ustawienie domyślnych zasad na podstawie czasu pamięci podręcznej dla aplikacji"
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
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1d5166090a0682b71f74565e666c96ddadb7c6c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>Porady: ustawienie domyślnych zasad na podstawie czasu pamięci podręcznej dla aplikacji
Domyślne zasady na podstawie czasu pamięci podręcznej umożliwia aplikacji zachowują się jego pamięci podręcznej zdefiniowany przez nagłówki wysyłane z pamięci podręcznej zasobów i zachowanie pamięci podręcznej określonych w sekcji 13 i 14 RFC 2616 dostępne pod adresem [http://www.ietf.org](http://www.ietf.org/). Jest to zachowanie pamięci podręcznej właściwe dla większości aplikacji.  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>Aby ustawić domyślną zasadę automatycznego dla aplikacji  
  
1.  Utwórz obiekt domyślne zasady oparte na czasie.  
  
2.  Ustaw ten obiekt zasad jako domyślnej domeny aplikacji.  
  
## <a name="example"></a>Przykład  
 Dwa przykłady w tej sekcji utworzyć identycznymi zasadami.  
  
 Poniższy przykład tworzy domyślne zasady na podstawie czasu i ustawia go jako domyślny dla tej domeny aplikacji.  
  
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
  
 Można również utworzyć w domyślnej na podstawie czasu pamięci podręcznej zasad przy użyciu <xref:System.Net.Cache.RequestCachePolicy> klasy, jak pokazano w poniższym przykładzie:  
  
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
 [Zarządzanie pamięcią podręczną dla aplikacji sieciowych](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [Zasady pamięci podręcznej](../../../docs/framework/network-programming/cache-policy.md)  
 [Zasady pamięci podręcznej oparte na lokalizacji](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [Zasady pamięci podręcznej oparte na czasie](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [\<requestCaching — > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
