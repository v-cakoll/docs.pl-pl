---
title: Wczytywanie deklaracji jednostek i odwołań do jednostek do modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e30b52b8cdfb4d185687d58c80f4475730031c86
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45748684"
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="a2577-102">Wczytywanie deklaracji jednostek i odwołań do jednostek do modelu DOM</span><span class="sxs-lookup"><span data-stu-id="a2577-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="a2577-103">Jednostka jest deklaracja, która stanowi nazwę do użycia w formacie XML, zamiast zawartości lub znaczników.</span><span class="sxs-lookup"><span data-stu-id="a2577-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="a2577-104">Istnieją dwie części do jednostek.</span><span class="sxs-lookup"><span data-stu-id="a2577-104">There are two parts to entities.</span></span> <span data-ttu-id="a2577-105">Najpierw należy powiązać nazwę, aby nowa zawartość przy użyciu deklaracji entity.</span><span class="sxs-lookup"><span data-stu-id="a2577-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="a2577-106">Deklaracja jednostki jest tworzona przy użyciu `<!ENTITY name "value">` składni w definicji typu dokumentu (DTD) lub schematu XML.</span><span class="sxs-lookup"><span data-stu-id="a2577-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="a2577-107">Po drugie z nazwą zdefiniowaną w deklaracji jednostki są następnie używane w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="a2577-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="a2577-108">W przypadku użycia w pliku XML, jest on nazywany odwołania do jednostki.</span><span class="sxs-lookup"><span data-stu-id="a2577-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="a2577-109">Na przykład następująca deklaracja jednostki deklaruje jednostki o nazwie `publisher` skojarzona z zawartością "Microsoft Press".</span><span class="sxs-lookup"><span data-stu-id="a2577-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="a2577-110">Poniższy przykład pokazuje użycie tej deklaracji jednostki w formacie XML, jako odwołanie do jednostki.</span><span class="sxs-lookup"><span data-stu-id="a2577-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="a2577-111">Niektóre parsery rozwiń jednostek automatycznie, gdy dokument jest ładowany do pamięci.</span><span class="sxs-lookup"><span data-stu-id="a2577-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="a2577-112">W związku z tym podczas odczytywania pliku XML do pamięci, deklaracje jednostki zostaną zapamiętane i zapisane.</span><span class="sxs-lookup"><span data-stu-id="a2577-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="a2577-113">Gdy analizator składni napotka później `&;` znaków, które należy zidentyfikować ogólne odwołanie do jednostki, analizator odwołuje się do tej nazwy tabeli deklaracji entity.</span><span class="sxs-lookup"><span data-stu-id="a2577-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="a2577-114">Odwołanie, `&publisher;` zastępuje zawartości, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="a2577-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="a2577-115">Za pomocą następujący kod XML</span><span class="sxs-lookup"><span data-stu-id="a2577-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="a2577-116">rozwijanie odwołania do jednostki i zastępując `&publisher;` Microsoft Press zawartości zapewnia następujący kod XML rozwinięty.</span><span class="sxs-lookup"><span data-stu-id="a2577-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="a2577-117">**Output**</span><span class="sxs-lookup"><span data-stu-id="a2577-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="a2577-118">Istnieje wiele rodzajów jednostek.</span><span class="sxs-lookup"><span data-stu-id="a2577-118">There are many kinds of entities.</span></span> <span data-ttu-id="a2577-119">Na poniższym diagramie przedstawiono podział typów jednostek i terminologia.</span><span class="sxs-lookup"><span data-stu-id="a2577-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="a2577-120">![Schemat blokowy hierarchii typów jednostek](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="a2577-120">![flow chart of entity type hierarchy](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="a2577-121">Wartość domyślna dla implementacji Microsoft .NET Framework XML Document Object Model (DOM) jest zachowanie odwołania jednostki i Rozwijaj jednostki po załadowaniu pliku XML.</span><span class="sxs-lookup"><span data-stu-id="a2577-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="a2577-122">Domniemanie tego jest to, że ponieważ dokument został załadowany w modelu DOM, **XmlEntityReference** węzła zawierającego zmienną odwołania `&publisher;` jest tworzone, z węzłami podrzędnymi reprezentujących zawartości jednostki zadeklarowanych w DTD.</span><span class="sxs-lookup"><span data-stu-id="a2577-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="a2577-123">Za pomocą `<!ENTITY publisher "Microsoft Press">` deklaracji jednostki na poniższym diagramie przedstawiono **XmlEntity** i **XmlText** węzłów przygotowane na podstawie tej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="a2577-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="a2577-124">![węzłów przygotowane na podstawie jednostki deklaracji](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="a2577-124">![nodes created from entity declaration](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="a2577-125">Różnice podczas odwołań do jednostek zostaną rozwinięte i nie są one sprawia, że różnica w jakie węzły są generowane w drzewie DOM w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a2577-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="a2577-126">Różnica w węzły, które są generowane zostało wyjaśnione w tematach [odwołań do jednostek są zachowywane](../../../../docs/standard/data/xml/entity-references-are-preserved.md) i [odwołań do jednostek są rozwinięte i nie jest zachowywana](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="a2577-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](../../../../docs/standard/data/xml/entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2577-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2577-127">See also</span></span>

- [<span data-ttu-id="a2577-128">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="a2577-128">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
