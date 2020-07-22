---
title: Inicjowanie obiektów za pomocą inicjatora obiektów — Przewodnik programowania w języku C#
description: Dowiedz się, w jaki sposób używać inicjatorów obiektów do inicjowania obiektów Type w języku C# bez wywoływania konstruktora. Użyj inicjatora obiektów do zdefiniowania typu anonimowego.
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 0781b168b0ae8b8383affe19d2721da67f662045
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865037"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="9d469-104">Inicjowanie obiektów za pomocą inicjatora obiektów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="9d469-104">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="9d469-105">Inicjatorów obiektów można użyć do zainicjowania obiektów typu w sposób deklaratywny bez jawnego wywołania konstruktora dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="9d469-105">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="9d469-106">W poniższych przykładach pokazano, jak używać inicjatorów obiektów z nazwanymi obiektami.</span><span class="sxs-lookup"><span data-stu-id="9d469-106">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="9d469-107">Kompilator przetwarza Inicjatory obiektów, najpierw uzyskując dostęp do domyślnego konstruktora wystąpień, a następnie przetwarza inicjalizacje elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9d469-107">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="9d469-108">W związku z tym, jeśli Konstruktor bez parametrów jest zadeklarowany jako `private` w klasie, Inicjatory obiektów, które wymagają dostępu publicznego, zakończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="9d469-108">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="9d469-109">Jeśli jest definiowany typ anonimowy, należy użyć inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="9d469-109">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="9d469-110">Aby uzyskać więcej informacji, zobacz [jak zwrócić podzbiory właściwości elementu w zapytaniu](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="9d469-110">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d469-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d469-111">Example</span></span>  

<span data-ttu-id="9d469-112">Poniższy przykład pokazuje, jak zainicjować nowy `StudentName` Typ za pomocą inicjatorów obiektów.</span><span class="sxs-lookup"><span data-stu-id="9d469-112">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="9d469-113">Ten przykład ustawia właściwości w `StudentName` typie:</span><span class="sxs-lookup"><span data-stu-id="9d469-113">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="9d469-114">Inicjatory obiektów mogą służyć do ustawiania indeksatorów w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="9d469-114">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="9d469-115">W poniższym przykładzie zdefiniowano `BaseballTeam` klasę, która używa indeksatora do pobierania i ustawiania graczy w różnych miejscach.</span><span class="sxs-lookup"><span data-stu-id="9d469-115">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="9d469-116">Inicjator może przypisywać graczy na podstawie skrótu do pozycji lub liczby użytej dla każdej pozycji siatkówki karty wyników:</span><span class="sxs-lookup"><span data-stu-id="9d469-116">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="9d469-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d469-117">See also</span></span>

- [<span data-ttu-id="9d469-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9d469-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9d469-119">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="9d469-119">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
