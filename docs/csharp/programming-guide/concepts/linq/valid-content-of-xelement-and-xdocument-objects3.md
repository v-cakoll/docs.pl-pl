---
title: Prawidłowa zawartość elementów XElement i XDocument Objects3
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: 1ad5b18e3bbc2143a56f9c8e7b34354761b4e42f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590936"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="3f5b9-102">Weryfikowanie zawartości obiektów XElement i XDocument</span><span class="sxs-lookup"><span data-stu-id="3f5b9-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="3f5b9-103">W tym temacie opisano prawidłowe argumenty, które mogą być przekazane do konstruktorów i metod, które są używane do dodawania zawartości do elementów i dokumentów.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="3f5b9-104">Prawidłowa zawartość</span><span class="sxs-lookup"><span data-stu-id="3f5b9-104">Valid Content</span></span>  
 <span data-ttu-id="3f5b9-105">Zapytania często są oceniane <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> lub <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="3f5b9-106">Można przekazać kolekcje <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiekty do <xref:System.Xml.Linq.XElement> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="3f5b9-107">Z tego względu wygodnie jest przekazać wyniki zapytania jako zawartość do metod i konstruktorów używanych do wypełniania drzew XML.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="3f5b9-108">Podczas dodawania prostej zawartości można przekazywać różne typy do tej metody.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="3f5b9-109">Prawidłowe typy to:</span><span class="sxs-lookup"><span data-stu-id="3f5b9-109">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="3f5b9-110">Dowolny typ, który `Object.ToString`implementuje.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-110">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="3f5b9-111">Dowolny typ, który <xref:System.Collections.Generic.IEnumerable%601>implementuje.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="3f5b9-112">Podczas dodawania złożonej zawartości można przekazywać różne typy do tej metody:</span><span class="sxs-lookup"><span data-stu-id="3f5b9-112">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="3f5b9-113">Dowolny typ, który implementuje<xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="3f5b9-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="3f5b9-114">Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekcja w obiekcie jest wyliczana i dodawane są wszystkie elementy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="3f5b9-115">Jeśli kolekcja zawiera <xref:System.Xml.Linq.XNode> obiekty lub <xref:System.Xml.Linq.XAttribute> , każdy element w kolekcji zostanie dodany osobno.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="3f5b9-116">Jeśli kolekcja zawiera tekst (lub obiekty, które są konwertowane na tekst), tekst w kolekcji zostanie połączony i dodany jako pojedynczy węzeł tekstowy.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="3f5b9-117">Jeśli zawartość jest `null`, nic nie jest dodawane.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="3f5b9-118">Przekazywanie elementów kolekcji w kolekcji może być `null`możliwe.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="3f5b9-119">`null` Element w kolekcji nie ma wpływu na drzewo.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="3f5b9-120">Dodany atrybut musi mieć unikatową nazwę w obrębie zawartego elementu.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="3f5b9-121">W przypadku <xref:System.Xml.Linq.XNode> dodawania <xref:System.Xml.Linq.XAttribute> lub obiektów, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty są po prostu dołączone do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="3f5b9-122">Jeśli nowa zawartość jest już nadrzędna i jest częścią innego drzewa XML, Nowa zawartość jest klonowana, a nowo sklonowana zawartość jest dołączona do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="3f5b9-123">Prawidłowa zawartość dla dokumentów</span><span class="sxs-lookup"><span data-stu-id="3f5b9-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="3f5b9-124">Atrybuty i zawartość prosta nie mogą zostać dodane do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="3f5b9-125">Istnieje wiele scenariuszy, które wymagają utworzenia <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="3f5b9-126">Zamiast tego można zazwyczaj utworzyć drzewa XML z <xref:System.Xml.Linq.XElement> węzłem głównym.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="3f5b9-127">Jeśli użytkownik nie ma konkretnego wymagania dotyczącego tworzenia dokumentu (na przykład dlatego, że konieczne jest utworzenie instrukcji przetwarzania i komentarzy na najwyższym poziomie lub konieczność obsługi typów dokumentów), często jest wygodniejszy do użycia <xref:System.Xml.Linq.XElement> jako węzeł główny.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="3f5b9-128">Prawidłowa zawartość dla dokumentu zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="3f5b9-128">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="3f5b9-129">Zero lub jeden <xref:System.Xml.Linq.XDocumentType> obiekt.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="3f5b9-130">Typy dokumentów muszą występować przed elementem.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-130">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="3f5b9-131">Zero lub jeden element.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-131">Zero or one element.</span></span>  
  
- <span data-ttu-id="3f5b9-132">Zero lub więcej komentarzy.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-132">Zero or more comments.</span></span>  
  
- <span data-ttu-id="3f5b9-133">Zero lub więcej instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-133">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="3f5b9-134">Zero lub więcej węzłów tekstowych, które zawierają tylko biały znak.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="3f5b9-135">Konstruktory i funkcje, które umożliwiają dodawanie zawartości</span><span class="sxs-lookup"><span data-stu-id="3f5b9-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="3f5b9-136">Poniższe metody pozwalają dodać zawartość podrzędną do elementu <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>lub:</span><span class="sxs-lookup"><span data-stu-id="3f5b9-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="3f5b9-137">Metoda</span><span class="sxs-lookup"><span data-stu-id="3f5b9-137">Method</span></span>|<span data-ttu-id="3f5b9-138">Opis</span><span class="sxs-lookup"><span data-stu-id="3f5b9-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="3f5b9-139">Konstruuje <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="3f5b9-140">Konstruuje <xref:System.Xml.Linq.XDocument>a.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="3f5b9-141">Dodaje do końca zawartości <xref:System.Xml.Linq.XElement> podrzędnej lub. <xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="3f5b9-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="3f5b9-142">Dodaje zawartość po <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="3f5b9-143">Dodaje zawartość przed <xref:System.Xml.Linq.XNode>.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="3f5b9-144">Dodaje zawartość na początku zawartości <xref:System.Xml.Linq.XContainer>podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="3f5b9-145">Zamienia całą zawartość (węzły podrzędne i atrybuty) obiektu <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="3f5b9-146">Zastępuje atrybuty <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="3f5b9-147">Zamienia węzły podrzędne na nową zawartość.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="3f5b9-148">Zamienia węzeł na nową zawartość.</span><span class="sxs-lookup"><span data-stu-id="3f5b9-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f5b9-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f5b9-149">See also</span></span>

- [<span data-ttu-id="3f5b9-150">Tworzenie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3f5b9-150">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
