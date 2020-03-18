---
title: Prawidłowa zawartość obiektów XElement i XDocument3
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: 1ad5b18e3bbc2143a56f9c8e7b34354761b4e42f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590936"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="df3ee-102">Weryfikowanie zawartości obiektów XElement i XDocument</span><span class="sxs-lookup"><span data-stu-id="df3ee-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="df3ee-103">W tym temacie opisano prawidłowe argumenty, które mogą być przekazywane do konstruktorów i metod, które są używane do dodawania zawartości do elementów i dokumentów.</span><span class="sxs-lookup"><span data-stu-id="df3ee-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="df3ee-104">Prawidłowa zawartość</span><span class="sxs-lookup"><span data-stu-id="df3ee-104">Valid Content</span></span>  
 <span data-ttu-id="df3ee-105">Zapytania często <xref:System.Collections.Generic.IEnumerable%601> oceniają <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute>do lub z <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="df3ee-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="df3ee-106">Kolekcje <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiekty można <xref:System.Xml.Linq.XElement> przekazać do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="df3ee-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="df3ee-107">W związku z tym jest wygodne, aby przekazać wyniki kwerendy jako zawartość do metod i konstruktorów, które są używane do wypełniania drzew XML.</span><span class="sxs-lookup"><span data-stu-id="df3ee-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="df3ee-108">Podczas dodawania zawartości prostej, różne typy mogą być przekazywane do tej metody.</span><span class="sxs-lookup"><span data-stu-id="df3ee-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="df3ee-109">Prawidłowe typy są następujące:</span><span class="sxs-lookup"><span data-stu-id="df3ee-109">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="df3ee-110">Dowolny typ, `Object.ToString`który implementuje .</span><span class="sxs-lookup"><span data-stu-id="df3ee-110">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="df3ee-111">Dowolny typ, <xref:System.Collections.Generic.IEnumerable%601>który implementuje .</span><span class="sxs-lookup"><span data-stu-id="df3ee-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="df3ee-112">Podczas dodawania złożonej zawartości do tej metody można przekazać różne typy:</span><span class="sxs-lookup"><span data-stu-id="df3ee-112">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="df3ee-113">Każdy typ implementuje<xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="df3ee-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="df3ee-114">Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekcja w obiekcie jest wyliczana, a wszystkie elementy w kolekcji są dodawane.</span><span class="sxs-lookup"><span data-stu-id="df3ee-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="df3ee-115">Jeśli kolekcja <xref:System.Xml.Linq.XNode> zawiera <xref:System.Xml.Linq.XAttribute> lub obiektów, każdy element w kolekcji jest dodawany oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="df3ee-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="df3ee-116">Jeśli kolekcja zawiera tekst (lub obiekty, które są konwertowane na tekst), tekst w kolekcji jest połączony i dodany jako węzeł pojedynczego tekstu.</span><span class="sxs-lookup"><span data-stu-id="df3ee-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="df3ee-117">Jeśli zawartość `null`jest , nic nie jest dodawane.</span><span class="sxs-lookup"><span data-stu-id="df3ee-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="df3ee-118">Podczas przekazywania elementów kolekcji w `null`kolekcji może być .</span><span class="sxs-lookup"><span data-stu-id="df3ee-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="df3ee-119">Element `null` w kolekcji nie ma wpływu na drzewo.</span><span class="sxs-lookup"><span data-stu-id="df3ee-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="df3ee-120">Dodany atrybut musi mieć unikatową nazwę w jego element zawierający.</span><span class="sxs-lookup"><span data-stu-id="df3ee-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="df3ee-121">Podczas <xref:System.Xml.Linq.XNode> dodawania lub <xref:System.Xml.Linq.XAttribute> obiektów, jeśli nowa zawartość nie ma nadrzędnego, obiekty są po prostu dołączone do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="df3ee-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="df3ee-122">Jeśli nowa zawartość jest już nadrzędna i jest częścią innego drzewa XML, nowa zawartość jest klonowana, a nowo sklonowana zawartość jest dołączona do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="df3ee-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="df3ee-123">Prawidłowa zawartość dokumentów</span><span class="sxs-lookup"><span data-stu-id="df3ee-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="df3ee-124">Atrybutów i prostej zawartości nie można dodać do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="df3ee-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="df3ee-125">Nie ma wielu scenariuszy, które <xref:System.Xml.Linq.XDocument>wymagają utworzenia pliku .</span><span class="sxs-lookup"><span data-stu-id="df3ee-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="df3ee-126">Zamiast tego zazwyczaj można utworzyć drzewa <xref:System.Xml.Linq.XElement> XML z węzłem głównym.</span><span class="sxs-lookup"><span data-stu-id="df3ee-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="df3ee-127">Jeśli nie masz określonego wymogu utworzenia dokumentu (na przykład dlatego, że musisz utworzyć instrukcje przetwarzania i komentarze na najwyższym poziomie lub <xref:System.Xml.Linq.XElement> musisz obsługiwać typy dokumentów), często wygodniej jest używać jako węzła głównego.</span><span class="sxs-lookup"><span data-stu-id="df3ee-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="df3ee-128">Prawidłowa zawartość dokumentu zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="df3ee-128">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="df3ee-129">Zero lub <xref:System.Xml.Linq.XDocumentType> jeden obiekt.</span><span class="sxs-lookup"><span data-stu-id="df3ee-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="df3ee-130">Typy dokumentów muszą znajdować się przed elementem.</span><span class="sxs-lookup"><span data-stu-id="df3ee-130">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="df3ee-131">Zero lub jeden element.</span><span class="sxs-lookup"><span data-stu-id="df3ee-131">Zero or one element.</span></span>  
  
- <span data-ttu-id="df3ee-132">Zero lub więcej komentarzy.</span><span class="sxs-lookup"><span data-stu-id="df3ee-132">Zero or more comments.</span></span>  
  
- <span data-ttu-id="df3ee-133">Zero lub więcej instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="df3ee-133">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="df3ee-134">Zero lub więcej węzłów tekstowych, które zawierają tylko biały znak.</span><span class="sxs-lookup"><span data-stu-id="df3ee-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="df3ee-135">Konstruktory i funkcje umożliwiające dodawanie zawartości</span><span class="sxs-lookup"><span data-stu-id="df3ee-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="df3ee-136">Następujące metody umożliwiają dodawanie zawartości podrzędnej <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>do zawartości podrzędnej lub :</span><span class="sxs-lookup"><span data-stu-id="df3ee-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="df3ee-137">Metoda</span><span class="sxs-lookup"><span data-stu-id="df3ee-137">Method</span></span>|<span data-ttu-id="df3ee-138">Opis</span><span class="sxs-lookup"><span data-stu-id="df3ee-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="df3ee-139">Konstruuje <xref:System.Xml.Linq.XElement>plik .</span><span class="sxs-lookup"><span data-stu-id="df3ee-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="df3ee-140">Konstruuje <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="df3ee-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="df3ee-141">Dodaje na końcu zawartości <xref:System.Xml.Linq.XElement> podrzędnej <xref:System.Xml.Linq.XDocument>lub .</span><span class="sxs-lookup"><span data-stu-id="df3ee-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="df3ee-142">Dodaje zawartość <xref:System.Xml.Linq.XNode>po pliku .</span><span class="sxs-lookup"><span data-stu-id="df3ee-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="df3ee-143">Dodaje zawartość <xref:System.Xml.Linq.XNode>przed .</span><span class="sxs-lookup"><span data-stu-id="df3ee-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="df3ee-144">Dodaje zawartość na początku zawartości podrzędnej pliku <xref:System.Xml.Linq.XContainer>.</span><span class="sxs-lookup"><span data-stu-id="df3ee-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="df3ee-145">Zastępuje całą zawartość (węzły podrzędne <xref:System.Xml.Linq.XElement>i atrybuty) pliku .</span><span class="sxs-lookup"><span data-stu-id="df3ee-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="df3ee-146">Zastępuje atrybuty pliku <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="df3ee-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="df3ee-147">Zastępuje węzły podrzędne nową zawartością.</span><span class="sxs-lookup"><span data-stu-id="df3ee-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="df3ee-148">Zastępuje węzeł nową zawartością.</span><span class="sxs-lookup"><span data-stu-id="df3ee-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df3ee-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df3ee-149">See also</span></span>

- [<span data-ttu-id="df3ee-150">Tworzenie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="df3ee-150">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
