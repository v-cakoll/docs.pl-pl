---
title: 'Instrukcje: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 5c9a81fc61a2272056ba34fa387fdafee6203824
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642558"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="e56b4-102">Instrukcje: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest</span><span class="sxs-lookup"><span data-stu-id="e56b4-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="e56b4-103">Ten przykład pokazuje, jak zarejestrować klasy określonego protokołu, który jest zdefiniowany w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="e56b4-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="e56b4-104">W tym przykładzie `CustomWebRequestCreator` jest implementowany przez użytkownika obiekt, który implementuje **Utwórz** metodę, która zwraca `CustomWebRequest` obiektu.</span><span class="sxs-lookup"><span data-stu-id="e56b4-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="e56b4-105">Przykład kodu zakłada, że zostały napisane `CustomWebRequest` kod, który implementuje protokołu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="e56b4-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e56b4-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="e56b4-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e56b4-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e56b4-107">Compiling the Code</span></span>  
 <span data-ttu-id="e56b4-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e56b4-108">This example requires:</span></span>  
  
 <span data-ttu-id="e56b4-109">Odwołuje się do <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e56b4-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e56b4-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e56b4-110">See also</span></span>

- [<span data-ttu-id="e56b4-111">Programowanie protokołów podłączanych</span><span class="sxs-lookup"><span data-stu-id="e56b4-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
