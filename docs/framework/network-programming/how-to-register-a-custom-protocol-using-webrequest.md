---
title: 'Instrukcje: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 05b6f6c3f0f1fc1b36b60e8b0dae50de2826aba4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048250"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Instrukcje: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest
Ten przykład pokazuje, jak zarejestrować klasę specyficzną dla protokołu, która została zdefiniowana w innym miejscu. W tym przykładzie `CustomWebRequestCreator` jest obiektem implementowanym przez użytkownika, który implementuje `CustomWebRequest` metodę Create, która zwraca obiekt. W przykładzie kodu założono, że Zapisano `CustomWebRequest` kod implementujący niestandardowy protokół.  
  
## <a name="example"></a>Przykład  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
 Odwołania do <xref:System.Net> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie protokołów podłączanych](programming-pluggable-protocols.md)
