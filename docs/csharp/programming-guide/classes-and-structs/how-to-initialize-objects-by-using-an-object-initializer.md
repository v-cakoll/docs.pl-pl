---
title: 'Instrukcje: Inicjowanie obiektów za pomocą obiektu inicjatora - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 7b31e28c23a70e9f0794c82feb2a984c40ee9d0f
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267582"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="58b7c-102">Instrukcje: Inicjowanie obiektów za pomocą inicjatora obiektów (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="58b7c-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>

<span data-ttu-id="58b7c-103">Inicjatory obiektów można użyć do zainicjowania obiekty typu w sposób deklaratywne, bez jawnego wywołania konstruktora dla typu.</span><span class="sxs-lookup"><span data-stu-id="58b7c-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="58b7c-104">Poniższe przykłady pokazują, jak używać inicjatory obiektów z nazwane obiekty.</span><span class="sxs-lookup"><span data-stu-id="58b7c-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="58b7c-105">Procesy kompilatora obiekt inicjatory pierwszego uzyskiwania dostępu do domyślnego konstruktora wystąpienia, a następnie przetwarzania operacji inicjowania elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="58b7c-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="58b7c-106">W związku z tym jeśli konstruktora bez parametrów jest zadeklarowany jako `private` w klasie inicjatorów obiektów, które wymagają dostępu publicznego zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="58b7c-106">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="58b7c-107">Jeśli definiujesz typ anonimowy, należy użyć inicjatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="58b7c-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="58b7c-108">Aby uzyskać więcej informacji, zobacz [jak: Zwracanie podzbiorów właściwości elementu w zapytaniu](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="58b7c-108">For more information, see [How to: Return Subsets of Element Properties in a Query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58b7c-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="58b7c-109">Example</span></span>  

<span data-ttu-id="58b7c-110">Poniższy przykład pokazuje, jak zainicjować nowy `StudentName` typu przy użyciu inicjatorów obiektów.</span><span class="sxs-lookup"><span data-stu-id="58b7c-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="58b7c-111">W tym przykładzie ustawia właściwości w `StudentName` typu:</span><span class="sxs-lookup"><span data-stu-id="58b7c-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="58b7c-112">Inicjatory obiektów może służyć do ustawiania indeksatorów w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="58b7c-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="58b7c-113">W poniższym przykładzie zdefiniowano `BaseballTeam` klasę, która używa indeksator do pobierania i ustawiania graczy w różnych miejscach.</span><span class="sxs-lookup"><span data-stu-id="58b7c-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="58b7c-114">Inicjator można przypisać odtwarzaczy, w oparciu o skrót dla pozycji, lub numer używany dla każdej karty wyników mecz pozycji:</span><span class="sxs-lookup"><span data-stu-id="58b7c-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="58b7c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58b7c-115">See also</span></span>

- [<span data-ttu-id="58b7c-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="58b7c-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="58b7c-117">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="58b7c-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
