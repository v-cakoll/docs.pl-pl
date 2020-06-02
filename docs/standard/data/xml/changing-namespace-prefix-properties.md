---
title: Zmienianie właściwości prefiksu przestrzeni nazw
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
ms.openlocfilehash: b817a68ff9789be414118ff4c1a3d88ca3ea9f01
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290918"
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="24ee9-102">Zmienianie właściwości prefiksu przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="24ee9-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="24ee9-103">Klasa **XmlNode** pozwala zmienić prefiks przestrzeni nazw skojarzony z danym węzłem.</span><span class="sxs-lookup"><span data-stu-id="24ee9-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="24ee9-104">Na przykład poniższy kod ilustruje prefiks elementu, który jest zmieniany.</span><span class="sxs-lookup"><span data-stu-id="24ee9-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
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
  
 <span data-ttu-id="24ee9-105">**Dane wyjściowe**</span><span class="sxs-lookup"><span data-stu-id="24ee9-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="24ee9-106">Zmiana prefiksu węzła nie powoduje zmiany jego przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="24ee9-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="24ee9-107">Przestrzeń nazw można ustawić tylko podczas tworzenia węzła.</span><span class="sxs-lookup"><span data-stu-id="24ee9-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="24ee9-108">Gdy utrwalasz drzewo, nowe atrybuty przestrzeni nazw mogą być utrwalane, aby spełnić ustawiony prefiks.</span><span class="sxs-lookup"><span data-stu-id="24ee9-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="24ee9-109">Jeśli nie można utworzyć nowej przestrzeni nazw, prefiks zostanie zmieniony, więc węzeł zachowuje swoją nazwę lokalną i przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="24ee9-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="24ee9-110">Poniższy przykład pokazuje dodawany atrybut przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="24ee9-110">The following example shows a namespace attribute being added.</span></span>  
  
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
  
 <span data-ttu-id="24ee9-111">**Dane wyjściowe**</span><span class="sxs-lookup"><span data-stu-id="24ee9-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="24ee9-112">Gdy drzewo zostało utrwalone jako ciąg w wyniku wywołania metody **doc. InnerXml**, `xmlns:a='123'` atrybut został dodany w celu zachowania przestrzeni nazw `test` elementu.</span><span class="sxs-lookup"><span data-stu-id="24ee9-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="24ee9-113">To `'123'` i pozostało `'123'` .</span><span class="sxs-lookup"><span data-stu-id="24ee9-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ee9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24ee9-114">See also</span></span>

- [<span data-ttu-id="24ee9-115">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="24ee9-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
