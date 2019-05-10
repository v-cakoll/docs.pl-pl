---
title: 'Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 74cb739d381c0b1422d9277be8c3c338a46f8fba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647418"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="85a69-102">Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia</span><span class="sxs-lookup"><span data-stu-id="85a69-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="85a69-103">W tym przykładzie pokazano, jak żądania strony sieci Web do pobierania wyników w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="85a69-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85a69-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="85a69-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="85a69-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="85a69-105">Compiling the Code</span></span>  
 <span data-ttu-id="85a69-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="85a69-106">This example requires:</span></span>  
  
- <span data-ttu-id="85a69-107">Odwołuje się do <xref:System.IO> i <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="85a69-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a69-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85a69-108">See also</span></span>

- [<span data-ttu-id="85a69-109">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="85a69-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
