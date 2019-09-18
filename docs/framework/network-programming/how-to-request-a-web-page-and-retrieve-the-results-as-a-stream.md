---
title: 'Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: b3d24a958ec93084d03d2ad2e0eb6d9d2507e155
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048176"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="bbf23-102">Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia</span><span class="sxs-lookup"><span data-stu-id="bbf23-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="bbf23-103">Ten przykład pokazuje, jak zażądać strony sieci Web i pobrać wyniki w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="bbf23-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbf23-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="bbf23-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="bbf23-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="bbf23-105">Compiling the Code</span></span>  
 <span data-ttu-id="bbf23-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="bbf23-106">This example requires:</span></span>  
  
- <span data-ttu-id="bbf23-107">Odwołania do <xref:System.IO> przestrzeni nazw <xref:System.Net> i.</span><span class="sxs-lookup"><span data-stu-id="bbf23-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf23-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbf23-108">See also</span></span>

- [<span data-ttu-id="bbf23-109">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="bbf23-109">Requesting Data</span></span>](requesting-data.md)
