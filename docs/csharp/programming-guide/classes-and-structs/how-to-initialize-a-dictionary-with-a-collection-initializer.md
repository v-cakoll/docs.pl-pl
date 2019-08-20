---
title: Inicjowanie słownika z inicjatorem kolekcji — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 22f80365b974df66999ac68f7bc2a9ffa7d445a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596814"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="87a93-102">Inicjowanie słownika przy użyciu inicjatora kolekcji (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="87a93-102">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="87a93-103">A <xref:System.Collections.Generic.Dictionary%602> zawiera kolekcję par klucz/wartość.</span><span class="sxs-lookup"><span data-stu-id="87a93-103">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="87a93-104">Jego <xref:System.Collections.Generic.Dictionary%602.Add*> Metoda przyjmuje dwa parametry — jeden dla klucza i jeden dla tej wartości.</span><span class="sxs-lookup"><span data-stu-id="87a93-104">Its <xref:System.Collections.Generic.Dictionary%602.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="87a93-105">Jednym ze sposobów na zainicjowanie <xref:System.Collections.Generic.Dictionary%602>lub dowolna kolekcja, której `Add` Metoda przyjmuje wiele parametrów, jest ujęcie każdego zestawu parametrów w nawiasach klamrowych, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="87a93-105">One way to initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, is to enclose each set of parameters in braces as shown in the following example.</span></span> <span data-ttu-id="87a93-106">Innym rozwiązaniem jest użycie inicjatora indeksu, również w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="87a93-106">Another option is to use an index initializer, also shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="87a93-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="87a93-107">Example</span></span>

<span data-ttu-id="87a93-108">W poniższym przykładzie kodu element <xref:System.Collections.Generic.Dictionary%602> jest inicjowany z wystąpieniami typu. `StudentName`</span><span class="sxs-lookup"><span data-stu-id="87a93-108">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  <span data-ttu-id="87a93-109">Pierwsze inicjowanie używa `Add` metody z dwoma argumentami.</span><span class="sxs-lookup"><span data-stu-id="87a93-109">The first initialization uses the `Add` method with two arguments.</span></span> <span data-ttu-id="87a93-110">Kompilator generuje wywołanie `Add` dla każdej `int` pary kluczy i `StudentName` wartości.</span><span class="sxs-lookup"><span data-stu-id="87a93-110">The compiler generates a call to `Add` for each of the pairs of `int` keys and `StudentName` values.</span></span> <span data-ttu-id="87a93-111">Druga używa metody `Dictionary` indeksu publicznego odczytu/zapisu klasy:</span><span class="sxs-lookup"><span data-stu-id="87a93-111">The second uses a public read / write indexer method of the `Dictionary` class:</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

<span data-ttu-id="87a93-112">Zwróć uwagę na dwie pary nawiasów klamrowych w każdym elemencie kolekcji w pierwszej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="87a93-112">Note the two pairs of braces in each element of the collection in the first declaration.</span></span> <span data-ttu-id="87a93-113">Wewnętrzne nawiasy klamrowe otaczające inicjatora obiektów dla `StudentName`, a skrajne nawiasy klamrowe obejmują inicjator dla pary klucz/wartość, które zostaną dodane `students` <xref:System.Collections.Generic.Dictionary%602>do.</span><span class="sxs-lookup"><span data-stu-id="87a93-113">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="87a93-114">Na koniec cały inicjator kolekcji dla słownika jest ujęty w nawiasy klamrowe.</span><span class="sxs-lookup"><span data-stu-id="87a93-114">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span> <span data-ttu-id="87a93-115">Podczas drugiego inicjowania po lewej stronie przypisania jest kluczem, a po prawej stronie jest wartością, przy użyciu inicjatora obiektu dla `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="87a93-115">In the second initialization, the left side of the assignment is the key and the right side is the value, using an object initializer for `StudentName`.</span></span>

## <a name="see-also"></a><span data-ttu-id="87a93-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87a93-116">See also</span></span>

- [<span data-ttu-id="87a93-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="87a93-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="87a93-118">Inicjatory obiektów i kolekcji</span><span class="sxs-lookup"><span data-stu-id="87a93-118">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
