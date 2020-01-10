---
title: Inicjowanie obiektów za pomocą inicjatora obiektów — C# Przewodnik programowania
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: a2ecc9df211d0082bd4b413653e374758c877abc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705590"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="85b33-102">Inicjowanie obiektów za pomocą inicjatora obiektów (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="85b33-102">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="85b33-103">Inicjatorów obiektów można użyć do zainicjowania obiektów typu w sposób deklaratywny bez jawnego wywołania konstruktora dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="85b33-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="85b33-104">W poniższych przykładach pokazano, jak używać inicjatorów obiektów z nazwanymi obiektami.</span><span class="sxs-lookup"><span data-stu-id="85b33-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="85b33-105">Kompilator przetwarza Inicjatory obiektów, najpierw uzyskując dostęp do domyślnego konstruktora wystąpień, a następnie przetwarza inicjalizacje elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="85b33-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="85b33-106">W związku z tym, jeśli Konstruktor bez parametrów jest zadeklarowany jako `private` w klasie, Inicjatory obiektów, które wymagają dostępu publicznego, zakończą się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="85b33-106">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="85b33-107">Jeśli jest definiowany typ anonimowy, należy użyć inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="85b33-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="85b33-108">Aby uzyskać więcej informacji, zobacz [jak zwrócić podzbiory właściwości elementu w zapytaniu](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="85b33-108">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="85b33-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="85b33-109">Example</span></span>  

<span data-ttu-id="85b33-110">Poniższy przykład pokazuje, jak zainicjować nowy typ `StudentName` przy użyciu inicjatorów obiektów.</span><span class="sxs-lookup"><span data-stu-id="85b33-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="85b33-111">Ten przykład ustawia właściwości w `StudentName` typie:</span><span class="sxs-lookup"><span data-stu-id="85b33-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="85b33-112">Inicjatory obiektów mogą służyć do ustawiania indeksatorów w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="85b33-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="85b33-113">W poniższym przykładzie zdefiniowano klasę `BaseballTeam`, która używa indeksatora do pobierania i ustawiania graczy w różnych miejscach.</span><span class="sxs-lookup"><span data-stu-id="85b33-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="85b33-114">Inicjator może przypisywać graczy na podstawie skrótu do pozycji lub liczby użytej dla każdej pozycji siatkówki karty wyników:</span><span class="sxs-lookup"><span data-stu-id="85b33-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="85b33-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85b33-115">See also</span></span>

- [<span data-ttu-id="85b33-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="85b33-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="85b33-117">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="85b33-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
