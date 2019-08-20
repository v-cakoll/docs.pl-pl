---
title: XAttribute — Omówienie klasyC#()
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 79ef00aa79be0c743423cfba1a911b238ff9a7ca
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590928"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="3abd6-102">XAttribute — Omówienie klasyC#()</span><span class="sxs-lookup"><span data-stu-id="3abd6-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="3abd6-103">Atrybuty są parami nazw/wartości, które są skojarzone z elementem.</span><span class="sxs-lookup"><span data-stu-id="3abd6-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="3abd6-104"><xref:System.Xml.Linq.XAttribute> Klasa reprezentuje atrybuty XML.</span><span class="sxs-lookup"><span data-stu-id="3abd6-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="3abd6-105">Omówienie</span><span class="sxs-lookup"><span data-stu-id="3abd6-105">Overview</span></span>  
 <span data-ttu-id="3abd6-106">Praca z atrybutami [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w jest podobna do pracy z elementami.</span><span class="sxs-lookup"><span data-stu-id="3abd6-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="3abd6-107">Ich konstruktory są podobne.</span><span class="sxs-lookup"><span data-stu-id="3abd6-107">Their constructors are similar.</span></span> <span data-ttu-id="3abd6-108">Metody używane do pobierania kolekcji są podobne.</span><span class="sxs-lookup"><span data-stu-id="3abd6-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="3abd6-109">Wyrażenie zapytania dla kolekcji atrybutów wygląda bardzo podobnie [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do wyrażenia zapytania dla kolekcji elementów. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3abd6-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="3abd6-110">Kolejność, w jakiej atrybuty zostały dodane do elementu, jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="3abd6-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="3abd6-111">Oznacza to, że podczas iteracji przez atrybuty są one widoczne w takiej samej kolejności, w jakiej zostały dodane.</span><span class="sxs-lookup"><span data-stu-id="3abd6-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="3abd6-112">Konstruktor XAttribute</span><span class="sxs-lookup"><span data-stu-id="3abd6-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="3abd6-113">Następujący Konstruktor <xref:System.Xml.Linq.XAttribute> klasy jest najczęściej używanym:</span><span class="sxs-lookup"><span data-stu-id="3abd6-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="3abd6-114">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="3abd6-114">Constructor</span></span>|<span data-ttu-id="3abd6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="3abd6-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="3abd6-116">Tworzy <xref:System.Xml.Linq.XAttribute> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3abd6-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="3abd6-117">`name` Argument określa nazwę atrybutu; `content` określa zawartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3abd6-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="3abd6-118">Tworzenie elementu z atrybutem</span><span class="sxs-lookup"><span data-stu-id="3abd6-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="3abd6-119">Poniższy kod przedstawia typowe zadanie tworzenia elementu, który zawiera atrybut:</span><span class="sxs-lookup"><span data-stu-id="3abd6-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="3abd6-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3abd6-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="3abd6-121">Funkcjonalne konstruowanie atrybutów</span><span class="sxs-lookup"><span data-stu-id="3abd6-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="3abd6-122">Można tworzyć <xref:System.Xml.Linq.XAttribute> obiekty w wierszu z <xref:System.Xml.Linq.XElement> konstrukcją obiektów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3abd6-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="3abd6-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3abd6-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="3abd6-124">Atrybuty nie są węzłami</span><span class="sxs-lookup"><span data-stu-id="3abd6-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="3abd6-125">Istnieją pewne różnice między atrybutami i elementami.</span><span class="sxs-lookup"><span data-stu-id="3abd6-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="3abd6-126"><xref:System.Xml.Linq.XAttribute>obiekty nie są węzłami w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="3abd6-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="3abd6-127">Są to pary nazw/wartości skojarzone z elementem XML.</span><span class="sxs-lookup"><span data-stu-id="3abd6-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="3abd6-128">W przeciwieństwie do Document Object Model (DOM), to dokładniej odzwierciedla strukturę XML.</span><span class="sxs-lookup"><span data-stu-id="3abd6-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="3abd6-129">Chociaż <xref:System.Xml.Linq.XAttribute> obiekty nie są w rzeczywistości węzłami w drzewie XML, praca <xref:System.Xml.Linq.XAttribute> z obiektami jest bardzo podobna do pracy <xref:System.Xml.Linq.XElement> z obiektami.</span><span class="sxs-lookup"><span data-stu-id="3abd6-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="3abd6-130">Ta różnica jest głównie ważna tylko dla deweloperów, którzy piszą kod, który współpracuje z drzewami XML na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="3abd6-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="3abd6-131">Wielu deweloperów nie będą zainteresowani tym rozróżnieniem.</span><span class="sxs-lookup"><span data-stu-id="3abd6-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3abd6-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3abd6-132">See also</span></span>

- [<span data-ttu-id="3abd6-133">Omówienie programowania LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3abd6-133">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
