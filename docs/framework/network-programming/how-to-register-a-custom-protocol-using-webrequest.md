---
title: 'Instrukcje: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 05b6f6c3f0f1fc1b36b60e8b0dae50de2826aba4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048250"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Instrukcje: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest
W tym przykładzie pokazano, jak zarejestrować klasę określonego protokołu, który jest zdefiniowany w innym miejscu. W tym `CustomWebRequestCreator` przykładzie jest obiekt zaimplementowany przez użytkownika, który implementuje **Create** metoda, która zwraca `CustomWebRequest` obiekt. Przykładowy kod zakłada, że napisano `CustomWebRequest` kod, który implementuje protokół niestandardowy.  
  
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
  
 Odwołania do <xref:System.Net> obszaru nazw.  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie protokołów podłączanych](programming-pluggable-protocols.md)
