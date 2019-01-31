---
title: Struktury - C# przewodnik programowania
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 609169d4624802f679f9661b7aa0596403cc48e7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261623"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="58691-102">Struktury (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="58691-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="58691-103">Struktury są zdefiniowane przy użyciu [struktury](../../language-reference/keywords/struct.md) — słowo kluczowe, na przykład:</span><span class="sxs-lookup"><span data-stu-id="58691-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
<span data-ttu-id="58691-104">Struktury współużytkując większość tej samej składni jako klasy.</span><span class="sxs-lookup"><span data-stu-id="58691-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="58691-105">Nazwa struktury musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="58691-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="58691-106">Struktury są bardziej ograniczone niż klas w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="58691-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="58691-107">W deklaracji struktury pola nie można zainicjować, chyba że są deklarowane jako const lub statyczną.</span><span class="sxs-lookup"><span data-stu-id="58691-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="58691-108">Domyślny konstruktor (Konstruktor bez parametrów), lub finalizator, nie można zadeklarować struktury.</span><span class="sxs-lookup"><span data-stu-id="58691-108">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="58691-109">Struktury są kopiowane w przydziale.</span><span class="sxs-lookup"><span data-stu-id="58691-109">Structs are copied on assignment.</span></span> <span data-ttu-id="58691-110">Gdy struktura jest przypisywana nowej zmiennej, wszystkie dane są kopiowane, a wszelkie zmiany nowa kopia nie zmienia danych do oryginalnej kopii.</span><span class="sxs-lookup"><span data-stu-id="58691-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="58691-111">Ważne jest, aby pamiętać podczas pracy z kolekcjami wartość typy takie jak `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="58691-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="58691-112">Struktury są typami wartości, w przeciwieństwie do klasy, które są typami odwołań.</span><span class="sxs-lookup"><span data-stu-id="58691-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="58691-113">W przeciwieństwie do klasy, struktury mogą być utworzone bez użycia `new` operatora.</span><span class="sxs-lookup"><span data-stu-id="58691-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="58691-114">Struktury można zadeklarować konstruktorów, które mają parametry.</span><span class="sxs-lookup"><span data-stu-id="58691-114">Structs can declare constructors that have parameters.</span></span> 
- <span data-ttu-id="58691-115">Struktura nie może dziedziczyć z innej struktury lub klasy, a nie może być podstawą klasy.</span><span class="sxs-lookup"><span data-stu-id="58691-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="58691-116">Wszystkie struktury dziedziczyć bezpośrednio <xref:System.ValueType>, który dziedziczy z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="58691-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="58691-117">Struktura może zaimplementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="58691-117">A struct can implement interfaces.</span></span> 
- <span data-ttu-id="58691-118">Struktura nie może być `null`, i nie można przypisać zmiennej struktury `null` chyba, że zmienna jest zadeklarowana jako typ dopuszczający wartość null.</span><span class="sxs-lookup"><span data-stu-id="58691-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable type.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="58691-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="58691-119">Related sections</span></span>  

<span data-ttu-id="58691-120">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="58691-120">For more information:</span></span>  
  
- [<span data-ttu-id="58691-121">Używanie struktur</span><span class="sxs-lookup"><span data-stu-id="58691-121">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="58691-122">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="58691-122">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="58691-123">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="58691-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="58691-124">Instrukcje: Różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody</span><span class="sxs-lookup"><span data-stu-id="58691-124">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [<span data-ttu-id="58691-125">Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="58691-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a><span data-ttu-id="58691-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58691-126">See also</span></span>

- [<span data-ttu-id="58691-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="58691-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="58691-128">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="58691-128">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="58691-129">Klasy</span><span class="sxs-lookup"><span data-stu-id="58691-129">Classes</span></span>](classes.md)
- [<span data-ttu-id="58691-130">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="58691-130">Identifier names</span></span>](../inside-a-program/identifier-names.md)
