---
title: Zmiana deklaracji Namespace w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fa41e8a4e8f5a15d789ddc81c2b94072c6f16b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568059"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="b11b9-102">Zmiana deklaracji Namespace w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="b11b9-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="b11b9-103">**XmlDocument** przedstawia deklaracje przestrzeni nazw i **xmlns** atrybuty jako część modelu obiektu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b11b9-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="b11b9-104">Są one przechowywane w **XmlDocument**, dlatego podczas zapisywania dokumentu, można zachować lokalizację te atrybuty.</span><span class="sxs-lookup"><span data-stu-id="b11b9-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="b11b9-105">Zmiana tych atrybutów nie ma wpływu na **nazwa**, **NamespaceURI**, i **prefiksu** właściwości innych węzłów w drzewie.</span><span class="sxs-lookup"><span data-stu-id="b11b9-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="b11b9-106">Na przykład, jeśli załadować następującego dokumentu a następnie `test` element ma **NamespaceURI** `123.`</span><span class="sxs-lookup"><span data-stu-id="b11b9-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="b11b9-107">Po usunięciu `xmlns` atrybutu w następujący sposób, a następnie `test` element nadal ma **NamespaceURI** z `123`.</span><span class="sxs-lookup"><span data-stu-id="b11b9-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="b11b9-108">Podobnie jeśli dodasz do innej `xmlns` atrybutu `doc` elementu w następujący sposób, a następnie `test` element nadal ma **NamespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="b11b9-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="b11b9-109">W związku z tym zmiana `xmlns` atrybutów nie będzie miał znaczenia dopóki Zapisz i ponownie załaduj **XmlDocument** obiektu.</span><span class="sxs-lookup"><span data-stu-id="b11b9-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b11b9-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b11b9-110">See Also</span></span>  
 [<span data-ttu-id="b11b9-111">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="b11b9-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
