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
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="5afc2-102">Instrukcje: określanie zasad pamięci podręcznej na podstawie czasu domyślnego dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="5afc2-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="5afc2-103">Domyślne zasady pamięci podręcznej na podstawie czasu umożliwia aplikacji jej zachowanie pamięci podręcznej, zdefiniowany przez nagłówki wysyłane z pamięci podręcznej zasobów i zachowanie pamięci podręcznej, zdefiniowane w sekcji 13 i 14 dokumencie RFC 2616, dostępne pod adresem [(Internet Engineering Task Force IETF)](https://www.ietf.org/) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5afc2-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="5afc2-104">Jest to zachowanie pamięci podręcznej odpowiedniej dla większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5afc2-104">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="5afc2-105">Aby ustawić domyślną zasadę automatycznego dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="5afc2-105">To set the default automatic policy for an application</span></span>  
  
1.  <span data-ttu-id="5afc2-106">Utwórz obiekt zasad na podstawie czasu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="5afc2-106">Create a default time-based policy object.</span></span>  
  
2.  <span data-ttu-id="5afc2-107">Obiekt zasad należy ustawić jako domyślne dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5afc2-107">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5afc2-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5afc2-108">Example</span></span>  
 <span data-ttu-id="5afc2-109">Dwa przykłady w tej sekcji produktu identycznymi zasadami.</span><span class="sxs-lookup"><span data-stu-id="5afc2-109">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="5afc2-110">Poniższy przykład tworzy domyślne zasady oparte na czasie i ustawia go jako domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5afc2-110">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="5afc2-111">Możesz również tworzyć, używając zasad pamięci podręcznej na podstawie czasu domyślnego <xref:System.Net.Cache.RequestCachePolicy> klasy, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="5afc2-111">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5afc2-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5afc2-112">See also</span></span>

- [<span data-ttu-id="5afc2-113">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="5afc2-113">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="5afc2-114">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="5afc2-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="5afc2-115">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="5afc2-115">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="5afc2-116">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="5afc2-116">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="5afc2-117">\<requestCaching — >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="5afc2-117">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
