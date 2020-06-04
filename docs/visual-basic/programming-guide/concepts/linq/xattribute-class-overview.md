---
title: XAttribute, klasa — przegląd
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 5b165044b4bea83e1a0789e3dd00367ed27b43e8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413209"
---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="2e7bb-102">Przegląd klasy XAttribute (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e7bb-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="2e7bb-103">Atrybuty są parami nazw/wartości, które są skojarzone z elementem.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="2e7bb-104"><xref:System.Xml.Linq.XAttribute>Klasa reprezentuje atrybuty XML.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="2e7bb-105">Omówienie</span><span class="sxs-lookup"><span data-stu-id="2e7bb-105">Overview</span></span>  
 <span data-ttu-id="2e7bb-106">Praca z atrybutami w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest podobna do pracy z elementami.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="2e7bb-107">Ich konstruktory są podobne.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-107">Their constructors are similar.</span></span> <span data-ttu-id="2e7bb-108">Metody używane do pobierania kolekcji są podobne.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="2e7bb-109">Wyrażenie zapytania LINQ dla kolekcji atrybutów wygląda bardzo podobnie do wyrażenia zapytania LINQ dla kolekcji elementów.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-109">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="2e7bb-110">Kolejność, w jakiej atrybuty zostały dodane do elementu, jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="2e7bb-111">Oznacza to, że podczas iteracji przez atrybuty są one widoczne w takiej samej kolejności, w jakiej zostały dodane.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="2e7bb-112">Konstruktor XAttribute</span><span class="sxs-lookup"><span data-stu-id="2e7bb-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="2e7bb-113">Następujący Konstruktor <xref:System.Xml.Linq.XAttribute> klasy jest najczęściej używanym:</span><span class="sxs-lookup"><span data-stu-id="2e7bb-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="2e7bb-114">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="2e7bb-114">Constructor</span></span>|<span data-ttu-id="2e7bb-115">Opis</span><span class="sxs-lookup"><span data-stu-id="2e7bb-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="2e7bb-116">Tworzy obiekt <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="2e7bb-117">`name`Argument określa nazwę atrybutu; `content` określa zawartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="2e7bb-118">Tworzenie elementu z atrybutem</span><span class="sxs-lookup"><span data-stu-id="2e7bb-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="2e7bb-119">Poniższy kod przedstawia element, który zawiera atrybut używając literałów XML w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="2e7bb-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="2e7bb-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2e7bb-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="2e7bb-121">Funkcjonalne konstruowanie atrybutów</span><span class="sxs-lookup"><span data-stu-id="2e7bb-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="2e7bb-122">Można tworzyć <xref:System.Xml.Linq.XAttribute> obiekty w wierszu z konstrukcją <xref:System.Xml.Linq.XElement> obiektów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2e7bb-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 <span data-ttu-id="2e7bb-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2e7bb-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="2e7bb-124">Atrybuty nie są węzłami</span><span class="sxs-lookup"><span data-stu-id="2e7bb-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="2e7bb-125">Istnieją pewne różnice między atrybutami i elementami.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="2e7bb-126"><xref:System.Xml.Linq.XAttribute>obiekty nie są węzłami w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="2e7bb-127">Są to pary nazw/wartości skojarzone z elementem XML.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="2e7bb-128">W przeciwieństwie do Document Object Model (DOM), to dokładniej odzwierciedla strukturę XML.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="2e7bb-129">Chociaż <xref:System.Xml.Linq.XAttribute> obiekty nie są w rzeczywistości węzłami w drzewie XML, praca z <xref:System.Xml.Linq.XAttribute> obiektami jest bardzo podobna do pracy z <xref:System.Xml.Linq.XElement> obiektami.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="2e7bb-130">Ta różnica jest głównie ważna tylko dla deweloperów, którzy piszą kod, który współpracuje z drzewami XML na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="2e7bb-131">Wielu deweloperów nie będą zainteresowani tym rozróżnieniem.</span><span class="sxs-lookup"><span data-stu-id="2e7bb-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e7bb-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e7bb-132">See also</span></span>

- [<span data-ttu-id="2e7bb-133">Omówienie programowania LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e7bb-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
