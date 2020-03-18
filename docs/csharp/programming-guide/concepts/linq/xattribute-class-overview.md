---
title: Omówienie klasy XAttribute (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 7a806314664c6319fc45cff0dddedbe38027059d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635668"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="81ca2-102">Omówienie klasy XAttribute (C#)</span><span class="sxs-lookup"><span data-stu-id="81ca2-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="81ca2-103">Atrybuty są pary nazwa/wartość, które są skojarzone z elementem.</span><span class="sxs-lookup"><span data-stu-id="81ca2-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="81ca2-104">Klasa <xref:System.Xml.Linq.XAttribute> reprezentuje atrybuty XML.</span><span class="sxs-lookup"><span data-stu-id="81ca2-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="81ca2-105">Omówienie</span><span class="sxs-lookup"><span data-stu-id="81ca2-105">Overview</span></span>  
 <span data-ttu-id="81ca2-106">Praca z atrybutami jest [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podobna do pracy z elementami.</span><span class="sxs-lookup"><span data-stu-id="81ca2-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="81ca2-107">Ich konstruktory są podobne.</span><span class="sxs-lookup"><span data-stu-id="81ca2-107">Their constructors are similar.</span></span> <span data-ttu-id="81ca2-108">Metody, które są używane do pobierania kolekcji z nich są podobne.</span><span class="sxs-lookup"><span data-stu-id="81ca2-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="81ca2-109">Wyrażenie kwerendy LINQ dla kolekcji atrybutów wygląda bardzo podobnie do wyrażenia kwerendy LINQ dla kolekcji elementów.</span><span class="sxs-lookup"><span data-stu-id="81ca2-109">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="81ca2-110">Kolejność, w jakiej atrybuty zostały dodane do elementu jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="81ca2-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="81ca2-111">Oznacza to, że podczas itetensji przez atrybuty, widać je w tej samej kolejności, że zostały one dodane.</span><span class="sxs-lookup"><span data-stu-id="81ca2-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="81ca2-112">Konstruktor XAttribute</span><span class="sxs-lookup"><span data-stu-id="81ca2-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="81ca2-113">Następujący konstruktor <xref:System.Xml.Linq.XAttribute> klasy jest najczęściej używany:</span><span class="sxs-lookup"><span data-stu-id="81ca2-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="81ca2-114">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="81ca2-114">Constructor</span></span>|<span data-ttu-id="81ca2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="81ca2-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="81ca2-116">Tworzy obiekt <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="81ca2-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="81ca2-117">Argument `name` określa nazwę atrybutu; `content` określa zawartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="81ca2-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="81ca2-118">Tworzenie elementu z atrybutem</span><span class="sxs-lookup"><span data-stu-id="81ca2-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="81ca2-119">Poniższy kod przedstawia typowe zadanie tworzenia elementu, który zawiera atrybut:</span><span class="sxs-lookup"><span data-stu-id="81ca2-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="81ca2-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="81ca2-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="81ca2-121">Funkcjonalna konstrukcja atrybutów</span><span class="sxs-lookup"><span data-stu-id="81ca2-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="81ca2-122">Obiekty można <xref:System.Xml.Linq.XAttribute> konstruować zgodnie z <xref:System.Xml.Linq.XElement> konstrukcją obiektów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="81ca2-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="81ca2-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="81ca2-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="81ca2-124">Atrybuty nie są węzłami</span><span class="sxs-lookup"><span data-stu-id="81ca2-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="81ca2-125">Istnieją pewne różnice między atrybutami i elementami.</span><span class="sxs-lookup"><span data-stu-id="81ca2-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="81ca2-126"><xref:System.Xml.Linq.XAttribute>obiekty nie są węzłami w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="81ca2-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="81ca2-127">Są to pary nazw/wartości skojarzone z elementem XML.</span><span class="sxs-lookup"><span data-stu-id="81ca2-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="81ca2-128">W przeciwieństwie do modelu obiektu dokumentu (DOM), odzwierciedla to bardziej odzwierciedla strukturę XML.</span><span class="sxs-lookup"><span data-stu-id="81ca2-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="81ca2-129">Mimo <xref:System.Xml.Linq.XAttribute> że obiekty nie są w rzeczywistości węzłów w drzewie XML, praca z <xref:System.Xml.Linq.XAttribute> obiektami jest bardzo podobny do pracy z <xref:System.Xml.Linq.XElement> obiektami.</span><span class="sxs-lookup"><span data-stu-id="81ca2-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="81ca2-130">To rozróżnienie jest przede wszystkim ważne tylko dla deweloperów, którzy piszą kod, który działa z drzewami XML na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="81ca2-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="81ca2-131">Wielu deweloperów nie będzie się tym przejmować.</span><span class="sxs-lookup"><span data-stu-id="81ca2-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ca2-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81ca2-132">See also</span></span>

- [<span data-ttu-id="81ca2-133">Omówienie programowania LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="81ca2-133">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
