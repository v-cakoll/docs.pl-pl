---
title: "Odczytywanie deklaracje jednostki i odwołań do jednostek w modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86dba977-5cc4-4567-964f-027ffabc47b2
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6370db06cbe7ff8d46258b0315059f5c37587fea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="reading-entity-declarations-and-entity-references-into-the-dom"></a><span data-ttu-id="328bd-102">Odczytywanie deklaracje jednostki i odwołań do jednostek w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="328bd-102">Reading Entity Declarations and Entity References into the DOM</span></span>
<span data-ttu-id="328bd-103">Jednostka jest deklaracją informującą Nazwa do użycia w kodzie XML zamiast zawartości lub znaczników.</span><span class="sxs-lookup"><span data-stu-id="328bd-103">An entity is a declaration that states a name to be used in the XML in place of content or markup.</span></span> <span data-ttu-id="328bd-104">Istnieją dwie części jednostek.</span><span class="sxs-lookup"><span data-stu-id="328bd-104">There are two parts to entities.</span></span> <span data-ttu-id="328bd-105">Najpierw należy powiązanie nazwę, aby nowa zawartość za pomocą deklaracji entity.</span><span class="sxs-lookup"><span data-stu-id="328bd-105">First, you must tie a name to the replacement content using an entity declaration.</span></span> <span data-ttu-id="328bd-106">Deklaracja jednostki jest tworzona przy użyciu `<!ENTITY name "value">` składni w definicji typu dokumentu (DTD) lub schematu XML.</span><span class="sxs-lookup"><span data-stu-id="328bd-106">An entity declaration is created by using the `<!ENTITY name "value">` syntax in a document type definition (DTD) or XML schema.</span></span> <span data-ttu-id="328bd-107">Po drugie z nazwą zdefiniowaną w deklaracji jednostki są następnie używane w kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="328bd-107">Secondly, the name defined in the entity declaration is subsequently used in the XML.</span></span> <span data-ttu-id="328bd-108">Używane w pliku XML, jest nazywany odwołania do jednostki.</span><span class="sxs-lookup"><span data-stu-id="328bd-108">When used in the XML, it is called an entity reference.</span></span> <span data-ttu-id="328bd-109">Na przykład następujące oświadczenie jednostka deklaruje jednostki nazwy `publisher` skojarzona z zawartością "Microsoft Press".</span><span class="sxs-lookup"><span data-stu-id="328bd-109">For example, the following entity declaration declares an entity of the name `publisher` being associated with the content of "Microsoft Press".</span></span>  
  
```xml  
<!ENTITY publisher "Microsoft Press">  
```  
  
 <span data-ttu-id="328bd-110">Poniższy przykład przedstawia użycie tej deklaracji jednostki w formacie XML jako odwołanie do jednostki.</span><span class="sxs-lookup"><span data-stu-id="328bd-110">The following example shows the use of this entity declaration in XML as an entity reference.</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="328bd-111">Niektóre analizatory składni rozwinąć jednostek automatycznie, gdy dokument jest ładowany do pamięci.</span><span class="sxs-lookup"><span data-stu-id="328bd-111">Some parsers automatically expand entities when a document is loaded into memory.</span></span> <span data-ttu-id="328bd-112">W związku z tym podczas odczytywania pliku XML do pamięci, deklaracje jednostki są zapamiętywane i zapisywane.</span><span class="sxs-lookup"><span data-stu-id="328bd-112">Therefore, when the XML is being read into memory, entity declarations are remembered and saved.</span></span> <span data-ttu-id="328bd-113">Gdy analizator następnie napotka `&;` znaków, które identyfikują ogólne odwołanie do jednostki, Analizator wyszukuje tę nazwę tabeli deklaracji entity.</span><span class="sxs-lookup"><span data-stu-id="328bd-113">When the parser subsequently encounters `&;` characters, which identify a general entity reference, the parser looks up that name in an entity declaration table.</span></span> <span data-ttu-id="328bd-114">Odwołanie, `&publisher;` zastępuje zawartość, która reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="328bd-114">The reference, `&publisher;` is replaced by the content that it represents.</span></span> <span data-ttu-id="328bd-115">Przy użyciu następującego pliku XML</span><span class="sxs-lookup"><span data-stu-id="328bd-115">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="328bd-116">Rozszerzanie odwołanie do jednostki i zastępowanie `&publisher;` z Microsoft Press zawartości zapewnia następujące rozwinięte XML.</span><span class="sxs-lookup"><span data-stu-id="328bd-116">expanding the entity reference and replacing the `&publisher;` with the Microsoft Press content gives the following expanded XML.</span></span>  
  
 <span data-ttu-id="328bd-117">**Dane wyjściowe**</span><span class="sxs-lookup"><span data-stu-id="328bd-117">**Output**</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by Microsoft Press</pubinfo>  
```  
  
 <span data-ttu-id="328bd-118">Istnieje wiele typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="328bd-118">There are many kinds of entities.</span></span> <span data-ttu-id="328bd-119">Poniższy diagram przedstawia podział typów jednostek i terminologię.</span><span class="sxs-lookup"><span data-stu-id="328bd-119">The following diagram shows the breakdown of entity types and terminology.</span></span>  
  
 <span data-ttu-id="328bd-120">![Schemat blokowy hierarchii typów jednostek](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="328bd-120">![flow chart of entity type hierarchy](../../../../docs/standard/data/xml/media/entity-hierarchy.gif "Entity_hierarchy")</span></span>  
  
 <span data-ttu-id="328bd-121">Wartość domyślna dla implementacji programu Microsoft .NET Framework z XML modelu DOM (Document Object) to zachowanie odwołań do jednostek i zwiększa jednostek po załadowaniu pliku XML.</span><span class="sxs-lookup"><span data-stu-id="328bd-121">The default for the Microsoft .NET Framework implementation of the XML Document Object Model (DOM) is to preserve the entities references and not expand the entities when the XML is loaded.</span></span> <span data-ttu-id="328bd-122">Wpływ na tego jest to, że zgodnie z dokumentem jest ładowany w modelu DOM, **XmlEntityReference** węzła odniesienia zmiennej zawierającego `&publisher;` jest utworzony, z węzłami podrzędnymi reprezentujący zawartości w jednostce zadeklarowany w definicji DTD.</span><span class="sxs-lookup"><span data-stu-id="328bd-122">The implication of this is that as a document is loaded in the DOM, an **XmlEntityReference** node containing the reference variable `&publisher;` is created, with child nodes representing the content in the entity declared in the DTD.</span></span>  
  
 <span data-ttu-id="328bd-123">Przy użyciu `<!ENTITY publisher "Microsoft Press">` deklaracji jednostki na poniższym diagramie przedstawiono **XmlEntity** i **XmlText** węzły utworzone na podstawie tej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="328bd-123">Using the `<!ENTITY publisher "Microsoft Press">` entity declaration, the following diagram shows the **XmlEntity** and **XmlText** nodes created from this declaration.</span></span>  
  
 <span data-ttu-id="328bd-124">![węzły utworzone na podstawie deklaracji jednostki](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span><span class="sxs-lookup"><span data-stu-id="328bd-124">![nodes created from entity declaration](../../../../docs/standard/data/xml/media/xml-entitydeclaration-node2.png "xml_entitydeclaration_node2")</span></span>  
  
 <span data-ttu-id="328bd-125">Różnice po rozwinięciu są odwołań do jednostek i jeśli nie są one sprawia, że różnica w węzłach, które są generowane w drzewie DOM w pamięci.</span><span class="sxs-lookup"><span data-stu-id="328bd-125">The differences when entity references are expanded and when they are not makes a difference in what nodes are generated in the DOM tree, in memory.</span></span> <span data-ttu-id="328bd-126">Różnica w węzłach, na których są generowane, znajduje się w tematach [odwołań do jednostek są zachowywane](../../../../docs/standard/data/xml/entity-references-are-preserved.md) i [odwołań do jednostek są rozwinięte i nie jest zachowywana](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span><span class="sxs-lookup"><span data-stu-id="328bd-126">The difference in the nodes that are generated is explained in the topics [Entity References are Preserved](../../../../docs/standard/data/xml/entity-references-are-preserved.md) and [Entity References are Expanded and Not Preserved](../../../../docs/standard/data/xml/entity-references-are-expanded-and-not-preserved.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="328bd-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="328bd-127">See Also</span></span>  
 [<span data-ttu-id="328bd-128">Modelu obiektu dokumentu XML modelu DOM)</span><span class="sxs-lookup"><span data-stu-id="328bd-128">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
