---
title: "Zmiana właściwości Namespace prefiksu"
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
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3cb0db0fbffa5f42fb09f29da2976727451e3741
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="e1502-102">Zmiana właściwości Namespace prefiksu</span><span class="sxs-lookup"><span data-stu-id="e1502-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="e1502-103">**XmlNode** klasa pozwala na zmianę skojarzonych z danym węźle prefiks przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e1502-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="e1502-104">Na przykład poniższy kod przedstawia prefiks elementu zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="e1502-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="e1502-105">**Output**</span><span class="sxs-lookup"><span data-stu-id="e1502-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="e1502-106">Zmiana prefiksu węzła nie zmienia jego przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e1502-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="e1502-107">Przestrzeń nazw można ustawić tylko w przypadku, gdy węzeł zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="e1502-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="e1502-108">Podczas utrwalania drzewa, nowe atrybuty przestrzeni nazw może się trwale do zaspokojenia prefiksu, które można ustawić.</span><span class="sxs-lookup"><span data-stu-id="e1502-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="e1502-109">Jeśli nie można utworzyć nowej przestrzeni nazw, prefiks zostanie zmieniona, więc węzeł zachowuje lokalnej nazwy i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e1502-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="e1502-110">W poniższym przykładzie przedstawiono dodawany atrybut przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e1502-110">The following example shows a namespace attribute being added.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="e1502-111">**Output**</span><span class="sxs-lookup"><span data-stu-id="e1502-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="e1502-112">Po drzewie został utrwalony na ciąg w wyniku wywołania **dokumentu. InnerXml**, `xmlns:a='123'` atrybut został dodany do zachowania przestrzeń nazw `test` elementu.</span><span class="sxs-lookup"><span data-stu-id="e1502-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="e1502-113">Było `'123'`, i pozostaje `'123'`.</span><span class="sxs-lookup"><span data-stu-id="e1502-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1502-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1502-114">See Also</span></span>  
 [<span data-ttu-id="e1502-115">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="e1502-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
