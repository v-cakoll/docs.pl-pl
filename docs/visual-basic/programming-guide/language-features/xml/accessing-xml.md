---
title: Uzyskiwanie dostępu do kodu XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 1fa1d94fc710272ac0ba9ea7167989da42a51fcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351748"
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="5ba11-102">Uzyskiwanie dostępu do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ba11-102">Accessing XML in Visual Basic</span></span>
<span data-ttu-id="5ba11-103">Visual Basic udostępnia właściwości osi XML na potrzeby uzyskiwania dostępu do struktur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] i nawigowania w nich.</span><span class="sxs-lookup"><span data-stu-id="5ba11-103">Visual Basic provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="5ba11-104">Te właściwości używają specjalnej składni, aby umożliwić dostęp do elementów i atrybutów przez określenie nazw XML.</span><span class="sxs-lookup"><span data-stu-id="5ba11-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="5ba11-105">Poniższa tabela zawiera listę funkcji języka, które umożliwiają dostęp do elementów i atrybutów XML w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5ba11-105">The following table lists the language features that enable you to access XML elements and attributes in Visual Basic.</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="5ba11-106">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="5ba11-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="5ba11-107">Opis właściwości</span><span class="sxs-lookup"><span data-stu-id="5ba11-107">Property description</span></span>|<span data-ttu-id="5ba11-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ba11-108">Example</span></span>|<span data-ttu-id="5ba11-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5ba11-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="5ba11-110">*oś podrzędna*</span><span class="sxs-lookup"><span data-stu-id="5ba11-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="5ba11-111">Pobiera wszystkie elementy `phone`, które są elementami podrzędnymi elementu `contact`.</span><span class="sxs-lookup"><span data-stu-id="5ba11-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="5ba11-112">*oś atrybutów*</span><span class="sxs-lookup"><span data-stu-id="5ba11-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="5ba11-113">Pobiera wszystkie `type` atrybuty elementu `phone`.</span><span class="sxs-lookup"><span data-stu-id="5ba11-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="5ba11-114">*oś elementu podrzędnego*</span><span class="sxs-lookup"><span data-stu-id="5ba11-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="5ba11-115">Pobiera wszystkie elementy `name` elementu `contacts`, niezależnie od ich występowania w hierarchii.</span><span class="sxs-lookup"><span data-stu-id="5ba11-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="5ba11-116">*Indeksator rozszerzeń*</span><span class="sxs-lookup"><span data-stu-id="5ba11-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="5ba11-117">Pobiera pierwszy `name` elementu z sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5ba11-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="5ba11-118">*value*</span><span class="sxs-lookup"><span data-stu-id="5ba11-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="5ba11-119">Pobiera ciąg reprezentujący pierwszy obiekt w sekwencji lub `Nothing`, jeśli sekwencja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="5ba11-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="5ba11-120">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5ba11-120">In This Section</span></span>  
 [<span data-ttu-id="5ba11-121">Instrukcje: dostęp do elementów potomnych XML</span><span class="sxs-lookup"><span data-stu-id="5ba11-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="5ba11-122">Pokazuje, jak używać właściwości osi elementu podrzędnego w celu uzyskania dostępu do wszystkich elementów XML, które mają określoną nazwę i które są zawarte w określonym elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="5ba11-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="5ba11-123">Instrukcje: dostęp do elementów podrzędnych XML</span><span class="sxs-lookup"><span data-stu-id="5ba11-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="5ba11-124">Pokazuje, jak używać właściwości osi podrzędnej w celu uzyskania dostępu do wszystkich elementów podrzędnych XML, które mają określoną nazwę w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="5ba11-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="5ba11-125">Instrukcje: dostęp do atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="5ba11-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="5ba11-126">Pokazuje, jak używać właściwości osi atrybutu w celu uzyskania dostępu do wszystkich atrybutów XML o określonej nazwie w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="5ba11-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="5ba11-127">Instrukcje: deklarowanie prefiksów przestrzeni nazw XML i korzystanie z nich</span><span class="sxs-lookup"><span data-stu-id="5ba11-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="5ba11-128">Pokazuje, jak zadeklarować prefiks przestrzeni nazw XML i używać go do tworzenia elementów XML i uzyskiwania do nich dostępu.</span><span class="sxs-lookup"><span data-stu-id="5ba11-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5ba11-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5ba11-129">Related Sections</span></span>  
 [<span data-ttu-id="5ba11-130">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="5ba11-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/index.md)  
 <span data-ttu-id="5ba11-131">Zawiera łącza do sekcji opisujących różne właściwości dostępu XML.</span><span class="sxs-lookup"><span data-stu-id="5ba11-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="5ba11-132">Omówienie LINQ to XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ba11-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="5ba11-133">Zawiera wprowadzenie do korzystania z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5ba11-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="5ba11-134">Tworzenie kodu XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ba11-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="5ba11-135">Zawiera wprowadzenie do korzystania z literałów XML w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5ba11-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="5ba11-136">Manipulowanie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ba11-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="5ba11-137">Zawiera łącza do sekcji dotyczące ładowania i modyfikowania kodu XML w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5ba11-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="5ba11-138">XML</span><span class="sxs-lookup"><span data-stu-id="5ba11-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="5ba11-139">Zawiera łącza do sekcji opisujących sposób używania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5ba11-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
