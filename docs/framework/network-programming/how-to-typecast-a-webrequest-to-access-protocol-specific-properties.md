---
title: 'Instrukcje: rzutowanie elementu WebRequest w celu uzyskania dostępu do właściwości specyficznych dla protokołu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: a224d9dbab0157d77c05a5937fe35c027296a674
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048022"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a>Instrukcje: rzutowanie elementu WebRequest w celu uzyskania dostępu do właściwości specyficznych dla protokołu
Ten przykład pokazuje, jak rzutowanie żądanie WebRequest, aby można było uzyskać dostęp do właściwości specyficznych dla protokołu.  
  
## <a name="example"></a>Przykład  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie protokołów podłączanych](programming-pluggable-protocols.md)
