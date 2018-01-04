---
title: "Usuwanie atrybutów z węzłem elementu w modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 967344db880347bde94330912bc5689c57b29921
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a><span data-ttu-id="57d6c-102">Usuwanie atrybutów z węzłem elementu w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="57d6c-102">Removing Attributes from an Element Node in the DOM</span></span>
<span data-ttu-id="57d6c-103">Istnieje wiele sposobów, aby usunąć atrybuty.</span><span class="sxs-lookup"><span data-stu-id="57d6c-103">There are many ways to remove attributes.</span></span> <span data-ttu-id="57d6c-104">Jeden technika jest je usunąć z kolekcji atrybutów.</span><span class="sxs-lookup"><span data-stu-id="57d6c-104">One technique is to remove them from the attribute collection.</span></span> <span data-ttu-id="57d6c-105">Aby to zrobić, są wykonywane następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="57d6c-105">To do this, the following steps are performed:</span></span>  
  
1.  <span data-ttu-id="57d6c-106">Pobierz kolekcję atrybutów z przy użyciu elementu `XmlAttributeCollection attrs = elem.Attributes;`.</span><span class="sxs-lookup"><span data-stu-id="57d6c-106">Get the attribute collection from the element using `XmlAttributeCollection attrs = elem.Attributes;`.</span></span>  
  
2.  <span data-ttu-id="57d6c-107">Usuń atrybut z kolekcji atrybutów przy użyciu jednej z trzech metod:</span><span class="sxs-lookup"><span data-stu-id="57d6c-107">Remove the attribute from the attribute collection using one of three methods:</span></span>  
  
    -   <span data-ttu-id="57d6c-108">Użyj <xref:System.Xml.XmlAttributeCollection.Remove%2A> Aby usunąć określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="57d6c-108">Use <xref:System.Xml.XmlAttributeCollection.Remove%2A> to remove a specific attribute.</span></span>  
  
    -   <span data-ttu-id="57d6c-109">Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> Aby usunąć wszystkie atrybuty z kolekcji i pozostawić element bez atrybutów.</span><span class="sxs-lookup"><span data-stu-id="57d6c-109">Use <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> to remove all attributes from the collection and leave the element with no attributes.</span></span>  
  
    -   <span data-ttu-id="57d6c-110">Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> można usunąć atrybutu z kolekcji atrybutów przy użyciu numeru indeksu.</span><span class="sxs-lookup"><span data-stu-id="57d6c-110">Use <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> to remove an attribute from the attribute collection by using its index number.</span></span>  
  
 <span data-ttu-id="57d6c-111">Następujące metody usuwanie atrybutów z węzeł elementu.</span><span class="sxs-lookup"><span data-stu-id="57d6c-111">The following methods remove attributes from the element node.</span></span>  
  
-   <span data-ttu-id="57d6c-112">Użyj <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> można usunąć kolekcji atrybutów.</span><span class="sxs-lookup"><span data-stu-id="57d6c-112">Use <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> to remove the attribute collection.</span></span>  
  
-   <span data-ttu-id="57d6c-113">Użyj <xref:System.Xml.XmlElement.RemoveAttribute%2A> usunąć jeden atrybut o nazwie z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="57d6c-113">Use <xref:System.Xml.XmlElement.RemoveAttribute%2A> to remove a single attribute by name from the collection.</span></span>  
  
-   <span data-ttu-id="57d6c-114">Użyj <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> usunięcie jeden atrybut, a numer indeksu z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="57d6c-114">Use <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> to remove a single attribute by index number from the collection.</span></span>  
  
 <span data-ttu-id="57d6c-115">Co więcej alternatywą jest uzyskać elementu, pobrać atrybutu z kolekcji atrybutów i usunąć węzła atrybutu bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="57d6c-115">One more alternative is to get the element, get the attribute from the attribute collection, and remove the attribute node directly.</span></span> <span data-ttu-id="57d6c-116">Aby uzyskać ten atrybut z kolekcji atrybutów, można użyć nazwy, `XmlAttribute attr = attrs["attr_name"];`, indeks `XmlAttribute attr = attrs[0];`, lub w pełni kwalifikowanie nazw z przestrzeni nazw `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span><span class="sxs-lookup"><span data-stu-id="57d6c-116">To get the attribute from the attribute collection, you can use a name, `XmlAttribute attr = attrs["attr_name"];`, an index `XmlAttribute attr = attrs[0];`, or by fully qualifying the name with the namespace `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span></span>  
  
 <span data-ttu-id="57d6c-117">Niezależnie od metody umożliwia usuwanie atrybutów ma ograniczeń specjalnych na usuwanie atrybutów, które są zdefiniowane jako domyślne atrybuty w definicji typu dokumentu (DTD).</span><span class="sxs-lookup"><span data-stu-id="57d6c-117">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the document type definition (DTD).</span></span> <span data-ttu-id="57d6c-118">Nie można usunąć atrybutów domyślnych, chyba że zostanie usunięty element, do którego należą.</span><span class="sxs-lookup"><span data-stu-id="57d6c-118">Default attributes cannot be removed unless the element they belong to is removed.</span></span> <span data-ttu-id="57d6c-119">Domyślne atrybuty zawsze znajdują się dla elementów, które mają atrybuty domyślne zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="57d6c-119">Default attributes are always present for elements that have default attributes declared.</span></span> <span data-ttu-id="57d6c-120">Usuwanie domyślnego atrybutu z <xref:System.Xml.XmlAttributeCollection> lub <xref:System.Xml.XmlElement> wyniki w atrybucie zastępczy wstawione do <xref:System.Xml.XmlAttributeCollection> elementu zainicjowany do wartości domyślnej, który został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="57d6c-120">Removing a default attribute from an <xref:System.Xml.XmlAttributeCollection> or from the <xref:System.Xml.XmlElement> results in a replacement attribute inserted into the <xref:System.Xml.XmlAttributeCollection> of the element, initialized to the default value that was declared.</span></span> <span data-ttu-id="57d6c-121">Jeśli masz zdefiniowany jako element `<book att1="1" att2="2" att3="3"></book>`, a następnie masz `book` zadeklarowany element z trzech atrybutów domyślnych.</span><span class="sxs-lookup"><span data-stu-id="57d6c-121">If you have an element defined as `<book att1="1" att2="2" att3="3"></book>`, then you have a `book` element with three default attributes declared.</span></span> <span data-ttu-id="57d6c-122">Implementacja XML modelu DOM (Document Object) gwarantuje, że tak długo, jak to `book` element istnieje, ma następujące trzy domyślne atrybuty `att1`, `att2`, i `att3`.</span><span class="sxs-lookup"><span data-stu-id="57d6c-122">The XML Document Object Model (DOM) implementation guarantees that as long as this `book` element exists, it has these three default attributes of `att1`, `att2`, and `att3`.</span></span>  
  
 <span data-ttu-id="57d6c-123">Po wywołaniu z <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> metody ustawia wartość atrybutu String.Empty, ponieważ atrybut nie może istnieć bez wartości.</span><span class="sxs-lookup"><span data-stu-id="57d6c-123">When called with an <xref:System.Xml.XmlAttribute>, the <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> method sets the value of the attribute to String.Empty, as an attribute cannot exist without a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57d6c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57d6c-124">See Also</span></span>  
 [<span data-ttu-id="57d6c-125">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="57d6c-125">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
