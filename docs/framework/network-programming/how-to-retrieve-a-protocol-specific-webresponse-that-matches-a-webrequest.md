---
title: 'Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: fee2b725afbceef45b9651a7cd88a61b37952e32
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642519"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="e4933-102">Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest</span><span class="sxs-lookup"><span data-stu-id="e4933-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="e4933-103">W tym przykładzie pokazano, jak można pobrać elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest.</span><span class="sxs-lookup"><span data-stu-id="e4933-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4933-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4933-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e4933-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e4933-105">Compiling the Code</span></span>  
 <span data-ttu-id="e4933-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e4933-106">This example requires:</span></span>  
  
- <span data-ttu-id="e4933-107">Odwołuje się do **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e4933-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4933-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4933-108">See also</span></span>

- [<span data-ttu-id="e4933-109">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="e4933-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
