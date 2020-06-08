---
title: 'Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest'
description: Dowiedz się, jak pobrać WebResponse specyficzny dla protokołu, który jest zgodny z żądaniem WebRequest w .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 15b1912a7bd951df7f3c14eb96251c2bdf237b4f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502460"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="6543e-103">Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest</span><span class="sxs-lookup"><span data-stu-id="6543e-103">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="6543e-104">Ten przykład pokazuje, jak pobrać WebResponse specyficzne dla protokołu, które pasują do żądania WebRequest.</span><span class="sxs-lookup"><span data-stu-id="6543e-104">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6543e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6543e-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6543e-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6543e-106">Compiling the Code</span></span>  
 <span data-ttu-id="6543e-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6543e-107">This example requires:</span></span>  
  
- <span data-ttu-id="6543e-108">Odwołania do przestrzeni nazw **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="6543e-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6543e-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6543e-109">See also</span></span>

- [<span data-ttu-id="6543e-110">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="6543e-110">Requesting Data</span></span>](requesting-data.md)
