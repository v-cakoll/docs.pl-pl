---
title: 'Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 21a5a81c6a5457897078db03fe35eaff330ed62d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647366"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a>Instrukcje: pobieranie elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest
W tym przykładzie pokazano, jak można pobrać elementu WebResponse specyficznego dla protokołu, który odpowiada elementowi WebRequest.  
  
## <a name="example"></a>Przykład  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołuje się do **przestrzeni nazw System.Net** przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Żądanie danych](../../../docs/framework/network-programming/requesting-data.md)
