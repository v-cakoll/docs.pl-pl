---
title: Zmienianie deklaracji Namespace w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a6b80a885f43facf4b3d4dd1dcb56d937d4f8de
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44188803"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="b072b-102">Zmienianie deklaracji Namespace w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="b072b-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="b072b-103">**XmlDocument** udostępnia deklaracje przestrzeni nazw i **xmlns** atrybutów jako część document object model.</span><span class="sxs-lookup"><span data-stu-id="b072b-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="b072b-104">Są one przechowywane w **XmlDocument**, dzięki czemu podczas zapisywania dokumentu, można zachować w niej lokalizacja tych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b072b-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="b072b-105">Zmiana tych atrybutów nie ma wpływu na **nazwa**, **NamespaceURI**, i **prefiksu** właściwości innych węzłów w drzewie.</span><span class="sxs-lookup"><span data-stu-id="b072b-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="b072b-106">Na przykład, jeśli załadować dokument a następnie `test` element ma **NamespaceURI** `123.`</span><span class="sxs-lookup"><span data-stu-id="b072b-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="b072b-107">Jeśli usuniesz `xmlns` atrybutu w następujący sposób, a następnie `test` element środki, nieopłacone **NamespaceURI** z `123`.</span><span class="sxs-lookup"><span data-stu-id="b072b-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="b072b-108">Podobnie jeśli dodasz innego `xmlns` atrybutu `doc` elementu w następujący sposób, a następnie `test` element środki, nieopłacone **NamespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="b072b-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="b072b-109">W związku z tym, zmieniając `xmlns` atrybuty będzie miał znaczenia, dopóki nie można zapisać i ponownie załaduj **XmlDocument** obiektu.</span><span class="sxs-lookup"><span data-stu-id="b072b-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b072b-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b072b-110">See also</span></span>

- [<span data-ttu-id="b072b-111">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="b072b-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
