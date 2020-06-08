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
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia

Ten przykład pokazuje, jak zażądać strony sieci Web i pobrać wyniki w strumieniu.
  
## <a name="example"></a>Przykład

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

## <a name="compiling-the-code"></a>Kompilowanie kodu

 Ten przykład wymaga:

- Odwołania do <xref:System.IO> <xref:System.Net> przestrzeni nazw i.

## <a name="see-also"></a>Zobacz także

- [Żądanie danych](requesting-data.md)
