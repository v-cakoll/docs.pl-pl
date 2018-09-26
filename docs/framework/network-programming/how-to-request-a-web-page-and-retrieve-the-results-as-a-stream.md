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
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Instrukcje: żądanie strony internetowej i pobieranie wyników jako Stream
W tym przykładzie pokazano, jak żądania strony sieci Web do pobierania wyników w strumieniu.  
  
## <a name="example"></a>Przykład  
  
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
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołuje się do <xref:System.IO> i <xref:System.Net> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Żądanie danych](../../../docs/framework/network-programming/requesting-data.md)
