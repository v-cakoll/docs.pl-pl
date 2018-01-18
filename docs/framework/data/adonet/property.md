---
title: property
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 50cd2f2678d304af8b898380645424e0635891d2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="property"></a><span data-ttu-id="717eb-102">property</span><span class="sxs-lookup"><span data-stu-id="717eb-102">property</span></span>
<span data-ttu-id="717eb-103">*Właściwości* są podstawowymi blokami konstrukcyjnymi elementu [typów jednostek](../../../../docs/framework/data/adonet/entity-type.md) i [typów złożonych](../../../../docs/framework/data/adonet/complex-type.md).</span><span class="sxs-lookup"><span data-stu-id="717eb-103">*Properties* are the fundamental building blocks of [entity types](../../../../docs/framework/data/adonet/entity-type.md) and [complex types](../../../../docs/framework/data/adonet/complex-type.md).</span></span> <span data-ttu-id="717eb-104">Właściwości definiują kształt i właściwości danych, który będzie zawierać wystąpienia typu jednostki lub typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="717eb-104">Properties define the shape and characteristics of data that an entity type instance or complex type instance will contain.</span></span> <span data-ttu-id="717eb-105">Właściwości w modelu koncepcyjnym są analogiczne do właściwości zdefiniowane w klasie.</span><span class="sxs-lookup"><span data-stu-id="717eb-105">Properties in a conceptual model are analogous to properties defined on a class.</span></span> <span data-ttu-id="717eb-106">W ten sam sposób, że właściwości dla klasy, zdefiniuj kształtu klasy i zawiera informacje o obiektach właściwości w modelu koncepcyjnym zdefiniuj kształtu typu jednostki i zawiera informacje na temat wystąpień typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="717eb-106">In the same way that properties on a class define the shape of the class and carry information about objects, properties in a conceptual model define the shape of an entity type and carry information about entity type instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="717eb-107">Właściwości, zgodnie z opisem w tym temacie różnią się od właściwości nawigacji.</span><span class="sxs-lookup"><span data-stu-id="717eb-107">Properties, as described in this topic, are different from navigation properties.</span></span> <span data-ttu-id="717eb-108">Aby uzyskać więcej informacji, zobacz [właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md).</span><span class="sxs-lookup"><span data-stu-id="717eb-108">For more information, see [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md).</span></span>  
  
 <span data-ttu-id="717eb-109">Definicja właściwości zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="717eb-109">A property definition contains the following information:</span></span>  
  
-   <span data-ttu-id="717eb-110">Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="717eb-110">A property name.</span></span> <span data-ttu-id="717eb-111">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="717eb-111">(Required)</span></span>  
  
-   <span data-ttu-id="717eb-112">Typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="717eb-112">A property type.</span></span> <span data-ttu-id="717eb-113">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="717eb-113">(Required)</span></span>  
  
-   <span data-ttu-id="717eb-114">Zestaw [aspekty](../../../../docs/framework/data/adonet/facet.md).</span><span class="sxs-lookup"><span data-stu-id="717eb-114">A set of [facets](../../../../docs/framework/data/adonet/facet.md).</span></span> <span data-ttu-id="717eb-115">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="717eb-115">(Optional)</span></span>  
  
 <span data-ttu-id="717eb-116">Właściwość może zawierać danych pierwotnych (na przykład ciągiem, liczbą całkowitą lub wartość logiczną) lub dane strukturalne (takie jak typ złożony).</span><span class="sxs-lookup"><span data-stu-id="717eb-116">A property can contain primitive data (such as a string, an integer, or a Boolean value), or structured data (such as a complex type).</span></span> <span data-ttu-id="717eb-117">Właściwości typu pierwotnego są również nazywane właściwości skalarne.</span><span class="sxs-lookup"><span data-stu-id="717eb-117">Properties that are of primitive type are also called scalar properties.</span></span> <span data-ttu-id="717eb-118">Aby uzyskać więcej informacji, zobacz [modelu Entity Data Model: typy pierwotne danych](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="717eb-118">For more information, see [Entity Data Model: Primitive Data Types](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="717eb-119">Typ złożony mają właściwości, które są typami złożonymi.</span><span class="sxs-lookup"><span data-stu-id="717eb-119">A complex type can, itself, have properties that are complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="717eb-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="717eb-120">Example</span></span>  
 <span data-ttu-id="717eb-121">Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.</span><span class="sxs-lookup"><span data-stu-id="717eb-121">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="717eb-122">Poszczególnych typów jednostek ma kilka właściwości, chociaż nie przekazywanych informacji o typie dla każdej właściwości w schemacie.</span><span class="sxs-lookup"><span data-stu-id="717eb-122">Each entity type has several properties, although type information for each property is not conveyed in the diagram.</span></span> <span data-ttu-id="717eb-123">Właściwości, które są [kluczy jednostek](../../../../docs/framework/data/adonet/entity-key.md) są oznaczone symbolem (Key).</span><span class="sxs-lookup"><span data-stu-id="717eb-123">Properties that are [entity keys](../../../../docs/framework/data/adonet/entity-key.md) are denoted with (Key).</span></span>  
  
 <span data-ttu-id="717eb-124">![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="717eb-124">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="717eb-125">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="717eb-125">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="717eb-126">Definiuje następujące CSDL `Book` jednostki typu (jak pokazano na powyższym diagramie) oraz wskazuje typ i nazwa każdej właściwości przy użyciu atrybutów XML.</span><span class="sxs-lookup"><span data-stu-id="717eb-126">The following CSDL defines the `Book` entity type (as shown in the diagram above) and indicates the type and name of each property by using XML attributes.</span></span> <span data-ttu-id="717eb-127">Opcjonalne aspektu `Nullable`, jest także zdefiniowana przy użyciu atrybutu XML.</span><span class="sxs-lookup"><span data-stu-id="717eb-127">An optional facet, `Nullable`, is also defined by using an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="717eb-128">Istnieje możliwość, że jedna z właściwości wyświetlane na diagramie jest właściwość typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="717eb-128">It is possible that one of the properties shown in the diagram is a complex type property.</span></span> <span data-ttu-id="717eb-129">Na przykład `Address` właściwość `Publisher` typu jednostki można właściwość typu złożonego złożony z kilku właściwości skalarne, takie jak `StreetAddress`, `City`, `StateOrProvince`, `Country`, i `PostalCode`.</span><span class="sxs-lookup"><span data-stu-id="717eb-129">For example, the `Address` property on the `Publisher` entity type could be a complex type property composed of several scalar properties, such as `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span> <span data-ttu-id="717eb-130">Reprezentacja CSDL typu złożonego, należy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="717eb-130">The CSDL representation of such a complex type would be as follows:</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="717eb-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="717eb-131">See Also</span></span>  
 [<span data-ttu-id="717eb-132">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="717eb-132">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="717eb-133">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="717eb-133">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
