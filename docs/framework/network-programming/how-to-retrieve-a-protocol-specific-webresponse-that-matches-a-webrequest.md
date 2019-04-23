---
title: 'Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: fee2b725afbceef45b9651a7cd88a61b37952e32
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087381"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="13db0-102">Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest</span><span class="sxs-lookup"><span data-stu-id="13db0-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="13db0-103">W tym przykładzie pokazano, jak można pobrać elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest.</span><span class="sxs-lookup"><span data-stu-id="13db0-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13db0-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="13db0-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="13db0-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="13db0-105">Compiling the Code</span></span>  
 <span data-ttu-id="13db0-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="13db0-106">This example requires:</span></span>  
  
-   <span data-ttu-id="13db0-107">Odwołuje się do **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="13db0-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13db0-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13db0-108">See also</span></span>

- [<span data-ttu-id="13db0-109">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="13db0-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
