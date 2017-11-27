---
title: Zmiana deklaracji Namespace w dokumencie XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 627882efcbc41310ee177cba984e4add5b07bd15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="16061-102">Zmiana deklaracji Namespace w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="16061-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="16061-103">**XmlDocument** przedstawia deklaracje przestrzeni nazw i **xmlns** atrybuty jako część modelu obiektu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="16061-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="16061-104">Są one przechowywane w **XmlDocument**, dlatego podczas zapisywania dokumentu, można zachować lokalizację te atrybuty.</span><span class="sxs-lookup"><span data-stu-id="16061-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="16061-105">Zmiana tych atrybutów nie ma wpływu na **nazwa**, **NamespaceURI**, i **prefiksu** właściwości innych węzłów w drzewie.</span><span class="sxs-lookup"><span data-stu-id="16061-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="16061-106">Na przykład, jeśli załadować następującego dokumentu a następnie `test` element ma **NamespaceURI**`123.`</span><span class="sxs-lookup"><span data-stu-id="16061-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="16061-107">Po usunięciu `xmlns` atrybutu w następujący sposób, a następnie `test` element nadal ma **NamespaceURI** z `123`.</span><span class="sxs-lookup"><span data-stu-id="16061-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="16061-108">Podobnie jeśli dodasz do innej `xmlns` atrybutu `doc` elementu w następujący sposób, a następnie `test` element nadal ma **NamespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="16061-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="16061-109">W związku z tym zmiana `xmlns` atrybutów nie będzie miał znaczenia dopóki Zapisz i ponownie załaduj **XmlDocument** obiektu.</span><span class="sxs-lookup"><span data-stu-id="16061-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16061-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16061-110">See Also</span></span>  
 [<span data-ttu-id="16061-111">Modelu obiektu dokumentu XML modelu DOM)</span><span class="sxs-lookup"><span data-stu-id="16061-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
