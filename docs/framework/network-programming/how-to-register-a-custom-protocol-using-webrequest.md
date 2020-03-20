---
title: 'Instrukcje: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 05b6f6c3f0f1fc1b36b60e8b0dae50de2826aba4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048250"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="b0abd-102">Instrukcje: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest</span><span class="sxs-lookup"><span data-stu-id="b0abd-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="b0abd-103">W tym przykładzie pokazano, jak zarejestrować klasę określonego protokołu, który jest zdefiniowany w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="b0abd-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="b0abd-104">W tym `CustomWebRequestCreator` przykładzie jest obiekt zaimplementowany przez użytkownika, który implementuje **Create** metoda, która zwraca `CustomWebRequest` obiekt.</span><span class="sxs-lookup"><span data-stu-id="b0abd-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="b0abd-105">Przykładowy kod zakłada, że napisano `CustomWebRequest` kod, który implementuje protokół niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="b0abd-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0abd-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0abd-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b0abd-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b0abd-107">Compiling the Code</span></span>  
 <span data-ttu-id="b0abd-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b0abd-108">This example requires:</span></span>  
  
 <span data-ttu-id="b0abd-109">Odwołania do <xref:System.Net> obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="b0abd-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0abd-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0abd-110">See also</span></span>

- [<span data-ttu-id="b0abd-111">Programowanie protokołów podłączanych</span><span class="sxs-lookup"><span data-stu-id="b0abd-111">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
