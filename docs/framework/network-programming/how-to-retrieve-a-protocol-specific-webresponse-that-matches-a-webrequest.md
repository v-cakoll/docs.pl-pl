---
title: 'Porady: Pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2a72e57156903c9d436a49aaf6da596868af4003
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074662"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="3b239-102">Porady: Pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest</span><span class="sxs-lookup"><span data-stu-id="3b239-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="3b239-103">W tym przykładzie pokazano, jak można pobrać elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest.</span><span class="sxs-lookup"><span data-stu-id="3b239-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b239-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b239-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3b239-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3b239-105">Compiling the Code</span></span>  
 <span data-ttu-id="3b239-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="3b239-106">This example requires:</span></span>  
  
-   <span data-ttu-id="3b239-107">Odwołuje się do **przestrzeni nazw System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3b239-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b239-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b239-108">See Also</span></span>  
 [<span data-ttu-id="3b239-109">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="3b239-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
