---
title: 'Porady: ustawienie domyślnych zasad na podstawie czasu pamięci podręcznej dla aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 021a13b9124cf54712643e33cbf0ca77ec828b27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396675"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="21742-102">Porady: ustawienie domyślnych zasad na podstawie czasu pamięci podręcznej dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="21742-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="21742-103">Domyślne zasady na podstawie czasu pamięci podręcznej umożliwia aplikacji zachowują się jego pamięci podręcznej zdefiniowany przez nagłówki wysyłane z pamięci podręcznej zasobów i zachowanie pamięci podręcznej określonych w sekcji 13 i 14 RFC 2616 dostępne pod adresem [ http://www.ietf.org ](http://www.ietf.org/). Jest to zachowanie pamięci podręcznej właściwe dla większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21742-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/). This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="21742-104">Aby ustawić domyślną zasadę automatycznego dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="21742-104">To set the default automatic policy for an application</span></span>  
  
1.  <span data-ttu-id="21742-105">Utwórz obiekt domyślne zasady oparte na czasie.</span><span class="sxs-lookup"><span data-stu-id="21742-105">Create a default time-based policy object.</span></span>  
  
2.  <span data-ttu-id="21742-106">Ustaw ten obiekt zasad jako domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21742-106">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21742-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="21742-107">Example</span></span>  
 <span data-ttu-id="21742-108">Dwa przykłady w tej sekcji utworzyć identycznymi zasadami.</span><span class="sxs-lookup"><span data-stu-id="21742-108">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="21742-109">Poniższy przykład tworzy domyślne zasady na podstawie czasu i ustawia go jako domyślny dla tej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21742-109">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="21742-110">Można również utworzyć w domyślnej na podstawie czasu pamięci podręcznej zasad przy użyciu <xref:System.Net.Cache.RequestCachePolicy> klasy, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="21742-110">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21742-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21742-111">See Also</span></span>  
 [<span data-ttu-id="21742-112">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="21742-112">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="21742-113">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="21742-113">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="21742-114">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="21742-114">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="21742-115">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="21742-115">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="21742-116">\<requestCaching — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="21742-116">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
