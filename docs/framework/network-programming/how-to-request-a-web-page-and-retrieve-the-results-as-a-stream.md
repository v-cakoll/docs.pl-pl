---
title: 'Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 23c094f0a3f528750c9589dbc99a0ada86236967
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642545"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Instrukcje: żądanie strony internetowej i pobieranie wyników jako strumienia
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
  
- Odwołuje się do <xref:System.IO> i <xref:System.Net> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Żądanie danych](../../../docs/framework/network-programming/requesting-data.md)
