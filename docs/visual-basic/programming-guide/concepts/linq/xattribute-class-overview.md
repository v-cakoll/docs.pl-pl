---
title: Klasa XAttribute — Przegląd (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 08b8ebf31a39325c98023d4bb333f8e06bbdeb3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="d4e07-102">Klasa XAttribute — Przegląd (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4e07-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="d4e07-103">Atrybuty są pary nazwa/wartość, które są skojarzone z elementem.</span><span class="sxs-lookup"><span data-stu-id="d4e07-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="d4e07-104"><xref:System.Xml.Linq.XAttribute> Klasa reprezentuje atrybuty XML.</span><span class="sxs-lookup"><span data-stu-id="d4e07-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="d4e07-105">Omówienie</span><span class="sxs-lookup"><span data-stu-id="d4e07-105">Overview</span></span>  
 <span data-ttu-id="d4e07-106">Praca z atrybutów w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest podobna do pracy z elementami.</span><span class="sxs-lookup"><span data-stu-id="d4e07-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="d4e07-107">Ich konstruktory są podobne.</span><span class="sxs-lookup"><span data-stu-id="d4e07-107">Their constructors are similar.</span></span> <span data-ttu-id="d4e07-108">Metody używane do pobierania kolekcji z nich są podobne.</span><span class="sxs-lookup"><span data-stu-id="d4e07-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="d4e07-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wygląda bardzo podobnie do wyrażenia zapytania dla kolekcji atrybutów [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania wyrażenie nie zawiera kolekcję elementów.</span><span class="sxs-lookup"><span data-stu-id="d4e07-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="d4e07-110">Kolejność, w którym atrybuty zostały dodane do elementu są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="d4e07-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="d4e07-111">Oznacza to, że podczas iteracji atrybuty wyświetlanych w tej samej kolejności, że zostały one dodane.</span><span class="sxs-lookup"><span data-stu-id="d4e07-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="d4e07-112">Konstruktor XAttribute</span><span class="sxs-lookup"><span data-stu-id="d4e07-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="d4e07-113">Następujące konstruktora <xref:System.Xml.Linq.XAttribute> klasy jest najczęściej używaną:</span><span class="sxs-lookup"><span data-stu-id="d4e07-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="d4e07-114">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="d4e07-114">Constructor</span></span>|<span data-ttu-id="d4e07-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d4e07-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="d4e07-116">Tworzy <xref:System.Xml.Linq.XAttribute> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d4e07-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="d4e07-117">`name` Argument określa nazwę atrybutu; `content` określa zawartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d4e07-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="d4e07-118">Tworzenie elementu za pomocą atrybutu</span><span class="sxs-lookup"><span data-stu-id="d4e07-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="d4e07-119">Poniższy kod przedstawia element, który zawiera atrybut przy użyciu literałów XML w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="d4e07-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="d4e07-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="d4e07-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="d4e07-121">Konstrukcja funkcjonalności atrybutów</span><span class="sxs-lookup"><span data-stu-id="d4e07-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="d4e07-122">Można utworzyć <xref:System.Xml.Linq.XAttribute> wiersza z konstrukcji obiektów <xref:System.Xml.Linq.XElement> obiekty w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d4e07-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="d4e07-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="d4e07-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="d4e07-124">Atrybuty nie są węzłami</span><span class="sxs-lookup"><span data-stu-id="d4e07-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="d4e07-125">Istnieją pewne różnice między atrybuty i elementy.</span><span class="sxs-lookup"><span data-stu-id="d4e07-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="d4e07-126"><xref:System.Xml.Linq.XAttribute> obiekty nie są węzłów w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="d4e07-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="d4e07-127">Są one pary nazwa/wartość skojarzona z elementem XML.</span><span class="sxs-lookup"><span data-stu-id="d4e07-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="d4e07-128">W przeciwieństwie do modelu DOM (Document Object), to lepiej odzwierciedla struktury XML.</span><span class="sxs-lookup"><span data-stu-id="d4e07-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="d4e07-129">Mimo że <xref:System.Xml.Linq.XAttribute> obiekty nie są faktycznie węzłów w drzewie XML, Praca z <xref:System.Xml.Linq.XAttribute> obiektów jest bardzo podobny do pracy z <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="d4e07-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="d4e07-130">Ta różnica jest głównie istotne tylko dla deweloperów, którzy pisania kodu, który działa z drzewa XML na poziomie węzła.</span><span class="sxs-lookup"><span data-stu-id="d4e07-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="d4e07-131">Nie są związane z tym rozróżnienia wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="d4e07-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e07-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4e07-132">See Also</span></span>  
 [<span data-ttu-id="d4e07-133">LINQ do programowania w języku XML-Przegląd (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4e07-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
