---
title: 'Instrukcje: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 05b6f6c3f0f1fc1b36b60e8b0dae50de2826aba4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048250"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="abc01-102">Instrukcje: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest</span><span class="sxs-lookup"><span data-stu-id="abc01-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="abc01-103">Ten przykład pokazuje, jak zarejestrować klasę specyficzną dla protokołu, która została zdefiniowana w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="abc01-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="abc01-104">W tym przykładzie `CustomWebRequestCreator` jest obiektem implementowanym przez użytkownika, który implementuje `CustomWebRequest` metodę Create, która zwraca obiekt.</span><span class="sxs-lookup"><span data-stu-id="abc01-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="abc01-105">W przykładzie kodu założono, że Zapisano `CustomWebRequest` kod implementujący niestandardowy protokół.</span><span class="sxs-lookup"><span data-stu-id="abc01-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abc01-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="abc01-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="abc01-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="abc01-107">Compiling the Code</span></span>  
 <span data-ttu-id="abc01-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="abc01-108">This example requires:</span></span>  
  
 <span data-ttu-id="abc01-109">Odwołania do <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="abc01-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc01-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abc01-110">See also</span></span>

- [<span data-ttu-id="abc01-111">Programowanie protokołów podłączanych</span><span class="sxs-lookup"><span data-stu-id="abc01-111">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
