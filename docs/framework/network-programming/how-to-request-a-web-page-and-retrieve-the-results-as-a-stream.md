---
title: 'Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia'
description: Ten przykład pokazuje, jak zażądać strony sieci Web i pobrać wyniki w strumieniu w .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: bd57f9af6be29c783d044e785ebb36aaa8592df2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502486"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="61a3d-103">Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia</span><span class="sxs-lookup"><span data-stu-id="61a3d-103">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>

<span data-ttu-id="61a3d-104">Ten przykład pokazuje, jak zażądać strony sieci Web i pobrać wyniki w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="61a3d-104">This example shows how to request a Web page and retrieve the results in a stream.</span></span>
  
## <a name="example"></a><span data-ttu-id="61a3d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="61a3d-105">Example</span></span>

```csharp
var myClient = new WebClient();
Stream response = myClient.OpenRead("https://docs.microsoft.com/dotnet/");
// The stream data is used here.
response.Close();
```

```vb
Dim myClient As New WebClient()
Dim response As Stream = myClient.OpenRead("https://docs.microsoft.com/dotnet/")
' The stream data is used here.
response.Close()
```

## <a name="compiling-the-code"></a><span data-ttu-id="61a3d-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="61a3d-106">Compiling the Code</span></span>

 <span data-ttu-id="61a3d-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="61a3d-107">This example requires:</span></span>

- <span data-ttu-id="61a3d-108">Odwołania do <xref:System.IO> <xref:System.Net> przestrzeni nazw i.</span><span class="sxs-lookup"><span data-stu-id="61a3d-108">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="61a3d-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61a3d-109">See also</span></span>

- [<span data-ttu-id="61a3d-110">Żądanie danych</span><span class="sxs-lookup"><span data-stu-id="61a3d-110">Requesting Data</span></span>](requesting-data.md)
