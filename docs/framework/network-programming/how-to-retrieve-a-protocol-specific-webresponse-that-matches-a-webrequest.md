---
title: 'Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 0cb2d11306f52df767d8c053e8ab745696bb8e47
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048140"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="af992-102">Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest</span><span class="sxs-lookup"><span data-stu-id="af992-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="af992-103">Ten przykład pokazuje, jak pobrać WebResponse specyficzne dla protokołu, które pasują do żądania WebRequest.</span><span class="sxs-lookup"><span data-stu-id="af992-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af992-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="af992-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="af992-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="af992-105">Compiling the Code</span></span>  
 <span data-ttu-id="af992-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="af992-106">This example requires:</span></span>  
  
- <span data-ttu-id="af992-107">Odwołania do przestrzeni nazw **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="af992-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af992-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af992-108">See also</span></span>

- [<span data-ttu-id="af992-109">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="af992-109">Requesting Data</span></span>](requesting-data.md)
