---
title: "Uzyskiwanie dostępu do XML w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79c7b8a94731e151a803a041d91dd1e240ddeb97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-xml-in-visual-basic"></a><span data-ttu-id="989aa-102">Uzyskiwanie dostępu do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="989aa-102">Accessing XML in Visual Basic</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="989aa-103">Udostępnia właściwości osi XML do uzyskiwania dostępu i nawigacja [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] struktury.</span><span class="sxs-lookup"><span data-stu-id="989aa-103"> provides XML axis properties for accessing and navigating [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] structures.</span></span> <span data-ttu-id="989aa-104">Te właściwości Użyj specjalnych składni, aby włączyć dostęp do elementów i atrybutów przez określenie nazw XML.</span><span class="sxs-lookup"><span data-stu-id="989aa-104">These properties use a special syntax to enable you to access elements and attributes by specifying the XML names.</span></span>  
  
 <span data-ttu-id="989aa-105">W poniższej tabeli wymieniono funkcje językowe, które umożliwiają dostęp do elementów XML oraz atrybuty w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="989aa-105">The following table lists the language features that enable you to access XML elements and attributes in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="xml-axis-properties"></a><span data-ttu-id="989aa-106">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="989aa-106">XML Axis Properties</span></span>  
  
|<span data-ttu-id="989aa-107">Opis właściwości</span><span class="sxs-lookup"><span data-stu-id="989aa-107">Property description</span></span>|<span data-ttu-id="989aa-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="989aa-108">Example</span></span>|<span data-ttu-id="989aa-109">Opis</span><span class="sxs-lookup"><span data-stu-id="989aa-109">Description</span></span>|  
|--------------------------|-------------|-----------------|  
|<span data-ttu-id="989aa-110">*osi podrzędnej*</span><span class="sxs-lookup"><span data-stu-id="989aa-110">*child axis*</span></span>|`contact.<phone>`|<span data-ttu-id="989aa-111">Pobiera wszystkie `phone` elementów, które są elementami podrzędnymi elementu `contact` elementu.</span><span class="sxs-lookup"><span data-stu-id="989aa-111">Gets all `phone` elements that are child elements of the `contact` element.</span></span>|  
|<span data-ttu-id="989aa-112">*Atrybut osi*</span><span class="sxs-lookup"><span data-stu-id="989aa-112">*attribute axis*</span></span>|`phone.@type`|<span data-ttu-id="989aa-113">Pobiera wszystkie `type` atrybuty `phone` elementu.</span><span class="sxs-lookup"><span data-stu-id="989aa-113">Gets all `type` attributes of the `phone` element.</span></span>|  
|<span data-ttu-id="989aa-114">*osi elementu podrzędnego*</span><span class="sxs-lookup"><span data-stu-id="989aa-114">*descendant axis*</span></span>|`contacts...<name>`|<span data-ttu-id="989aa-115">Pobiera wszystkie `name` elementy `contacts` elementu, niezależnie od tego, jak głęboko w hierarchii występowania.</span><span class="sxs-lookup"><span data-stu-id="989aa-115">Gets all `name` elements of the `contacts` element, regardless of how deep in the hierarchy they occur.</span></span>|  
|<span data-ttu-id="989aa-116">*indeksator rozszerzeń*</span><span class="sxs-lookup"><span data-stu-id="989aa-116">*extension indexer*</span></span>|`contacts...<name>(0)`|<span data-ttu-id="989aa-117">Pobiera pierwszy `name` element z sekwencji.</span><span class="sxs-lookup"><span data-stu-id="989aa-117">Gets the first `name` element from the sequence.</span></span>|  
|<span data-ttu-id="989aa-118">*wartość*</span><span class="sxs-lookup"><span data-stu-id="989aa-118">*value*</span></span>|`contacts...<name>.Value`|<span data-ttu-id="989aa-119">Pobiera pierwszy obiekt reprezentację ciągu w sekwencji, lub `Nothing` Jeśli sekwencja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="989aa-119">Gets the string representation of the first object in the sequence, or `Nothing` if the sequence is empty.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="989aa-120">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="989aa-120">In This Section</span></span>  
 [<span data-ttu-id="989aa-121">Porady: dostęp do elementów podrzędnych XML</span><span class="sxs-lookup"><span data-stu-id="989aa-121">How to: Access XML Descendant Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 <span data-ttu-id="989aa-122">Przedstawia sposób użycia właściwości osi elementu podrzędnego na dostęp do wszystkich elementów XML, które mają określonej nazwy i znajdujących się w obszarze określonego elementu XML.</span><span class="sxs-lookup"><span data-stu-id="989aa-122">Shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under a specified XML element.</span></span>  
  
 [<span data-ttu-id="989aa-123">Porady: dostęp do elementów podrzędnych XML</span><span class="sxs-lookup"><span data-stu-id="989aa-123">How to: Access XML Child Elements</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 <span data-ttu-id="989aa-124">Przedstawia sposób użycia elementem podrzędnym właściwości osi, aby dostęp do wszystkich elementów podrzędnych XML, których nazwa określona w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="989aa-124">Shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="989aa-125">Porady: dostęp do atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="989aa-125">How to: Access XML Attributes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 <span data-ttu-id="989aa-126">Przedstawia sposób użycia właściwości osi atrybutu na dostęp do wszystkich atrybutów XML, których nazwa określona w elemencie XML.</span><span class="sxs-lookup"><span data-stu-id="989aa-126">Shows how to use an attribute axis property to access all XML attributes that have a specified name in an XML element.</span></span>  
  
 [<span data-ttu-id="989aa-127">Porady: deklarowanie prefiksów Namespace XML i korzystanie</span><span class="sxs-lookup"><span data-stu-id="989aa-127">How to: Declare and Use XML Namespace Prefixes</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 <span data-ttu-id="989aa-128">Pokazuje, jak deklaruje prefiks przestrzeni nazw XML i użyć go do tworzenia i dostęp do elementów XML.</span><span class="sxs-lookup"><span data-stu-id="989aa-128">Shows how to declare an XML namespace prefix and use it to create and access XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="989aa-129">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="989aa-129">Related Sections</span></span>  
 [<span data-ttu-id="989aa-130">Właściwości osi XML</span><span class="sxs-lookup"><span data-stu-id="989aa-130">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="989aa-131">Zawiera łącza do sekcji opisujące różne właściwości dostępu XML.</span><span class="sxs-lookup"><span data-stu-id="989aa-131">Provides links to sections describing the various XML access properties.</span></span>  
  
 [<span data-ttu-id="989aa-132">Przegląd LINQ do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="989aa-132">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="989aa-133">Wprowadzenie do przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="989aa-133">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="989aa-134">Tworzenie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="989aa-134">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="989aa-135">Wprowadzenie do przy użyciu literałów XML w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="989aa-135">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="989aa-136">Manipulowanie XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="989aa-136">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 <span data-ttu-id="989aa-137">Zawiera łącza do sekcji o ładowania i modyfikowanie kodu XML w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="989aa-137">Provides links to sections about loading and modifying XML in Visual Basic.</span></span>  
  
 [<span data-ttu-id="989aa-138">XML</span><span class="sxs-lookup"><span data-stu-id="989aa-138">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="989aa-139">Zawiera łącza do sekcji opisujący sposób użycia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="989aa-139">Provides links to sections describing how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>
