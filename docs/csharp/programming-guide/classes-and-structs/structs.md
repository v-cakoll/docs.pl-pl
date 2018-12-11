---
title: Struktury - C# przewodnik programowania
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 3f19d0485939e1923c479c1c9fdeb06572a11e14
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240388"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="70f9d-102">Struktury (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="70f9d-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="70f9d-103">Struktury są zdefiniowane przy użyciu [struktury](../../language-reference/keywords/struct.md) — słowo kluczowe, na przykład:</span><span class="sxs-lookup"><span data-stu-id="70f9d-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
<span data-ttu-id="70f9d-104">Struktury współużytkując większość tej samej składni jako klasy.</span><span class="sxs-lookup"><span data-stu-id="70f9d-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="70f9d-105">Nazwa struktury musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="70f9d-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="70f9d-106">Struktury są bardziej ograniczone niż klas w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="70f9d-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="70f9d-107">W deklaracji struktury pola nie można zainicjować, chyba że są deklarowane jako const lub statyczną.</span><span class="sxs-lookup"><span data-stu-id="70f9d-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="70f9d-108">Domyślny konstruktor (Konstruktor bez parametrów), lub finalizator, nie można zadeklarować struktury.</span><span class="sxs-lookup"><span data-stu-id="70f9d-108">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="70f9d-109">Struktury są kopiowane w przydziale.</span><span class="sxs-lookup"><span data-stu-id="70f9d-109">Structs are copied on assignment.</span></span> <span data-ttu-id="70f9d-110">Gdy struktura jest przypisywana nowej zmiennej, wszystkie dane są kopiowane, a wszelkie zmiany nowa kopia nie zmienia danych do oryginalnej kopii.</span><span class="sxs-lookup"><span data-stu-id="70f9d-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="70f9d-111">Ważne jest, aby pamiętać podczas pracy z kolekcjami wartość typy takie jak `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="70f9d-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="70f9d-112">Struktury są typami wartości, w przeciwieństwie do klasy, które są typami odwołań.</span><span class="sxs-lookup"><span data-stu-id="70f9d-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="70f9d-113">W przeciwieństwie do klasy, struktury mogą być utworzone bez użycia `new` operatora.</span><span class="sxs-lookup"><span data-stu-id="70f9d-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="70f9d-114">Struktury można zadeklarować konstruktorów, które mają parametry.</span><span class="sxs-lookup"><span data-stu-id="70f9d-114">Structs can declare constructors that have parameters.</span></span> 
- <span data-ttu-id="70f9d-115">Struktura nie może dziedziczyć z innej struktury lub klasy, a nie może być podstawą klasy.</span><span class="sxs-lookup"><span data-stu-id="70f9d-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="70f9d-116">Wszystkie struktury dziedziczyć bezpośrednio <xref:System.ValueType>, który dziedziczy z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="70f9d-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="70f9d-117">Struktura może zaimplementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="70f9d-117">A struct can implement interfaces.</span></span>  
- <span data-ttu-id="70f9d-118">Struktura może służyć jako typ dopuszczający wartość null i można przypisać wartości null.</span><span class="sxs-lookup"><span data-stu-id="70f9d-118">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="70f9d-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="70f9d-119">Related sections</span></span>  

<span data-ttu-id="70f9d-120">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="70f9d-120">For more information:</span></span>  
  
- [<span data-ttu-id="70f9d-121">Używanie struktur</span><span class="sxs-lookup"><span data-stu-id="70f9d-121">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="70f9d-122">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="70f9d-122">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="70f9d-123">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="70f9d-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="70f9d-124">Instrukcje: Różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody</span><span class="sxs-lookup"><span data-stu-id="70f9d-124">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [<span data-ttu-id="70f9d-125">Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="70f9d-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a><span data-ttu-id="70f9d-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70f9d-126">See also</span></span>

- [<span data-ttu-id="70f9d-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="70f9d-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="70f9d-128">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="70f9d-128">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="70f9d-129">Klasy</span><span class="sxs-lookup"><span data-stu-id="70f9d-129">Classes</span></span>](classes.md)
- [<span data-ttu-id="70f9d-130">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="70f9d-130">Identifier names</span></span>](../inside-a-program/identifier-names.md)
