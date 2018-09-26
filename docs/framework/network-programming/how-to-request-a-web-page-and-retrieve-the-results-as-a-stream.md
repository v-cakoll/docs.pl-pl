---
title: 'Instrukcje: żądanie strony internetowej i pobieranie wyników jako Stream'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2ceaa7cbaf2035276a0ba0105f3969f0249c6132
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084933"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="46513-102">Instrukcje: żądanie strony internetowej i pobieranie wyników jako Stream</span><span class="sxs-lookup"><span data-stu-id="46513-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="46513-103">W tym przykładzie pokazano, jak żądania strony sieci Web do pobierania wyników w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="46513-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46513-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="46513-104">Example</span></span>  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="46513-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="46513-105">Compiling the Code</span></span>  
 <span data-ttu-id="46513-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="46513-106">This example requires:</span></span>  
  
-   <span data-ttu-id="46513-107">Odwołuje się do <xref:System.IO> i <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="46513-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46513-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46513-108">See Also</span></span>  
 [<span data-ttu-id="46513-109">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="46513-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
