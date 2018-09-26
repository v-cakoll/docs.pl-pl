---
title: 'Porady: Określanie zasad pamięci podręcznej na podstawie czasu domyślnego dla aplikacji'
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
ms.openlocfilehash: 1e08026f8d1ec8b39f7ef3c2c34efad9e51b8fe9
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074891"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="c1d1c-102">Porady: Określanie zasad pamięci podręcznej na podstawie czasu domyślnego dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="c1d1c-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="c1d1c-103">Domyślne zasady pamięci podręcznej na podstawie czasu umożliwia aplikacji jej zachowanie pamięci podręcznej, zdefiniowany przez nagłówki wysyłane z pamięci podręcznej zasobów i zachowanie pamięci podręcznej, zdefiniowane w sekcji 13 i 14 dokumencie RFC 2616, dostępne pod adresem [ http://www.ietf.org ](http://www.ietf.org/). Jest to zachowanie pamięci podręcznej odpowiedniej dla większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c1d1c-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/). This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="c1d1c-104">Aby ustawić domyślną zasadę automatycznego dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="c1d1c-104">To set the default automatic policy for an application</span></span>  
  
1.  <span data-ttu-id="c1d1c-105">Utwórz obiekt zasad na podstawie czasu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="c1d1c-105">Create a default time-based policy object.</span></span>  
  
2.  <span data-ttu-id="c1d1c-106">Obiekt zasad należy ustawić jako domyślne dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c1d1c-106">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1d1c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1d1c-107">Example</span></span>  
 <span data-ttu-id="c1d1c-108">Dwa przykłady w tej sekcji produktu identycznymi zasadami.</span><span class="sxs-lookup"><span data-stu-id="c1d1c-108">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="c1d1c-109">Poniższy przykład tworzy domyślne zasady oparte na czasie i ustawia go jako domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c1d1c-109">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="c1d1c-110">Możesz również tworzyć, używając zasad pamięci podręcznej na podstawie czasu domyślnego <xref:System.Net.Cache.RequestCachePolicy> klasy, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c1d1c-110">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1d1c-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1d1c-111">See Also</span></span>  
 [<span data-ttu-id="c1d1c-112">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="c1d1c-112">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="c1d1c-113">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="c1d1c-113">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="c1d1c-114">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="c1d1c-114">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="c1d1c-115">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="c1d1c-115">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="c1d1c-116">\<requestCaching — >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="c1d1c-116">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
