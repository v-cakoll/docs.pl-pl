---
title: Struktury (Przewodnik programowania w języku C#)
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 27d4b0d7edf1b5e89e84ac1df5783d68ebb4efe0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186932"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="3a81f-102">Struktury (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3a81f-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="3a81f-103">Struktury są zdefiniowane przy użyciu [struktury](../../language-reference/keywords/struct.md) — słowo kluczowe, na przykład:</span><span class="sxs-lookup"><span data-stu-id="3a81f-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
<span data-ttu-id="3a81f-104">Struktury współużytkując większość tej samej składni jako klasy.</span><span class="sxs-lookup"><span data-stu-id="3a81f-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="3a81f-105">Nazwa struktury musi być prawidłową C# [nazwa identyfikatora](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="3a81f-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="3a81f-106">Struktury są bardziej ograniczone niż klas w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3a81f-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="3a81f-107">W deklaracji struktury pola nie można zainicjować, chyba że są deklarowane jako const lub statyczną.</span><span class="sxs-lookup"><span data-stu-id="3a81f-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="3a81f-108">Domyślny konstruktor (Konstruktor bez parametrów), lub finalizator, nie można zadeklarować struktury.</span><span class="sxs-lookup"><span data-stu-id="3a81f-108">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="3a81f-109">Struktury są kopiowane w przydziale.</span><span class="sxs-lookup"><span data-stu-id="3a81f-109">Structs are copied on assignment.</span></span> <span data-ttu-id="3a81f-110">Gdy struktura jest przypisywana nowej zmiennej, wszystkie dane są kopiowane, a wszelkie zmiany nowa kopia nie zmienia danych do oryginalnej kopii.</span><span class="sxs-lookup"><span data-stu-id="3a81f-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="3a81f-111">Ważne jest, aby pamiętać podczas pracy z kolekcjami wartość typy takie jak `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="3a81f-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="3a81f-112">Struktury są typami wartości, w przeciwieństwie do klasy, które są typami odwołań.</span><span class="sxs-lookup"><span data-stu-id="3a81f-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="3a81f-113">W przeciwieństwie do klasy, struktury mogą być utworzone bez użycia `new` operatora.</span><span class="sxs-lookup"><span data-stu-id="3a81f-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="3a81f-114">Struktury można zadeklarować konstruktorów, które mają parametry.</span><span class="sxs-lookup"><span data-stu-id="3a81f-114">Structs can declare constructors that have parameters.</span></span> 
- <span data-ttu-id="3a81f-115">Struktura nie może dziedziczyć z innej struktury lub klasy, a nie może być podstawą klasy.</span><span class="sxs-lookup"><span data-stu-id="3a81f-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="3a81f-116">Wszystkie struktury dziedziczyć bezpośrednio <xref:System.ValueType>, który dziedziczy z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="3a81f-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="3a81f-117">Struktura może zaimplementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="3a81f-117">A struct can implement interfaces.</span></span>  
- <span data-ttu-id="3a81f-118">Struktura może służyć jako typ dopuszczający wartość null i można przypisać wartości null.</span><span class="sxs-lookup"><span data-stu-id="3a81f-118">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3a81f-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="3a81f-119">Related sections</span></span>  

<span data-ttu-id="3a81f-120">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="3a81f-120">For more information:</span></span>  
  
- [<span data-ttu-id="3a81f-121">Używanie struktur</span><span class="sxs-lookup"><span data-stu-id="3a81f-121">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="3a81f-122">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="3a81f-122">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="3a81f-123">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="3a81f-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="3a81f-124">Instrukcje: różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody</span><span class="sxs-lookup"><span data-stu-id="3a81f-124">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [<span data-ttu-id="3a81f-125">Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="3a81f-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a><span data-ttu-id="3a81f-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a81f-126">See also</span></span>

- [<span data-ttu-id="3a81f-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3a81f-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3a81f-128">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="3a81f-128">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="3a81f-129">Klasy</span><span class="sxs-lookup"><span data-stu-id="3a81f-129">Classes</span></span>](classes.md)
- [<span data-ttu-id="3a81f-130">Nazwy identyfikatorów</span><span class="sxs-lookup"><span data-stu-id="3a81f-130">Identifier names</span></span>](../inside-a-program/identifier-names.md)
