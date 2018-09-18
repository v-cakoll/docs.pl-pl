---
title: Zmienianie właściwości prefiksu Namespace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a6597a3a57cd68c4dd17c4fbae882590f373709
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45969070"
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="2e236-102">Zmienianie właściwości prefiksu Namespace</span><span class="sxs-lookup"><span data-stu-id="2e236-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="2e236-103">**XmlNode** klasy pozwala na zmianę skojarzonych z danym węźle prefiks przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2e236-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="2e236-104">Na przykład poniższy kod przedstawia prefiks elementu zmieniany.</span><span class="sxs-lookup"><span data-stu-id="2e236-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
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
  
 <span data-ttu-id="2e236-105">**Output**</span><span class="sxs-lookup"><span data-stu-id="2e236-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="2e236-106">Zmiana prefiksu węzeł nie powoduje zmiany jego przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="2e236-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="2e236-107">Przestrzeń nazw można ustawić tylko w przypadku, gdy węzeł zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="2e236-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="2e236-108">Gdy będzie się powtarzać drzewa, nowe atrybuty z przestrzeni nazw może być utrwalone się spełnić prefiksu, gdy ustawiasz.</span><span class="sxs-lookup"><span data-stu-id="2e236-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="2e236-109">Jeśli nie można utworzyć nowej przestrzeni nazw, prefiks zostanie zmieniona, więc węzeł zachowuje swoją nazwę lokalną i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2e236-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="2e236-110">Trwa dodawanie atrybutu przestrzeni nazw można znaleźć w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2e236-110">The following example shows a namespace attribute being added.</span></span>  
  
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
  
 <span data-ttu-id="2e236-111">**Output**</span><span class="sxs-lookup"><span data-stu-id="2e236-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="2e236-112">Po drzewie został zachowany na ciąg wyniku wywołania **dokumentu. Właściwości InnerXml**, `xmlns:a='123'` atrybut został dodany do zachowania przestrzeń nazw `test` elementu.</span><span class="sxs-lookup"><span data-stu-id="2e236-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="2e236-113">Było `'123'`, i pozostaje `'123'`.</span><span class="sxs-lookup"><span data-stu-id="2e236-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e236-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e236-114">See also</span></span>

- [<span data-ttu-id="2e236-115">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="2e236-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
