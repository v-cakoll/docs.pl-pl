---
title: Zmienianie deklaracji przestrzeni nazw w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5457eab1f34eb3e7424d508509f5dd6a42ffb51f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976935"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="c4831-102">Zmienianie deklaracji przestrzeni nazw w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="c4831-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="c4831-103">Element **XmlDocument** ujawnia deklaracje przestrzeni nazw i atrybuty **xmlns** w ramach modelu obiektów dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c4831-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="c4831-104">Są one przechowywane w **XmlDocument**, dlatego po zapisaniu dokumentu można zachować jego lokalizację.</span><span class="sxs-lookup"><span data-stu-id="c4831-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="c4831-105">Zmiana tych atrybutów nie ma wpływu na właściwości **name**, **NamespaceURI**i **prefix** innych węzłów znajdujących się już w drzewie.</span><span class="sxs-lookup"><span data-stu-id="c4831-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="c4831-106">Na przykład, Jeśli załadujesz następujący dokument, element `test` ma **NamespaceURI** `123.`</span><span class="sxs-lookup"><span data-stu-id="c4831-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="c4831-107">W przypadku usunięcia `xmlns` atrybutu w następujący sposób element `test` nadal ma **NamespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="c4831-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="c4831-108">Podobnie, jeśli dodasz inny atrybut `xmlns` do elementu `doc` w następujący sposób, element `test` nadal ma `123`**NamespaceURI** .</span><span class="sxs-lookup"><span data-stu-id="c4831-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="c4831-109">W związku z tym zmiana atrybutów `xmlns` nie będzie miała wpływu do momentu zapisania i ponownego załadowania obiektu **XmlDocument** .</span><span class="sxs-lookup"><span data-stu-id="c4831-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4831-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4831-110">See also</span></span>

- [<span data-ttu-id="c4831-111">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="c4831-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
