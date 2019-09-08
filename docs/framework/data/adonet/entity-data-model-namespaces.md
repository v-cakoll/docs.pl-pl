---
title: 'Model danych jednostki: Namespaces'
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: a8629a1f162f5d942390f62d5a2ac20e2135c531
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784005"
---
# <a name="entity-data-model-namespaces"></a><span data-ttu-id="7cb15-102">Model danych jednostki: Namespaces</span><span class="sxs-lookup"><span data-stu-id="7cb15-102">Entity Data Model: Namespaces</span></span>
<span data-ttu-id="7cb15-103">Przestrzeń nazw w Entity Data Model (EDM) jest kontenerem abstrakcyjnym dla [typów jednostek](entity-type.md), [typów złożonych](complex-type.md)i [skojarzeń](association-type.md).</span><span class="sxs-lookup"><span data-stu-id="7cb15-103">A namespace in the Entity Data Model (EDM) is an abstract container for [entity types](entity-type.md), [complex types](complex-type.md), and [associations](association-type.md).</span></span> <span data-ttu-id="7cb15-104">Przestrzenie nazw w modelu EDM są podobne do przestrzeni nazw w języku programowania: zawierają kontekst dla obiektów, które zawierają i umożliwiają rozróżnianie obiektów, które mają taką samą nazwę (ale znajdują się w różnych obszarach nazw).</span><span class="sxs-lookup"><span data-stu-id="7cb15-104">Namespaces in the EDM are similar to namespaces in a programming language: they provide context for the objects that they contain and they provide a way to disambiguate objects that have the same name (but are contained in different namespaces).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cb15-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cb15-105">Example</span></span>  
 <span data-ttu-id="7cb15-106">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="7cb15-106">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="7cb15-107">Poniższy kod CSDL używa przestrzeni nazw do identyfikowania typu, który jest zdefiniowany w innym modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="7cb15-107">The following CSDL code uses a namespace to identify a type that is defined in a different conceptual model.</span></span> <span data-ttu-id="7cb15-108">W przykładzie zdefiniowano typ jednostki (`Publisher`), który ma właściwość typu złożonego`Address`() `ExtendedBooksModel` , która jest importowana z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7cb15-108">The example defines an entity type (`Publisher`) that has a complex type property (`Address`) that is imported from the `ExtendedBooksModel` namespace.</span></span> <span data-ttu-id="7cb15-109">Należy zauważyć, `Using` że element wskazuje, że przestrzeń nazw została zaimportowana.</span><span class="sxs-lookup"><span data-stu-id="7cb15-109">Note that the `Using` element indicates that a namespace has been imported.</span></span> <span data-ttu-id="7cb15-110">Należy również zauważyć, że typ `Address` właściwości jest zdefiniowany przy użyciu jego w pełni kwalifikowanej nazwy (`ExtendedBooksModel.Address`), co oznacza, że ten `ExtendedBooksModel` typ jest zdefiniowany w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7cb15-110">Also note that the type of the `Address` property is defined by using its fully qualified name (`ExtendedBooksModel.Address`), indicating that this type is defined in the `ExtendedBooksModel` namespace.</span></span>  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a><span data-ttu-id="7cb15-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cb15-111">See also</span></span>

- [<span data-ttu-id="7cb15-112">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="7cb15-112">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="7cb15-113">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="7cb15-113">Entity Data Model</span></span>](entity-data-model.md)
