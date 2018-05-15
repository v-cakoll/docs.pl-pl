---
title: Uzyskiwanie dostępu do XML w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: b000b3f6846f800b2a96ce10cdd408a355f78a81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="9ff1f-102">Uzyskiwanie dostępu do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ff1f-102">Accessing XML in Visual Basic</span></span>
<span data-ttu-id="9ff1f-103">Visual Basic zapewnia właściwości osi XML do uzyskiwania dostępu i nawigacja [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] struktury.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="9ff1f-104">Te właściwości Użyj specjalnych składni, aby włączyć dostęp do elementów i atrybutów przez określenie nazw XML.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="9ff1f-105">W poniższej tabeli wymieniono funkcje językowe, które umożliwiają dostęp do elementów XML oraz atrybuty w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="9ff1f-106">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="9ff1f-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="9ff1f-107">Opis właściwości</span><span class="sxs-lookup"><span data-stu-id="9ff1f-107">Property description</span></span>|<span data-ttu-id="9ff1f-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ff1f-108">Example</span></span>|<span data-ttu-id="9ff1f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9ff1f-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="9ff1f-110">*osi podrzędnej*</span><span class="sxs-lookup"><span data-stu-id="9ff1f-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="9ff1f-111">Pobiera wszystkie `phone` elementów, które są elementami podrzędnymi elementu `contact` elementu.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="9ff1f-112">*Atrybut osi*</span><span class="sxs-lookup"><span data-stu-id="9ff1f-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="9ff1f-113">Pobiera wszystkie `type` atrybuty `phone` elementu.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="9ff1f-114">*osi elementu podrzędnego*</span><span class="sxs-lookup"><span data-stu-id="9ff1f-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="9ff1f-115">Pobiera wszystkie `name` elementy `contacts` elementu, niezależnie od tego, jak głęboko w hierarchii występowania.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="9ff1f-116">*indeksator rozszerzeń*</span><span class="sxs-lookup"><span data-stu-id="9ff1f-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="9ff1f-117">Pobiera pierwszy `name` element z sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="9ff1f-118">*value*</span><span class="sxs-lookup"><span data-stu-id="9ff1f-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="9ff1f-119">Pobiera pierwszy obiekt reprezentację ciągu w sekwencji, lub `Nothing` Jeśli sekwencja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="9ff1f-120">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9ff1f-120">In This Section</span></span>  
 [<span data-ttu-id="9ff1f-121">Instrukcje: dostęp do elementów potomnych XML</span><span class="sxs-lookup"><span data-stu-id="9ff1f-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="9ff1f-122">Przedstawia sposób użycia właściwości osi elementu podrzędnego na dostęp do wszystkich elementów XML, które mają określonej nazwy i znajdujących się w obszarze określonego elementu XML.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="9ff1f-123">Instrukcje: dostęp do elementów podrzędnych XML</span><span class="sxs-lookup"><span data-stu-id="9ff1f-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="9ff1f-124">Przedstawia sposób użycia elementem podrzędnym właściwości osi, aby dostęp do wszystkich elementów podrzędnych XML, których nazwa określona w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="9ff1f-125">Instrukcje: dostęp do atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="9ff1f-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="9ff1f-126">Przedstawia sposób użycia właściwości osi atrybutu na dostęp do wszystkich atrybutów XML, których nazwa określona w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="9ff1f-127">Instrukcje: deklarowanie prefiksów przestrzeni nazw XML i korzystanie z nich</span><span class="sxs-lookup"><span data-stu-id="9ff1f-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="9ff1f-128">Pokazuje, jak deklaruje prefiks przestrzeni nazw XML i użyć go do tworzenia i dostęp do elementów XML.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9ff1f-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9ff1f-129">Related Sections</span></span>  
 [<span data-ttu-id="9ff1f-130">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="9ff1f-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="9ff1f-131">Zawiera łącza do sekcji opisujące różne właściwości dostępu XML.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="9ff1f-132">Przegląd LINQ do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ff1f-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="9ff1f-133">Wprowadzenie do przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="9ff1f-134">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ff1f-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="9ff1f-135">Wprowadzenie do przy użyciu literałów XML w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="9ff1f-136">Manipulowanie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ff1f-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="9ff1f-137">Zawiera łącza do sekcji o ładowania i modyfikowanie kodu XML w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="9ff1f-138">XML</span><span class="sxs-lookup"><span data-stu-id="9ff1f-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="9ff1f-139">Zawiera łącza do sekcji opisujący sposób użycia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9ff1f-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
