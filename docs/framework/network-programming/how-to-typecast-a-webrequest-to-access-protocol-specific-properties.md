---
title: 'Instrukcje: Rzutowanie elementu WebRequest do właściwości specyficznych dla protokołu dostępu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: 6202b0b02d334c076dbe41a785195344dd2d7efe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564516"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a><span data-ttu-id="e26ff-102">Instrukcje: Rzutowanie elementu WebRequest do właściwości specyficznych dla protokołu dostępu</span><span class="sxs-lookup"><span data-stu-id="e26ff-102">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>
<span data-ttu-id="e26ff-103">W tym przykładzie przedstawiono sposób rzutowanie elementu WebRequest, dzięki czemu można dostęp do właściwości specyficznych dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="e26ff-103">This example shows how to typecast a WebRequest so that you can access protocol specific properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e26ff-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e26ff-104">Example</span></span>  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a><span data-ttu-id="e26ff-105">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e26ff-105">See also</span></span>
- [<span data-ttu-id="e26ff-106">Programowanie protokołów podłączanych</span><span class="sxs-lookup"><span data-stu-id="e26ff-106">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
