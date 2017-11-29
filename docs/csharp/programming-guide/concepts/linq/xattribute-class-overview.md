---
title: "Przegląd klasy XAttribute (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e9cfedb476f44ef8c3eaeb45bac571d17802d525
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="cbfd5-102">Przegląd klasy XAttribute (C#)</span><span class="sxs-lookup"><span data-stu-id="cbfd5-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="cbfd5-103">Atrybuty są pary nazwa/wartość, które są skojarzone z elementem.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="cbfd5-104"><xref:System.Xml.Linq.XAttribute> Klasa reprezentuje atrybuty XML.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="cbfd5-105">Omówienie</span><span class="sxs-lookup"><span data-stu-id="cbfd5-105">Overview</span></span>  
 <span data-ttu-id="cbfd5-106">Praca z atrybutów w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest podobna do pracy z elementami.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="cbfd5-107">Ich konstruktory są podobne.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-107">Their constructors are similar.</span></span> <span data-ttu-id="cbfd5-108">Metody używane do pobierania kolekcji z nich są podobne.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="cbfd5-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wygląda bardzo podobnie do wyrażenia zapytania dla kolekcji atrybutów [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania wyrażenie nie zawiera kolekcję elementów.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="cbfd5-110">Kolejność, w którym atrybuty zostały dodane do elementu są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="cbfd5-111">Oznacza to, że podczas iteracji atrybuty wyświetlanych w tej samej kolejności, że zostały one dodane.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="cbfd5-112">Konstruktor XAttribute</span><span class="sxs-lookup"><span data-stu-id="cbfd5-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="cbfd5-113">Następujące konstruktora <xref:System.Xml.Linq.XAttribute> klasy jest najczęściej używaną:</span><span class="sxs-lookup"><span data-stu-id="cbfd5-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="cbfd5-114">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="cbfd5-114">Constructor</span></span>|<span data-ttu-id="cbfd5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="cbfd5-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="cbfd5-116">Tworzy <xref:System.Xml.Linq.XAttribute> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="cbfd5-117">`name` Argument określa nazwę atrybutu; `content` określa zawartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="cbfd5-118">Tworzenie elementu za pomocą atrybutu</span><span class="sxs-lookup"><span data-stu-id="cbfd5-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="cbfd5-119">Poniższy kod przedstawia typowych zadań tworzenia elementu zawierającego atrybut:</span><span class="sxs-lookup"><span data-stu-id="cbfd5-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="cbfd5-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="cbfd5-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="cbfd5-121">Konstrukcja funkcjonalności atrybutów</span><span class="sxs-lookup"><span data-stu-id="cbfd5-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="cbfd5-122">Można utworzyć <xref:System.Xml.Linq.XAttribute> wiersza z konstrukcji obiektów <xref:System.Xml.Linq.XElement> obiekty w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cbfd5-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 <span data-ttu-id="cbfd5-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="cbfd5-123">This example produces the following output:</span></span>  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="cbfd5-124">Atrybuty nie są węzłami</span><span class="sxs-lookup"><span data-stu-id="cbfd5-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="cbfd5-125">Istnieją pewne różnice między atrybuty i elementy.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="cbfd5-126"><xref:System.Xml.Linq.XAttribute>obiekty nie są węzłów w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="cbfd5-127">Są one pary nazwa/wartość skojarzona z elementem XML.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="cbfd5-128">W przeciwieństwie do modelu DOM (Document Object), to lepiej odzwierciedla struktury XML.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="cbfd5-129">Mimo że <xref:System.Xml.Linq.XAttribute> obiekty nie są faktycznie węzłów w drzewie XML, Praca z <xref:System.Xml.Linq.XAttribute> obiektów jest bardzo podobny do pracy z <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="cbfd5-130">Ta różnica jest głównie istotne tylko dla deweloperów, którzy pisania kodu, który działa z drzewa XML na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="cbfd5-131">Nie są związane z tym rozróżnienia wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="cbfd5-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbfd5-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbfd5-132">See Also</span></span>  
 [<span data-ttu-id="cbfd5-133">LINQ do XML-przegląd programowania w języku (C#)</span><span class="sxs-lookup"><span data-stu-id="cbfd5-133">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
