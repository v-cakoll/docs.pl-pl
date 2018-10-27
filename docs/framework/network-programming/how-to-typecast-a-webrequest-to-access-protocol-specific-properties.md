---
title: 'Porady: rzutowanie elementu WebRequest do właściwości specyficznych dla protokołu dostępu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: ec5b9f1db17cf1c90484b0a44063efef9fa16cf9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180091"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a>Porady: rzutowanie elementu WebRequest do właściwości specyficznych dla protokołu dostępu
W tym przykładzie przedstawiono sposób rzutowanie elementu WebRequest, dzięki czemu można dostęp do właściwości specyficznych dla protokołu.  
  
## <a name="example"></a>Przykład  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie protokołów podłączanych](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
