---
title: property
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: d1e20a6570c458041ec5d8ececbfa291ca9e4612
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735393"
---
# <a name="property"></a><span data-ttu-id="aa9c4-102">property</span><span class="sxs-lookup"><span data-stu-id="aa9c4-102">property</span></span>
<span data-ttu-id="aa9c4-103">*Właściwości* są podstawowymi blokami konstrukcyjnymi [typów jednostek](entity-type.md) i [typów złożonych](complex-type.md).</span><span class="sxs-lookup"><span data-stu-id="aa9c4-103">*Properties* are the fundamental building blocks of [entity types](entity-type.md) and [complex types](complex-type.md).</span></span> <span data-ttu-id="aa9c4-104">Właściwości definiują kształt i charakterystykę danych, które będzie zawierać wystąpienie typu jednostki lub wystąpienie typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-104">Properties define the shape and characteristics of data that an entity type instance or complex type instance will contain.</span></span> <span data-ttu-id="aa9c4-105">Właściwości w modelu koncepcyjnym są analogiczne do właściwości zdefiniowanych w klasie.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-105">Properties in a conceptual model are analogous to properties defined on a class.</span></span> <span data-ttu-id="aa9c4-106">W taki sam sposób, w jaki właściwości klasy definiują kształt klasy i zawierają informacje o obiektach, właściwości w modelu koncepcyjnym definiują kształt typu jednostki i zawierają informacje o wystąpieniach typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-106">In the same way that properties on a class define the shape of the class and carry information about objects, properties in a conceptual model define the shape of an entity type and carry information about entity type instances.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa9c4-107">Właściwości, zgodnie z opisem w tym temacie, różnią się od właściwości nawigacji.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-107">Properties, as described in this topic, are different from navigation properties.</span></span> <span data-ttu-id="aa9c4-108">Aby uzyskać więcej informacji, zobacz [właściwości nawigacji](navigation-property.md).</span><span class="sxs-lookup"><span data-stu-id="aa9c4-108">For more information, see [navigation properties](navigation-property.md).</span></span>  
  
 <span data-ttu-id="aa9c4-109">Definicja właściwości zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="aa9c4-109">A property definition contains the following information:</span></span>  
  
- <span data-ttu-id="aa9c4-110">Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-110">A property name.</span></span> <span data-ttu-id="aa9c4-111">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="aa9c4-111">(Required)</span></span>  
  
- <span data-ttu-id="aa9c4-112">Typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-112">A property type.</span></span> <span data-ttu-id="aa9c4-113">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="aa9c4-113">(Required)</span></span>  
  
- <span data-ttu-id="aa9c4-114">Zestaw [aspektów](facet.md).</span><span class="sxs-lookup"><span data-stu-id="aa9c4-114">A set of [facets](facet.md).</span></span> <span data-ttu-id="aa9c4-115">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="aa9c4-115">(Optional)</span></span>  
  
 <span data-ttu-id="aa9c4-116">Właściwość może zawierać dane pierwotne (takie jak ciąg, liczba całkowita lub wartość logiczna) lub dane strukturalne (takie jak typ złożony).</span><span class="sxs-lookup"><span data-stu-id="aa9c4-116">A property can contain primitive data (such as a string, an integer, or a Boolean value), or structured data (such as a complex type).</span></span> <span data-ttu-id="aa9c4-117">Właściwości typu pierwotnego są również nazywane właściwościami skalarnymi.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-117">Properties that are of primitive type are also called scalar properties.</span></span> <span data-ttu-id="aa9c4-118">Aby uzyskać więcej informacji, zobacz [Entity Data Model: typy danych pierwotnych](entity-data-model-primitive-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="aa9c4-118">For more information, see [Entity Data Model: Primitive Data Types](entity-data-model-primitive-data-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa9c4-119">Typ złożony może sam, mieć właściwości, które są typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-119">A complex type can, itself, have properties that are complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa9c4-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa9c4-120">Example</span></span>  
 <span data-ttu-id="aa9c4-121">Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-121">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="aa9c4-122">Każdy typ jednostki ma kilka właściwości, chociaż informacje o typie dla każdej właściwości nie są przekazywane na diagramie.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-122">Each entity type has several properties, although type information for each property is not conveyed in the diagram.</span></span> <span data-ttu-id="aa9c4-123">Właściwości, które są [kluczami jednostek](entity-key.md) , są oznaczane symbolem (Key).</span><span class="sxs-lookup"><span data-stu-id="aa9c4-123">Properties that are [entity keys](entity-key.md) are denoted with (Key).</span></span>  
  
 ![Przykładowy model z trzema typami jednostek](./media/property/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="aa9c4-125">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-125">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="aa9c4-126">Poniższy plik CSDL definiuje typ jednostki `Book` (jak pokazano na powyższym diagramie) i wskazuje typ i nazwę każdej właściwości przy użyciu atrybutów XML.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-126">The following CSDL defines the `Book` entity type (as shown in the diagram above) and indicates the type and name of each property by using XML attributes.</span></span> <span data-ttu-id="aa9c4-127">Opcjonalny zestaw reguł, `Nullable`, jest również definiowany przy użyciu atrybutu XML.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-127">An optional facet, `Nullable`, is also defined by using an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="aa9c4-128">Istnieje możliwość, że jedna z właściwości pokazywanych na diagramie jest właściwością typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-128">It is possible that one of the properties shown in the diagram is a complex type property.</span></span> <span data-ttu-id="aa9c4-129">Na przykład właściwość `Address` w typie jednostki `Publisher` może być właściwością typu złożonego składającą się z kilku właściwości skalarnych, takich jak `StreetAddress`, `City`, `StateOrProvince`, `Country`i `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="aa9c4-129">For example, the `Address` property on the `Publisher` entity type could be a complex type property composed of several scalar properties, such as `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span> <span data-ttu-id="aa9c4-130">Reprezentacja CSDL tego typu złożonego będzie następująca:</span><span class="sxs-lookup"><span data-stu-id="aa9c4-130">The CSDL representation of such a complex type would be as follows:</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="aa9c4-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa9c4-131">See also</span></span>

- [<span data-ttu-id="aa9c4-132">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="aa9c4-132">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="aa9c4-133">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="aa9c4-133">Entity Data Model</span></span>](entity-data-model.md)
