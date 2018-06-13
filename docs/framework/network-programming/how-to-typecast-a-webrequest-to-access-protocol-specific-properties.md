---
title: 'Porady: rzutowanie typu WebRequest do właściwości specyficzne dla protokołu dostępu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3e01c68bdaa0cf9d3ab38b2267b35c57ad590ca1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394075"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a><span data-ttu-id="cf015-102">Porady: rzutowanie typu WebRequest do właściwości specyficzne dla protokołu dostępu</span><span class="sxs-lookup"><span data-stu-id="cf015-102">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>
<span data-ttu-id="cf015-103">W tym przykładzie przedstawiono sposób rzutowanie typu WebRequest, umożliwiając dostęp do właściwości specyficzne dla protokołu.</span><span class="sxs-lookup"><span data-stu-id="cf015-103">This example shows how to typecast a WebRequest so that you can access protocol specific properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf015-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf015-104">Example</span></span>  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf015-105">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf015-105">See Also</span></span>  
 [<span data-ttu-id="cf015-106">Programowanie protokołów podłączanych</span><span class="sxs-lookup"><span data-stu-id="cf015-106">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
