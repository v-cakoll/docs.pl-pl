---
title: Jak zainicjować obiekty za pomocą inicjatora obiektów - Przewodnik programowania C#
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: a2ecc9df211d0082bd4b413653e374758c877abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705590"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="5cdc9-102">Jak zainicjować obiekty za pomocą inicjatora obiektów (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="5cdc9-102">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="5cdc9-103">Można użyć inicjatorów obiektów do inicjowania obiektów typu w sposób deklaratywny bez jawnego wywoływania konstruktora dla typu.</span><span class="sxs-lookup"><span data-stu-id="5cdc9-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="5cdc9-104">W poniższych przykładach przedstawiono sposób używania inicjatorów obiektów z nazwanymi obiektami.</span><span class="sxs-lookup"><span data-stu-id="5cdc9-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="5cdc9-105">Kompilator przetwarza inicjatory obiektów, najpierw uzyskując dostęp do domyślnego konstruktora wystąpienia, a następnie przetwarzając inicjowania elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="5cdc9-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="5cdc9-106">W związku z tym jeśli konstruktor bezparametrów jest zadeklarowany, jak `private` w klasie, inicjatory obiektów, które wymagają dostępu publicznego zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5cdc9-106">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="5cdc9-107">Należy użyć inicjatora obiektów, jeśli definiujesz typ anonimowy.</span><span class="sxs-lookup"><span data-stu-id="5cdc9-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="5cdc9-108">Aby uzyskać więcej informacji, zobacz [Jak zwrócić podzestawy właściwości elementu w kwerendzie](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="5cdc9-108">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cdc9-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cdc9-109">Example</span></span>  

<span data-ttu-id="5cdc9-110">W poniższym przykładzie pokazano, `StudentName` jak zainicjować nowy typ przy użyciu inicjatorów obiektów.</span><span class="sxs-lookup"><span data-stu-id="5cdc9-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="5cdc9-111">W tym przykładzie ustawia `StudentName` właściwości w typie:</span><span class="sxs-lookup"><span data-stu-id="5cdc9-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="5cdc9-112">Inicjatory obiektów mogą służyć do ustawiania indeksatorów w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="5cdc9-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="5cdc9-113">W poniższym `BaseballTeam` przykładzie definiuje klasę, która używa indeksatora, aby uzyskać i ustawić graczy na różnych pozycjach.</span><span class="sxs-lookup"><span data-stu-id="5cdc9-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="5cdc9-114">Iinitor może przypisać graczy, na podstawie skrótu pozycji, lub liczby używanej dla każdej pozycji baseball karty wyników:</span><span class="sxs-lookup"><span data-stu-id="5cdc9-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="5cdc9-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5cdc9-115">See also</span></span>

- [<span data-ttu-id="5cdc9-116">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="5cdc9-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5cdc9-117">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="5cdc9-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
