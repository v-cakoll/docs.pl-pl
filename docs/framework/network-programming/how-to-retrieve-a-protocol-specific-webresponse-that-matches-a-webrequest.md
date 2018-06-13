---
title: 'Porady: pobieranie WebResponse specyficzne dla protokołu, który odpowiada WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d15b63482cb37fa986dd065beefcf6baee4c8312
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394215"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="37e1a-102">Porady: pobieranie WebResponse specyficzne dla protokołu, który odpowiada WebRequest</span><span class="sxs-lookup"><span data-stu-id="37e1a-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="37e1a-103">W tym przykładzie pokazano, jak pobrać WebResponse specyficzne dla protokołu, który odpowiada WebRequest.</span><span class="sxs-lookup"><span data-stu-id="37e1a-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37e1a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="37e1a-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="37e1a-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="37e1a-105">Compiling the Code</span></span>  
 <span data-ttu-id="37e1a-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="37e1a-106">This example requires:</span></span>  
  
-   <span data-ttu-id="37e1a-107">Odwołuje się do **System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="37e1a-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e1a-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37e1a-108">See Also</span></span>  
 [<span data-ttu-id="37e1a-109">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="37e1a-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
