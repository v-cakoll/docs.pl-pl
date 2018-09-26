---
title: Nieprawidłowa zawartość XElement i XDocument Objects3
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: afaeed7ba49891380982ec9c3cade43574ab8c16
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170564"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="5ab8e-102">Weryfikowanie zawartości obiektów XElement i XDocument</span><span class="sxs-lookup"><span data-stu-id="5ab8e-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="5ab8e-103">W tym temacie opisano prawidłowe argumenty, które mogą być przekazywane do konstruktorów i metod, których używasz do dodawania zawartości do elementów i dokumentów.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="5ab8e-104">Nieprawidłowa zawartość</span><span class="sxs-lookup"><span data-stu-id="5ab8e-104">Valid Content</span></span>  
 <span data-ttu-id="5ab8e-105">Zapytania często zwrócić <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> lub <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="5ab8e-106">Można przekazać kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiekty do <xref:System.Xml.Linq.XElement> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="5ab8e-107">Dlatego jest wygodne do przekazania wyników zapytania jako zawartość do metod i konstruktorów, używanych do wypełnienia drzew XML.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="5ab8e-108">Podczas dodawania zawartość, proste, różne typy mogą być przekazywane do tej metody.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="5ab8e-109">Prawidłowe typy:</span><span class="sxs-lookup"><span data-stu-id="5ab8e-109">Valid types include the following:</span></span>  
  
-   <xref:System.String>  
  
-   <xref:System.Double>  
  
-   <xref:System.Single>  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Boolean>  
  
-   <xref:System.DateTime>  
  
-   <xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset>  
  
-   <span data-ttu-id="5ab8e-110">Dowolny typ, który implementuje `Object.ToString`.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-110">Any type that implements `Object.ToString`.</span></span>  
  
-   <span data-ttu-id="5ab8e-111">Dowolny typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="5ab8e-112">Podczas dodawania zawartości złożonej, różnych typów można przekazany do tej metody:</span><span class="sxs-lookup"><span data-stu-id="5ab8e-112">When adding complex content, various types can be passed to this method:</span></span>  
  
-   <xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   <span data-ttu-id="5ab8e-113">Dowolny typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="5ab8e-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="5ab8e-114">Jeśli obiekt implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>, są wyliczane kolekcji w obiekcie, a wszystkie elementy w kolekcji są dodawane.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="5ab8e-115">Jeśli kolekcja zawiera <xref:System.Xml.Linq.XNode> lub <xref:System.Xml.Linq.XAttribute> obiektów, każdy element w kolekcji zostanie dodany osobno.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="5ab8e-116">Jeśli kolekcja zawiera tekst (lub obiektów, które są konwertowane na tekst), tekst w kolekcji jest połączonych i dodać jako węzeł w jeden tekst.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="5ab8e-117">Jeśli zawartość jest `null`, nic nie zostanie dodany.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="5ab8e-118">Podczas przekazywania kolekcję elementów w kolekcji może być `null`.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="5ab8e-119">Element `null` elementu w kolekcji nie ma wpływu na drzewie.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="5ab8e-120">Dodano atrybut musi mieć unikatową nazwę w ramach jego elemencie zawierającego.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="5ab8e-121">Podczas dodawania <xref:System.Xml.Linq.XNode> lub <xref:System.Xml.Linq.XAttribute> obiektów, jeśli nowa zawartość nie ma elementu nadrzędnego, następnie obiekty są po prostu dołączone do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="5ab8e-122">Jeśli nowa zawartość jest elementem nadrzędnym, a jest częścią innego drzewa XML, następnie został sklonowany nowej zawartości, a nowo sklonowanego zawartości jest dołączony do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="5ab8e-123">Nieprawidłowa zawartość dokumentów</span><span class="sxs-lookup"><span data-stu-id="5ab8e-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="5ab8e-124">Atrybuty i prostej zawartości nie można dodać do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="5ab8e-125">Nie są wiele scenariuszy, w których konieczna utworzyć <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="5ab8e-126">Zamiast tego można utworzyć zwykle z drzewa XML z <xref:System.Xml.Linq.XElement> węzła głównego.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="5ab8e-127">Jeśli nie masz określonych wymagań można utworzyć dokumentu, (na przykład dlatego, że należy utworzyć instrukcje przetwarzania i komentarze na najwyższym poziomie lub masz obsługę typów dokumentów), jest często bardziej wygodny w użyciu <xref:System.Xml.Linq.XElement> jako węzeł główny.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="5ab8e-128">Nieprawidłowa zawartość dokumentu obejmuje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="5ab8e-128">Valid content for a document includes the following:</span></span>  
  
-   <span data-ttu-id="5ab8e-129">Zero lub jeden <xref:System.Xml.Linq.XDocumentType> obiektów.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="5ab8e-130">Typy dokumentów musi występować przed elementem.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-130">The document types must come before the element.</span></span>  
  
-   <span data-ttu-id="5ab8e-131">Zero lub jeden element.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-131">Zero or one element.</span></span>  
  
-   <span data-ttu-id="5ab8e-132">Zero lub więcej komentarzy.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-132">Zero or more comments.</span></span>  
  
-   <span data-ttu-id="5ab8e-133">Zero lub więcej instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-133">Zero or more processing instructions.</span></span>  
  
-   <span data-ttu-id="5ab8e-134">Zero lub więcej węzły tekstowe, które zawierają tylko białe miejsca.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="5ab8e-135">Konstruktory i funkcje, które umożliwiają dodawanie zawartości</span><span class="sxs-lookup"><span data-stu-id="5ab8e-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="5ab8e-136">Następujące metody umożliwiają dodanie zawartość elementu podrzędnego do <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>:</span><span class="sxs-lookup"><span data-stu-id="5ab8e-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="5ab8e-137">Metoda</span><span class="sxs-lookup"><span data-stu-id="5ab8e-137">Method</span></span>|<span data-ttu-id="5ab8e-138">Opis</span><span class="sxs-lookup"><span data-stu-id="5ab8e-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="5ab8e-139">Konstruuje <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="5ab8e-140">Konstruuje <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="5ab8e-141">Dodaje do końca zawartość elementu podrzędnego <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="5ab8e-142">Dodaje zawartość po <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="5ab8e-143">Dodaje zawartość przed <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="5ab8e-144">Dodaje zawartość na początku zawartość elementu podrzędnego <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="5ab8e-145">Zastępuje całą zawartość (węzły podrzędne i atrybuty) <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="5ab8e-146">Zastępuje atrybuty <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="5ab8e-147">Zamienia węzłów podrzędnych nowej zawartości.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="5ab8e-148">Zamienia węzeł nowej zawartości.</span><span class="sxs-lookup"><span data-stu-id="5ab8e-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ab8e-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ab8e-149">See Also</span></span>

- [<span data-ttu-id="5ab8e-150">Tworzenie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5ab8e-150">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
