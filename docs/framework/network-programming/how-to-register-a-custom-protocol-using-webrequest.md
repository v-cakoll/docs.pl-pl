---
title: 'Porady: rejestrowanie przy użyciu WebRequest protokołu niestandardowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e6902adeac04d95d576ae72469624a5b4f8aa0c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394595"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="68b1e-102">Porady: rejestrowanie przy użyciu WebRequest protokołu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="68b1e-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="68b1e-103">Ten przykład przedstawia sposób rejestrowania protokołu, który określonych classthat jest zdefiniowany w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="68b1e-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="68b1e-104">W tym przykładzie `CustomWebRequestCreator` jest implementowany przez użytkownika obiekt, który implementuje **Utwórz** metodę zwracającą `CustomWebRequest` obiektu.</span><span class="sxs-lookup"><span data-stu-id="68b1e-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="68b1e-105">Przykład kodu zakłada, że można zapisywać `CustomWebRequest` kodu, który implementuje ten protokół niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="68b1e-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68b1e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="68b1e-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="68b1e-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="68b1e-107">Compiling the Code</span></span>  
 <span data-ttu-id="68b1e-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="68b1e-108">This example requires:</span></span>  
  
 <span data-ttu-id="68b1e-109">Odwołuje się do <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="68b1e-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68b1e-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68b1e-110">See Also</span></span>  
 [<span data-ttu-id="68b1e-111">Programowanie protokołów podłączanych</span><span class="sxs-lookup"><span data-stu-id="68b1e-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
