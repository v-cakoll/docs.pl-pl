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
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="fdf7e-102">Instrukcje: określanie zasad pamięci podręcznej na podstawie czasu domyślnego dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="fdf7e-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="fdf7e-103">Domyślna zasada pamięci podręcznej oparta na czasie umożliwia aplikacji zdefiniowanie zachowania pamięci podręcznej przez nagłówki wysyłane za pomocą zasobu w pamięci podręcznej oraz zachowanie pamięci podręcznej zdefiniowane w sekcjach 13 i 14 RFC 2616, dostępne w witrynie internetowej [Internet Engineering Task Force (IETF).](https://www.ietf.org/)</span><span class="sxs-lookup"><span data-stu-id="fdf7e-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="fdf7e-104">Jest to odpowiednie zachowanie pamięci podręcznej dla większości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fdf7e-104">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="fdf7e-105">Aby ustawić domyślną zasadę automatyczną dla aplikacji</span><span class="sxs-lookup"><span data-stu-id="fdf7e-105">To set the default automatic policy for an application</span></span>  
  
1. <span data-ttu-id="fdf7e-106">Utwórz domyślny obiekt zasad oparty na czasie.</span><span class="sxs-lookup"><span data-stu-id="fdf7e-106">Create a default time-based policy object.</span></span>  
  
2. <span data-ttu-id="fdf7e-107">Ustaw obiekt zasad jako domyślny dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fdf7e-107">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdf7e-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="fdf7e-108">Example</span></span>  
 <span data-ttu-id="fdf7e-109">Dwa przykłady w tej sekcji tworzą identyczne zasady.</span><span class="sxs-lookup"><span data-stu-id="fdf7e-109">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="fdf7e-110">Poniższy przykład tworzy domyślną zasadę opartą na czasie i ustawia ją jako domyślną dla domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fdf7e-110">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="fdf7e-111">Można również utworzyć domyślne zasady pamięci <xref:System.Net.Cache.RequestCachePolicy> podręcznej oparte na czasie przy użyciu klasy, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fdf7e-111">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fdf7e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fdf7e-112">See also</span></span>

- [<span data-ttu-id="fdf7e-113">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="fdf7e-113">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="fdf7e-114">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="fdf7e-114">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="fdf7e-115">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="fdf7e-115">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="fdf7e-116">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="fdf7e-116">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="fdf7e-117">\<requestCaching> Element (Ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="fdf7e-117">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
