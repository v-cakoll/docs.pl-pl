---
title: "Porady: rejestrowanie przy użyciu WebRequest protokołu niestandardowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4fdb1188aeb7fd754ab21a268070830f55347441
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Porady: rejestrowanie przy użyciu WebRequest protokołu niestandardowego
Ten przykład przedstawia sposób rejestrowania protokołu, który określonych classthat jest zdefiniowany w innym miejscu. W tym przykładzie `CustomWebRequestCreator` jest implementowany przez użytkownika obiekt, który implementuje **Utwórz** metodę zwracającą `CustomWebRequest` obiektu. Przykład kodu zakłada, że można zapisywać `CustomWebRequest` kodu, który implementuje ten protokół niestandardowych.  
  
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
 [Protokoły podłączany programowania](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
