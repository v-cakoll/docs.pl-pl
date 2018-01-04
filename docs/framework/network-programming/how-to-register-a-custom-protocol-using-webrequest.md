---
title: "Porady: rejestrowanie przy użyciu WebRequest protokołu niestandardowego"
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
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7fefaf65fe0bf1c761e976359f3015389a557369
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="82e5d-102">Porady: rejestrowanie przy użyciu WebRequest protokołu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="82e5d-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="82e5d-103">Ten przykład przedstawia sposób rejestrowania protokołu, który określonych classthat jest zdefiniowany w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="82e5d-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="82e5d-104">W tym przykładzie `CustomWebRequestCreator` jest implementowany przez użytkownika obiekt, który implementuje **Utwórz** metodę zwracającą `CustomWebRequest` obiektu.</span><span class="sxs-lookup"><span data-stu-id="82e5d-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="82e5d-105">Przykład kodu zakłada, że można zapisywać `CustomWebRequest` kodu, który implementuje ten protokół niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="82e5d-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82e5d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="82e5d-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="82e5d-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="82e5d-107">Compiling the Code</span></span>  
 <span data-ttu-id="82e5d-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="82e5d-108">This example requires:</span></span>  
  
 <span data-ttu-id="82e5d-109">Odwołuje się do <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="82e5d-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e5d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82e5d-110">See Also</span></span>  
 [<span data-ttu-id="82e5d-111">Programowanie protokołów podłączanych</span><span class="sxs-lookup"><span data-stu-id="82e5d-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
