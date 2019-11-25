---
title: Struktury — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 35b39da0b15c41b7b2c7a6567bea5dca3fb430e7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970317"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="271ec-102">Struktury (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="271ec-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="271ec-103">Struktury są zdefiniowane za pomocą słowa kluczowego [struct](../../language-reference/keywords/struct.md) , na przykład:</span><span class="sxs-lookup"><span data-stu-id="271ec-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
<span data-ttu-id="271ec-104">Struktury współużytkują większość tej samej składni co klasy.</span><span class="sxs-lookup"><span data-stu-id="271ec-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="271ec-105">Nazwa struktury musi być prawidłową C# [nazwą identyfikatora](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="271ec-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="271ec-106">Struktury są bardziej ograniczone niż klasy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="271ec-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="271ec-107">W deklaracji struktury nie można inicjować pól, chyba że są one zadeklarowane jako const lub static.</span><span class="sxs-lookup"><span data-stu-id="271ec-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="271ec-108">Struktura nie może deklarować bezparametrowego konstruktora (Konstruktor bez parametrów) lub finalizatora.</span><span class="sxs-lookup"><span data-stu-id="271ec-108">A struct cannot declare a parameterless constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="271ec-109">Struktury są kopiowane podczas przypisywania.</span><span class="sxs-lookup"><span data-stu-id="271ec-109">Structs are copied on assignment.</span></span> <span data-ttu-id="271ec-110">Gdy struktura jest przypisana do nowej zmiennej, wszystkie dane są kopiowane i wszelkie modyfikacje nowej kopii nie zmieniają danych dla oryginalnej kopii.</span><span class="sxs-lookup"><span data-stu-id="271ec-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="271ec-111">Jest to ważne, aby pamiętać, że podczas pracy z kolekcjami typów wartości takich jak `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="271ec-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="271ec-112">Struktury są typami wartości, w przeciwieństwie do klas, które są typami referencyjnymi.</span><span class="sxs-lookup"><span data-stu-id="271ec-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="271ec-113">W przeciwieństwie do klas, struktury mogą być tworzone bez użycia operatora `new`.</span><span class="sxs-lookup"><span data-stu-id="271ec-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="271ec-114">Struktury mogą deklarować konstruktory z parametrami.</span><span class="sxs-lookup"><span data-stu-id="271ec-114">Structs can declare constructors that have parameters.</span></span>
- <span data-ttu-id="271ec-115">Struktura nie może dziedziczyć z innej struktury lub klasy i nie może być podstawą klasy.</span><span class="sxs-lookup"><span data-stu-id="271ec-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="271ec-116">Wszystkie struktury dziedziczą bezpośrednio z <xref:System.ValueType>, które dziedziczą z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="271ec-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="271ec-117">Struktura może implementować interfejsy.</span><span class="sxs-lookup"><span data-stu-id="271ec-117">A struct can implement interfaces.</span></span>
- <span data-ttu-id="271ec-118">Nie można `null`struktury i nie można przypisać zmiennej struktury `null`, chyba że zmienna jest zadeklarowana jako typ wartości null.</span><span class="sxs-lookup"><span data-stu-id="271ec-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable value type.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="271ec-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="271ec-119">See also</span></span>

- [<span data-ttu-id="271ec-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="271ec-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="271ec-121">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="271ec-121">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="271ec-122">Klasy</span><span class="sxs-lookup"><span data-stu-id="271ec-122">Classes</span></span>](classes.md)
- [<span data-ttu-id="271ec-123">Typy wartości null</span><span class="sxs-lookup"><span data-stu-id="271ec-123">Nullable value types</span></span>](../../language-reference/builtin-types/nullable-value-types.md)
- [<span data-ttu-id="271ec-124">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="271ec-124">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="271ec-125">Używanie struktur</span><span class="sxs-lookup"><span data-stu-id="271ec-125">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="271ec-126">Jak poznać różnicę między przekazaniem struktury i przekazaniem odwołania do klasy do metody</span><span class="sxs-lookup"><span data-stu-id="271ec-126">How to know the difference between passing a struct and passing a class reference to a method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
