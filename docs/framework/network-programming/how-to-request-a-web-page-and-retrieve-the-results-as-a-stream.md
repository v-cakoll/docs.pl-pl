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
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia
Ten przykład pokazuje, jak zażądać strony sieci Web i pobrać wyniki w strumieniu.  
  
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
  
- Odwołania do <xref:System.IO> przestrzeni nazw <xref:System.Net> i.  
  
## <a name="see-also"></a>Zobacz także

- [Żądanie danych](requesting-data.md)
