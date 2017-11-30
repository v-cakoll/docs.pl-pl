---
title: "Nieprawidłowa zawartość klasy XElement i Objects3 klasy XDocument"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
caps.latest.revision: "5"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 113a187c9a852420ffcef3893a415a24bae2c655
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="886f2-102">Nieprawidłowa zawartość klasy XElement i obiektów klasy XDocument</span><span class="sxs-lookup"><span data-stu-id="886f2-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="886f2-103">W tym temacie opisano nieprawidłowe argumenty, które mogą zostać przekazane do konstruktorów i metod, które umożliwia dodawanie zawartości do elementów i dokumentów.</span><span class="sxs-lookup"><span data-stu-id="886f2-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="886f2-104">Nieprawidłowa zawartość.</span><span class="sxs-lookup"><span data-stu-id="886f2-104">Valid Content</span></span>  
 <span data-ttu-id="886f2-105">Zapytania często obliczać <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> lub <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="886f2-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="886f2-106">Kolekcje można przekazać <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiekty do <xref:System.Xml.Linq.XElement> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="886f2-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="886f2-107">W związku z tym jest wygodne do przekazania wyników zapytania jako zawartość do metody i konstruktory używanych do wypełnienia drzew XML.</span><span class="sxs-lookup"><span data-stu-id="886f2-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="886f2-108">Podczas dodawania zawartości prostej, różnych typów mogą być przekazywane do tej metody.</span><span class="sxs-lookup"><span data-stu-id="886f2-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="886f2-109">Prawidłowe typy:</span><span class="sxs-lookup"><span data-stu-id="886f2-109">Valid types include the following:</span></span>  
  
-   <xref:System.String>  
  
-   <xref:System.Double>  
  
-   <xref:System.Single>  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Boolean>  
  
-   <xref:System.DateTime>  
  
-   <xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset>  
  
-   <span data-ttu-id="886f2-110">Dowolnego typu, który implementuje `Object.ToString`.</span><span class="sxs-lookup"><span data-stu-id="886f2-110">Any type that implements `Object.ToString`.</span></span>  
  
-   <span data-ttu-id="886f2-111">Dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="886f2-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="886f2-112">Podczas dodawania zawartości złożonej, różne typy mogą zostać przekazane do tej metody:</span><span class="sxs-lookup"><span data-stu-id="886f2-112">When adding complex content, various types can be passed to this method:</span></span>  
  
-   <xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   <span data-ttu-id="886f2-113">Dowolnego typu, który implementuje<xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="886f2-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="886f2-114">Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>wyliczeniu kolekcji w obiekcie i zostaną dodane wszystkie elementy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="886f2-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="886f2-115">Jeśli kolekcja zawiera <xref:System.Xml.Linq.XNode> lub <xref:System.Xml.Linq.XAttribute> obiekty oddzielnie dodaniu każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="886f2-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="886f2-116">Jeśli kolekcja zawiera tekst (lub obiektów, które są konwertowane na tekst), tekst w kolekcji jest połączony i dodać jako węzeł jeden tekst.</span><span class="sxs-lookup"><span data-stu-id="886f2-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="886f2-117">Jeśli zawartość jest `null`, nic nie jest dodane.</span><span class="sxs-lookup"><span data-stu-id="886f2-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="886f2-118">Podczas przekazywania kolekcji elementów w kolekcji może być `null`.</span><span class="sxs-lookup"><span data-stu-id="886f2-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="886f2-119">A `null` elementu w kolekcji nie ma wpływu na drzewie.</span><span class="sxs-lookup"><span data-stu-id="886f2-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="886f2-120">Dodano atrybut musi mieć unikatową nazwę w ramach jego elementu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="886f2-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="886f2-121">Podczas dodawania <xref:System.Xml.Linq.XNode> lub <xref:System.Xml.Linq.XAttribute> obiekty, jeśli nowa zawartość nie ma elementu nadrzędnego, następnie obiekty są po prostu dołączone do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="886f2-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="886f2-122">Jeśli nowa zawartość jest elementem nadrzędnym, a jest częścią innego drzewa XML, następnie nowej zawartości został sklonowany, a zawartość nowo sklonowanego jest dołączony do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="886f2-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="886f2-123">Nieprawidłowa zawartość dokumentów</span><span class="sxs-lookup"><span data-stu-id="886f2-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="886f2-124">Atrybuty i prostej zawartości nie można dodać do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="886f2-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="886f2-125">Nie ma wiele scenariuszy, które wymagają utworzenia <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="886f2-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="886f2-126">Zamiast tego zazwyczaj można utworzyć z drzewa XML z <xref:System.Xml.Linq.XElement> węzła głównego.</span><span class="sxs-lookup"><span data-stu-id="886f2-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="886f2-127">Jeśli nie ma określonych wymagań można utworzyć dokumentu (na przykład dlatego należy utworzyć instrukcji przetwarzania i komentarze na najwyższym poziomie lub ma do obsługi typów dokumentu), jest często bardziej wygodne <xref:System.Xml.Linq.XElement> jako węzeł główny.</span><span class="sxs-lookup"><span data-stu-id="886f2-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="886f2-128">Nieprawidłowa zawartość dokumentu obejmuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="886f2-128">Valid content for a document includes the following:</span></span>  
  
-   <span data-ttu-id="886f2-129">Zero lub jeden <xref:System.Xml.Linq.XDocumentType> obiektów.</span><span class="sxs-lookup"><span data-stu-id="886f2-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="886f2-130">Typy dokumentów musi występować przed elementem.</span><span class="sxs-lookup"><span data-stu-id="886f2-130">The document types must come before the element.</span></span>  
  
-   <span data-ttu-id="886f2-131">Zero lub jeden element.</span><span class="sxs-lookup"><span data-stu-id="886f2-131">Zero or one element.</span></span>  
  
-   <span data-ttu-id="886f2-132">Komentarze do zera lub większej.</span><span class="sxs-lookup"><span data-stu-id="886f2-132">Zero or more comments.</span></span>  
  
-   <span data-ttu-id="886f2-133">Zero lub więcej instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="886f2-133">Zero or more processing instructions.</span></span>  
  
-   <span data-ttu-id="886f2-134">Zero lub więcej węzły tekstowe, które zawierają tylko puste miejsca.</span><span class="sxs-lookup"><span data-stu-id="886f2-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="886f2-135">Konstruktory i funkcje, które umożliwiają dodawanie zawartości</span><span class="sxs-lookup"><span data-stu-id="886f2-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="886f2-136">Następujące metody umożliwiają dodawanie zawartość elementu podrzędnego do <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="886f2-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="886f2-137">Metoda</span><span class="sxs-lookup"><span data-stu-id="886f2-137">Method</span></span>|<span data-ttu-id="886f2-138">Opis</span><span class="sxs-lookup"><span data-stu-id="886f2-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="886f2-139">Konstruuje <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="886f2-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="886f2-140">Konstruuje <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="886f2-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="886f2-141">Dodaje na końcu zawartości elementu podrzędnego <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="886f2-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="886f2-142">Dodaje zawartość po <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="886f2-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="886f2-143">Dodaje zawartość przed <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="886f2-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="886f2-144">Dodaje zawartość na początku elementu podrzędnego zawartości <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="886f2-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="886f2-145">Zamienia całą zawartość (węzły podrzędne i atrybuty) z <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="886f2-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="886f2-146">Zastępuje atrybuty <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="886f2-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="886f2-147">Węzły podrzędne są zastępowane nową zawartość.</span><span class="sxs-lookup"><span data-stu-id="886f2-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="886f2-148">Zamienia węzła nową zawartość.</span><span class="sxs-lookup"><span data-stu-id="886f2-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="886f2-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="886f2-149">See Also</span></span>  
 [<span data-ttu-id="886f2-150">Tworzenie drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="886f2-150">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
