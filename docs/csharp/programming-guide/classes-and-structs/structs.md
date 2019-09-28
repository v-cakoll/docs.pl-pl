---
title: Struktury — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: df2a235651a2242ffe18df377dce9995af31e99f
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392454"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="31fa0-102">Struktury (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="31fa0-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="31fa0-103">Struktury są zdefiniowane za pomocą słowa kluczowego [struct](../../language-reference/keywords/struct.md) , na przykład:</span><span class="sxs-lookup"><span data-stu-id="31fa0-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
<span data-ttu-id="31fa0-104">Struktury współużytkują większość tej samej składni co klasy.</span><span class="sxs-lookup"><span data-stu-id="31fa0-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="31fa0-105">Nazwa struktury musi być prawidłową C# [nazwą identyfikatora](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="31fa0-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="31fa0-106">Struktury są bardziej ograniczone niż klasy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="31fa0-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="31fa0-107">W deklaracji struktury nie można inicjować pól, chyba że są one zadeklarowane jako const lub static.</span><span class="sxs-lookup"><span data-stu-id="31fa0-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="31fa0-108">Struktura nie może deklarować bezparametrowego konstruktora (Konstruktor bez parametrów) lub finalizatora.</span><span class="sxs-lookup"><span data-stu-id="31fa0-108">A struct cannot declare a parameterless constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="31fa0-109">Struktury są kopiowane podczas przypisywania.</span><span class="sxs-lookup"><span data-stu-id="31fa0-109">Structs are copied on assignment.</span></span> <span data-ttu-id="31fa0-110">Gdy struktura jest przypisana do nowej zmiennej, wszystkie dane są kopiowane i wszelkie modyfikacje nowej kopii nie zmieniają danych dla oryginalnej kopii.</span><span class="sxs-lookup"><span data-stu-id="31fa0-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="31fa0-111">Jest to ważne, aby pamiętać, że podczas pracy z kolekcjami typów wartości, takimi jak `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="31fa0-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="31fa0-112">Struktury są typami wartości, w przeciwieństwie do klas, które są typami referencyjnymi.</span><span class="sxs-lookup"><span data-stu-id="31fa0-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="31fa0-113">W przeciwieństwie do klas, struktury mogą być tworzone bez użycia operatora `new`.</span><span class="sxs-lookup"><span data-stu-id="31fa0-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="31fa0-114">Struktury mogą deklarować konstruktory z parametrami.</span><span class="sxs-lookup"><span data-stu-id="31fa0-114">Structs can declare constructors that have parameters.</span></span>
- <span data-ttu-id="31fa0-115">Struktura nie może dziedziczyć z innej struktury lub klasy i nie może być podstawą klasy.</span><span class="sxs-lookup"><span data-stu-id="31fa0-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="31fa0-116">Wszystkie struktury dziedziczą bezpośrednio z <xref:System.ValueType>, które dziedziczy po <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="31fa0-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="31fa0-117">Struktura może implementować interfejsy.</span><span class="sxs-lookup"><span data-stu-id="31fa0-117">A struct can implement interfaces.</span></span>
- <span data-ttu-id="31fa0-118">Struktura nie może być `null` i nie można przypisać zmiennej struktury `null`, chyba że zmienna jest zadeklarowana jako typ wartości null.</span><span class="sxs-lookup"><span data-stu-id="31fa0-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable value type.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="31fa0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31fa0-119">See also</span></span>

- [<span data-ttu-id="31fa0-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="31fa0-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="31fa0-121">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="31fa0-121">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="31fa0-122">Klasy</span><span class="sxs-lookup"><span data-stu-id="31fa0-122">Classes</span></span>](classes.md)
- [<span data-ttu-id="31fa0-123">Typy wartości null</span><span class="sxs-lookup"><span data-stu-id="31fa0-123">Nullable value types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="31fa0-124">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="31fa0-124">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="31fa0-125">Używanie struktur</span><span class="sxs-lookup"><span data-stu-id="31fa0-125">Using Structs</span></span>](using-structs.md)
- <span data-ttu-id="31fa0-126">[Instrukcje: Zapoznaj się z różnicą między przekazywaniem struktury i przekazywaniem odwołania do klasy do metody @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="31fa0-126">[How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)</span></span>
