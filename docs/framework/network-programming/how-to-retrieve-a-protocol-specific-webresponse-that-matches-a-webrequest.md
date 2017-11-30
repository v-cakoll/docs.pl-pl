---
title: "Porady: pobieranie WebResponse specyficzne dla protokołu, który odpowiada WebRequest"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cbf6b6eab3502f8f04f33f6f11d5d071e3406a7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="d5846-102">Porady: pobieranie WebResponse specyficzne dla protokołu, który odpowiada WebRequest</span><span class="sxs-lookup"><span data-stu-id="d5846-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="d5846-103">W tym przykładzie pokazano, jak pobrać WebResponse specyficzne dla protokołu, który odpowiada WebRequest.</span><span class="sxs-lookup"><span data-stu-id="d5846-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5846-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5846-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d5846-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d5846-105">Compiling the Code</span></span>  
 <span data-ttu-id="d5846-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="d5846-106">This example requires:</span></span>  
  
-   <span data-ttu-id="d5846-107">Odwołuje się do **System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d5846-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5846-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5846-108">See Also</span></span>  
 [<span data-ttu-id="d5846-109">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="d5846-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
