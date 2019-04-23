---
title: Usuwanie atrybutów z węzła elementu w ramach modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e38ad777112e5e88fe40c530da6107d0de0e3ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336138"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a><span data-ttu-id="9e655-102">Usuwanie atrybutów z węzła elementu w ramach modelu DOM</span><span class="sxs-lookup"><span data-stu-id="9e655-102">Removing Attributes from an Element Node in the DOM</span></span>
<span data-ttu-id="9e655-103">Istnieje wiele sposobów, aby usunąć atrybuty.</span><span class="sxs-lookup"><span data-stu-id="9e655-103">There are many ways to remove attributes.</span></span> <span data-ttu-id="9e655-104">Jedna z technik jest je usunąć z kolekcji atrybutów.</span><span class="sxs-lookup"><span data-stu-id="9e655-104">One technique is to remove them from the attribute collection.</span></span> <span data-ttu-id="9e655-105">Aby to zrobić, wykonywane są następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9e655-105">To do this, the following steps are performed:</span></span>  
  
1. <span data-ttu-id="9e655-106">Pobierz kolekcję atrybutów z elementu za pomocą `XmlAttributeCollection attrs = elem.Attributes;`.</span><span class="sxs-lookup"><span data-stu-id="9e655-106">Get the attribute collection from the element using `XmlAttributeCollection attrs = elem.Attributes;`.</span></span>  
  
2. <span data-ttu-id="9e655-107">Usuń atrybut z kolekcji atrybutów przy użyciu jednej z trzech metod:</span><span class="sxs-lookup"><span data-stu-id="9e655-107">Remove the attribute from the attribute collection using one of three methods:</span></span>  
  
    -   <span data-ttu-id="9e655-108">Użyj <xref:System.Xml.XmlAttributeCollection.Remove%2A> Aby usunąć określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="9e655-108">Use <xref:System.Xml.XmlAttributeCollection.Remove%2A> to remove a specific attribute.</span></span>  
  
    -   <span data-ttu-id="9e655-109">Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> usunąć wszystkie atrybuty z kolekcji i pozostaw elementu żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="9e655-109">Use <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> to remove all attributes from the collection and leave the element with no attributes.</span></span>  
  
    -   <span data-ttu-id="9e655-110">Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> Aby usunąć atrybut z kolekcji atrybutów przy użyciu jego numer indeksu.</span><span class="sxs-lookup"><span data-stu-id="9e655-110">Use <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> to remove an attribute from the attribute collection by using its index number.</span></span>  
  
 <span data-ttu-id="9e655-111">Następujące metody usuwanie atrybutów z węzła elementu.</span><span class="sxs-lookup"><span data-stu-id="9e655-111">The following methods remove attributes from the element node.</span></span>  
  
-   <span data-ttu-id="9e655-112">Użyj <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> do usunięcia z kolekcji atrybutów.</span><span class="sxs-lookup"><span data-stu-id="9e655-112">Use <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> to remove the attribute collection.</span></span>  
  
-   <span data-ttu-id="9e655-113">Użyj <xref:System.Xml.XmlElement.RemoveAttribute%2A> usunąć jeden atrybut według nazwy z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9e655-113">Use <xref:System.Xml.XmlElement.RemoveAttribute%2A> to remove a single attribute by name from the collection.</span></span>  
  
-   <span data-ttu-id="9e655-114">Użyj <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> usunąć jeden atrybut przez numer indeksu z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9e655-114">Use <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> to remove a single attribute by index number from the collection.</span></span>  
  
 <span data-ttu-id="9e655-115">Co więcej alternatywą jest pobieranie elementu, Pobierz atrybut z kolekcji atrybutów i Usuń węzeł atrybutu bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="9e655-115">One more alternative is to get the element, get the attribute from the attribute collection, and remove the attribute node directly.</span></span> <span data-ttu-id="9e655-116">Aby uzyskać ten atrybut z kolekcji atrybutów, można użyć nazwy `XmlAttribute attr = attrs["attr_name"];`, indeks `XmlAttribute attr = attrs[0];`, lub w pełni kwalifikując nazwę z przestrzenią nazw `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span><span class="sxs-lookup"><span data-stu-id="9e655-116">To get the attribute from the attribute collection, you can use a name, `XmlAttribute attr = attrs["attr_name"];`, an index `XmlAttribute attr = attrs[0];`, or by fully qualifying the name with the namespace `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span></span>  
  
 <span data-ttu-id="9e655-117">Niezależnie od metody, aby usunąć atrybuty istnieją specjalne ograniczenia na temat usuwania atrybutów, które są zdefiniowane jako domyślne atrybuty w definicji typu dokumentu (DTD).</span><span class="sxs-lookup"><span data-stu-id="9e655-117">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the document type definition (DTD).</span></span> <span data-ttu-id="9e655-118">Nie można usunąć domyślnych atrybutów, chyba że zostanie usunięty element, do którego należą.</span><span class="sxs-lookup"><span data-stu-id="9e655-118">Default attributes cannot be removed unless the element they belong to is removed.</span></span> <span data-ttu-id="9e655-119">Atrybuty domyślne są zawsze obecne elementy, które mają domyślne atrybutów zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="9e655-119">Default attributes are always present for elements that have default attributes declared.</span></span> <span data-ttu-id="9e655-120">Usunięcie domyślnego atrybutu z <xref:System.Xml.XmlAttributeCollection> lub <xref:System.Xml.XmlElement> wyniki w atrybucie zastąpienie wstawiony <xref:System.Xml.XmlAttributeCollection> elementu zainicjowany do wartości domyślnej, który został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="9e655-120">Removing a default attribute from an <xref:System.Xml.XmlAttributeCollection> or from the <xref:System.Xml.XmlElement> results in a replacement attribute inserted into the <xref:System.Xml.XmlAttributeCollection> of the element, initialized to the default value that was declared.</span></span> <span data-ttu-id="9e655-121">Jeśli masz element, który został zdefiniowany jako `<book att1="1" att2="2" att3="3"></book>`, można skorzystać z `book` zadeklarowany element z trzech atrybutów domyślnych.</span><span class="sxs-lookup"><span data-stu-id="9e655-121">If you have an element defined as `<book att1="1" att2="2" att3="3"></book>`, then you have a `book` element with three default attributes declared.</span></span> <span data-ttu-id="9e655-122">Implementacja XML Document Object Model (DOM) gwarantuje, że tak długo, jak to `book` element istnieje, jego atrybuty te trzy domyślne `att1`, `att2`, i `att3`.</span><span class="sxs-lookup"><span data-stu-id="9e655-122">The XML Document Object Model (DOM) implementation guarantees that as long as this `book` element exists, it has these three default attributes of `att1`, `att2`, and `att3`.</span></span>  
  
 <span data-ttu-id="9e655-123">Gdy zostanie wywołana z <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> metody ustawia wartość atrybutu String.Empty, ponieważ atrybut nie może istnieć bez wartości.</span><span class="sxs-lookup"><span data-stu-id="9e655-123">When called with an <xref:System.Xml.XmlAttribute>, the <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> method sets the value of the attribute to String.Empty, as an attribute cannot exist without a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e655-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e655-124">See also</span></span>

- [<span data-ttu-id="9e655-125">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="9e655-125">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
