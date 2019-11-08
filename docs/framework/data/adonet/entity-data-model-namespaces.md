---
title: 'Entity Data Model: przestrzenie nazw'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: a403bcd459005ed9cea4a455fcde40c31c8caac9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738441"
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="64fb5-102">Entity Data Model: przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="64fb5-102">Entity Data Model: Namespaces</span></span>
<span data-ttu-id="64fb5-103">Przestrzeń nazw w Entity Data Model (EDM) jest kontenerem abstrakcyjnym dla [typów jednostek](entity-type.md), [typów złożonych](complex-type.md)i [skojarzeń](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="64fb5-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](entity-type.md), [complex types](complex-type.md), and [associations](association-type.md).</span></span> <span data-ttu-id="64fb5-104">Przestrzenie nazw w modelu EDM są podobne do przestrzeni nazw w języku programowania: zawierają kontekst dla obiektów, które zawierają i umożliwiają rozróżnianie obiektów, które mają taką samą nazwę (ale znajdują się w różnych obszarach nazw).</span><span class="sxs-lookup"><span data-stu-id="64fb5-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64fb5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="64fb5-105">Example</span></span>  
 <span data-ttu-id="64fb5-106">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="64fb5-106">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="64fb5-107">Poniższy kod CSDL używa przestrzeni nazw do identyfikowania typu, który jest zdefiniowany w innym modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="64fb5-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="64fb5-108">W przykładzie zdefiniowano typ jednostki (`Publisher`), który ma właściwość typu złożonego (`Address`) importowaną z przestrzeni nazw `ExtendedBooksModel`.</span><span class="sxs-lookup"><span data-stu-id="64fb5-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="64fb5-109">Należy zauważyć, że element `Using` wskazuje, że przestrzeń nazw została zaimportowana.</span><span class="sxs-lookup"><span data-stu-id="64fb5-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="64fb5-110">Należy również zauważyć, że typ właściwości `Address` jest zdefiniowany przy użyciu jej w pełni kwalifikowanej nazwy (`ExtendedBooksModel.Address`), co oznacza, że ten typ jest zdefiniowany w przestrzeni nazw `ExtendedBooksModel`.</span><span class="sxs-lookup"><span data-stu-id="64fb5-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="64fb5-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64fb5-111">See also</span></span>

- [<span data-ttu-id="64fb5-112">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="64fb5-112">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="64fb5-113">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="64fb5-113">Entity Data Model</span></span>](entity-data-model.md)
