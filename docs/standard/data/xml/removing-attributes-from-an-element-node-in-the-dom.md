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
ms.openlocfilehash: b4ca08d8080c2116ce05634a544c91780869b165
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a><span data-ttu-id="d6466-102">Usuwanie atrybutów z węzłem elementu w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="d6466-102">Removing Attributes from an Element Node in the DOM</span></span>
<span data-ttu-id="d6466-103">Istnieje wiele sposobów, aby usunąć atrybuty.</span><span class="sxs-lookup"><span data-stu-id="d6466-103">There are many ways to remove attributes.</span></span> <span data-ttu-id="d6466-104">Jeden technika jest je usunąć z kolekcji atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d6466-104">One technique is to remove them from the attribute collection.</span></span> <span data-ttu-id="d6466-105">Aby to zrobić, są wykonywane następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="d6466-105">To do this, the following steps are performed:</span></span>  
  
1.  <span data-ttu-id="d6466-106">Pobierz kolekcję atrybutów z przy użyciu elementu `XmlAttributeCollection attrs = elem.Attributes;`.</span><span class="sxs-lookup"><span data-stu-id="d6466-106">Get the attribute collection from the element using `XmlAttributeCollection attrs = elem.Attributes;`.</span></span>  
  
2.  <span data-ttu-id="d6466-107">Usuń atrybut z kolekcji atrybutów przy użyciu jednej z trzech metod:</span><span class="sxs-lookup"><span data-stu-id="d6466-107">Remove the attribute from the attribute collection using one of three methods:</span></span>  
  
    -   <span data-ttu-id="d6466-108">Użyj <xref:System.Xml.XmlAttributeCollection.Remove%2A> Aby usunąć określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="d6466-108">Use <xref:System.Xml.XmlAttributeCollection.Remove%2A> to remove a specific attribute.</span></span>  
  
    -   <span data-ttu-id="d6466-109">Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> Aby usunąć wszystkie atrybuty z kolekcji i pozostawić element bez atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d6466-109">Use <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> to remove all attributes from the collection and leave the element with no attributes.</span></span>  
  
    -   <span data-ttu-id="d6466-110">Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> można usunąć atrybutu z kolekcji atrybutów przy użyciu numeru indeksu.</span><span class="sxs-lookup"><span data-stu-id="d6466-110">Use <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> to remove an attribute from the attribute collection by using its index number.</span></span>  
  
 <span data-ttu-id="d6466-111">Następujące metody usuwanie atrybutów z węzeł elementu.</span><span class="sxs-lookup"><span data-stu-id="d6466-111">The following methods remove attributes from the element node.</span></span>  
  
-   <span data-ttu-id="d6466-112">Użyj <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> można usunąć kolekcji atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d6466-112">Use <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> to remove the attribute collection.</span></span>  
  
-   <span data-ttu-id="d6466-113">Użyj <xref:System.Xml.XmlElement.RemoveAttribute%2A> usunąć jeden atrybut o nazwie z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d6466-113">Use <xref:System.Xml.XmlElement.RemoveAttribute%2A> to remove a single attribute by name from the collection.</span></span>  
  
-   <span data-ttu-id="d6466-114">Użyj <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> usunięcie jeden atrybut, a numer indeksu z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d6466-114">Use <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> to remove a single attribute by index number from the collection.</span></span>  
  
 <span data-ttu-id="d6466-115">Co więcej alternatywą jest uzyskać elementu, pobrać atrybutu z kolekcji atrybutów i usunąć węzła atrybutu bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="d6466-115">One more alternative is to get the element, get the attribute from the attribute collection, and remove the attribute node directly.</span></span> <span data-ttu-id="d6466-116">Aby uzyskać ten atrybut z kolekcji atrybutów, można użyć nazwy, `XmlAttribute attr = attrs["attr_name"];`, indeks `XmlAttribute attr = attrs[0];`, lub w pełni kwalifikowanie nazw z przestrzeni nazw `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span><span class="sxs-lookup"><span data-stu-id="d6466-116">To get the attribute from the attribute collection, you can use a name, `XmlAttribute attr = attrs["attr_name"];`, an index `XmlAttribute attr = attrs[0];`, or by fully qualifying the name with the namespace `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span></span>  
  
 <span data-ttu-id="d6466-117">Niezależnie od metody umożliwia usuwanie atrybutów ma ograniczeń specjalnych na usuwanie atrybutów, które są zdefiniowane jako domyślne atrybuty w definicji typu dokumentu (DTD).</span><span class="sxs-lookup"><span data-stu-id="d6466-117">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the document type definition (DTD).</span></span> <span data-ttu-id="d6466-118">Nie można usunąć atrybutów domyślnych, chyba że zostanie usunięty element, do którego należą.</span><span class="sxs-lookup"><span data-stu-id="d6466-118">Default attributes cannot be removed unless the element they belong to is removed.</span></span> <span data-ttu-id="d6466-119">Domyślne atrybuty zawsze znajdują się dla elementów, które mają atrybuty domyślne zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="d6466-119">Default attributes are always present for elements that have default attributes declared.</span></span> <span data-ttu-id="d6466-120">Usuwanie domyślnego atrybutu z <xref:System.Xml.XmlAttributeCollection> lub <xref:System.Xml.XmlElement> wyniki w atrybucie zastępczy wstawione do <xref:System.Xml.XmlAttributeCollection> elementu zainicjowany do wartości domyślnej, który został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="d6466-120">Removing a default attribute from an <xref:System.Xml.XmlAttributeCollection> or from the <xref:System.Xml.XmlElement> results in a replacement attribute inserted into the <xref:System.Xml.XmlAttributeCollection> of the element, initialized to the default value that was declared.</span></span> <span data-ttu-id="d6466-121">Jeśli masz zdefiniowany jako element `<book att1="1" att2="2" att3="3"></book>`, a następnie masz `book` zadeklarowany element z trzech atrybutów domyślnych.</span><span class="sxs-lookup"><span data-stu-id="d6466-121">If you have an element defined as `<book att1="1" att2="2" att3="3"></book>`, then you have a `book` element with three default attributes declared.</span></span> <span data-ttu-id="d6466-122">Implementacja XML modelu DOM (Document Object) gwarantuje, że tak długo, jak to `book` element istnieje, ma następujące trzy domyślne atrybuty `att1`, `att2`, i `att3`.</span><span class="sxs-lookup"><span data-stu-id="d6466-122">The XML Document Object Model (DOM) implementation guarantees that as long as this `book` element exists, it has these three default attributes of `att1`, `att2`, and `att3`.</span></span>  
  
 <span data-ttu-id="d6466-123">Po wywołaniu z <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> metody ustawia wartość atrybutu String.Empty, ponieważ atrybut nie może istnieć bez wartości.</span><span class="sxs-lookup"><span data-stu-id="d6466-123">When called with an <xref:System.Xml.XmlAttribute>, the <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> method sets the value of the attribute to String.Empty, as an attribute cannot exist without a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6466-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6466-124">See Also</span></span>  
 [<span data-ttu-id="d6466-125">Modelu obiektu dokumentu XML modelu DOM)</span><span class="sxs-lookup"><span data-stu-id="d6466-125">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
