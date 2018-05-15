---
title: 'Porady: ustawienie zasad pamięci podręcznej na żądanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- request cache policies
ms.assetid: 39c15e40-586b-4ac9-9cce-146f74b7e545
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 98cd64aaab66d69c29c022d770b34bb0efdb4bef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-cache-policy-for-a-request"></a><span data-ttu-id="b3bfe-102">Porady: ustawienie zasad pamięci podręcznej na żądanie</span><span class="sxs-lookup"><span data-stu-id="b3bfe-102">How to: Set Cache Policy for a Request</span></span>
<span data-ttu-id="b3bfe-103">W poniższym przykładzie pokazano, ustawienie zasady pamięci podręcznej dla żądania.</span><span class="sxs-lookup"><span data-stu-id="b3bfe-103">The following example demonstrates setting a cache policy for a request.</span></span> <span data-ttu-id="b3bfe-104">Przykład danych wejściowych jest identyfikatorem URI, takich jak http://www.contoso.com/.</span><span class="sxs-lookup"><span data-stu-id="b3bfe-104">The example input is a URI such as http://www.contoso.com/.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3bfe-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3bfe-105">Example</span></span>  
 <span data-ttu-id="b3bfe-106">Poniższy przykład kodu tworzy zasady pamięci podręcznej, który umożliwia żądany zasób ma być używany z pamięci podręcznej, jeśli nie był w pamięci podręcznej przez czas dłuższy niż jeden dzień.</span><span class="sxs-lookup"><span data-stu-id="b3bfe-106">The following code example creates a cache policy that allows the requested resource to be used from the cache if it has not been in the cache for longer than one day.</span></span> <span data-ttu-id="b3bfe-107">Przykład wyświetla komunikat informujący o tym, czy zasób został użyty z pamięci podręcznej — na przykład `"The response was retrieved from the cache : False."`— a następnie wyświetla zasobu.</span><span class="sxs-lookup"><span data-stu-id="b3bfe-107">The example displays a message that indicates whether the resource was used from the cache—for example, `"The response was retrieved from the cache : False."`—and then displays the resource.</span></span> <span data-ttu-id="b3bfe-108">Żądania mogą być spełnione przez dowolnego pamięci podręcznej między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="b3bfe-108">A request can be fulfilled by any cache between the client and server.</span></span>  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Cache;  
using System.IO;  
  
namespace Examples.System.Net.Cache  
{  
    public class CacheExample  
    {     
        public static void UseCacheForOneDay(Uri resource)  
        {  
            // Create a policy that allows items in the cache  
            // to be used if they have been cached one day or less.  
            HttpRequestCachePolicy requestPolicy =   
                new HttpRequestCachePolicy (HttpCacheAgeControl.MaxAge,  
                TimeSpan.FromDays(1));  
  
            WebRequest request = WebRequest.Create (resource);  
            // Set the policy for this request only.  
            request.CachePolicy = requestPolicy;  
            HttpWebResponse response = (HttpWebResponse)request.GetResponse();  
            // Determine whether the response was retrieved from the cache.  
            Console.WriteLine ("The response was retrieved from the cache : {0}.",  
               response.IsFromCache);  
            Stream s = response.GetResponseStream ();  
            StreamReader reader = new StreamReader (s);  
            // Display the requested resource.  
            Console.WriteLine(reader.ReadToEnd());  
            reader.Close ();  
            s.Close();  
            response.Close();  
        }  
        public static void Main(string[] args)  
        {  
            if (args == null || args.Length != 1)  
            {  
                Console.WriteLine ("You must specify the URI to retrieve.");  
                return;  
            }  
            UseCacheForOneDay (new Uri(args[0]));  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Cache  
Imports System.IO  
Namespace Examples.System.Net.Cache  
    Public Class CacheExample  
        Public Shared Sub UseCacheForOneDay(ByVal resource As Uri)  
            ' Create a policy that allows items in the cache  
            ' to be used if they have been cached one day or less.  
            Dim requestPolicy As New HttpRequestCachePolicy _  
                  (HttpCacheAgeControl.MaxAge, TimeSpan.FromDays(1))  
            Dim request As WebRequest = WebRequest.Create(resource)  
            ' Set the policy for this request only.  
            request.CachePolicy = requestPolicy  
            Dim response As HttpWebResponse = _  
             CType(request.GetResponse(), HttpWebResponse)  
            ' Determine whether the response was retrieved from the cache.  
            Console.WriteLine("The response was retrieved from the cache : {0}.", _  
                response.IsFromCache)  
            Dim s As Stream = response.GetResponseStream()  
            Dim reader As New StreamReader(s)  
            ' Display the requested resource.  
            Console.WriteLine(reader.ReadToEnd())  
            reader.Close()  
            s.Close()  
            response.Close()  
        End Sub  
        Public Shared Sub Main(ByVal args() As String)  
            If args Is Nothing OrElse args.Length <> 1 Then  
                Console.WriteLine("You must specify the URI to retrieve.")  
                Return  
            End If  
            UseCacheForOneDay(New Uri(args(0)))  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3bfe-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3bfe-109">See Also</span></span>  
 [<span data-ttu-id="b3bfe-110">Zarządzanie pamięcią podręczną dla aplikacji sieciowych</span><span class="sxs-lookup"><span data-stu-id="b3bfe-110">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="b3bfe-111">Zasady pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="b3bfe-111">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="b3bfe-112">Zasady pamięci podręcznej oparte na lokalizacji</span><span class="sxs-lookup"><span data-stu-id="b3bfe-112">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="b3bfe-113">Zasady pamięci podręcznej oparte na czasie</span><span class="sxs-lookup"><span data-stu-id="b3bfe-113">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="b3bfe-114">\<requestCaching — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="b3bfe-114">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
