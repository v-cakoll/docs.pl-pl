---
title: 'Porady: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1f78f98f94daa51c17a1294285e13dfddd457106
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579767"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="99184-102">Porady: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest</span><span class="sxs-lookup"><span data-stu-id="99184-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="99184-103">W tym przykładzie pokazano, jak zarejestrować protokołu, który określonych classthat zdefiniowanej w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="99184-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="99184-104">W tym przykładzie `CustomWebRequestCreator` jest implementowany przez użytkownika obiekt, który implementuje **Utwórz** metodę, która zwraca `CustomWebRequest` obiektu.</span><span class="sxs-lookup"><span data-stu-id="99184-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="99184-105">Przykład kodu zakłada, że zostały napisane `CustomWebRequest` kod, który implementuje protokołu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="99184-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99184-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="99184-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="99184-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="99184-107">Compiling the Code</span></span>  
 <span data-ttu-id="99184-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="99184-108">This example requires:</span></span>  
  
 <span data-ttu-id="99184-109">Odwołuje się do <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="99184-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99184-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99184-110">See Also</span></span>  
 [<span data-ttu-id="99184-111">Programowanie protokołów podłączanych</span><span class="sxs-lookup"><span data-stu-id="99184-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
