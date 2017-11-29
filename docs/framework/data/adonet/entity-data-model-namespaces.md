---
title: 'Modelu danych jednostki: przestrzenie nazw'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e473453576f04e89b58806c5140e29855d7d022
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="ef10b-102">Modelu danych jednostki: przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="ef10b-102">Entity Data Model: Namespaces</span></span>
<span data-ttu-id="ef10b-103">Przestrzeń nazw w modelu danych jednostki (EDM) jest abstrakcyjny kontener dla [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md), [typów złożonych](../../../../docs/framework/data/adonet/complex-type.md), i [skojarzenia](../../../../docs/framework/data/adonet/association-type.md).</span><span class="sxs-lookup"><span data-stu-id="ef10b-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](../../../../docs/framework/data/adonet/entity-type.md), [complex types](../../../../docs/framework/data/adonet/complex-type.md), and [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="ef10b-104">Przestrzenie nazw w EDM są podobne do przestrzeni nazw w języku programowania: stanowią kontekst dla obiektów, które zawierają i umożliwiają do odróżniania obiektów, które mają taką samą nazwę (ale znajdują się w różnych przestrzeniach nazw).</span><span class="sxs-lookup"><span data-stu-id="ef10b-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef10b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef10b-105">Example</span></span>  
 <span data-ttu-id="ef10b-106">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="ef10b-106">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ef10b-107">Następujący kod w pliku CSDL używa przestrzeni nazw do identyfikacji typu, który jest zdefiniowany w różnych modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="ef10b-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="ef10b-108">W przykładzie zdefiniowano typ jednostki (`Publisher`) mający właściwość typu złożonego (`Address`) importowanym z `ExtendedBooksModel` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ef10b-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="ef10b-109">Należy pamiętać, że `Using` element wskazuje, że przestrzeni nazw zostały zaimportowane.</span><span class="sxs-lookup"><span data-stu-id="ef10b-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="ef10b-110">Należy również zauważyć, że typ `Address` właściwość jest zdefiniowana przy użyciu w pełni kwalifikowanej nazwy (`ExtendedBooksModel.Address`), co oznacza, że ten typ jest zdefiniowany w `ExtendedBooksModel` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ef10b-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="ef10b-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef10b-111">See Also</span></span>  
 [<span data-ttu-id="ef10b-112">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="ef10b-112">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="ef10b-113">Modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="ef10b-113">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
