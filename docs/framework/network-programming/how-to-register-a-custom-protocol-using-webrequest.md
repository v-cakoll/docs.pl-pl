---
title: 'Porady: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 5f863aa61058e87a7911bab3b02c3ba345419596
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193607"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Porady: rejestrowanie protokołu niestandardowego przy użyciu elementu WebRequest
W tym przykładzie pokazano, jak zarejestrować protokołu, który określonych classthat zdefiniowanej w innym miejscu. W tym przykładzie `CustomWebRequestCreator` jest implementowany przez użytkownika obiekt, który implementuje **Utwórz** metodę, która zwraca `CustomWebRequest` obiektu. Przykład kodu zakłada, że zostały napisane `CustomWebRequest` kod, który implementuje protokołu niestandardowego.  
  
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
  
 Odwołuje się do <xref:System.Net> przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie protokołów podłączanych](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
