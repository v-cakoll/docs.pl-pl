---
title: Struktury (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: abe39b336aa8e9aa7a8a8ee96ed6848804644ddd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518706"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="619f8-102">Struktury (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="619f8-102">Structs (C# Programming Guide)</span></span>
<span data-ttu-id="619f8-103">Struktury są zdefiniowane przy użyciu [struktury](../../../csharp/language-reference/keywords/struct.md) — słowo kluczowe, na przykład:</span><span class="sxs-lookup"><span data-stu-id="619f8-103">Structs are defined by using the [struct](../../../csharp/language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 <span data-ttu-id="619f8-104">Struktury udostępniać większość tej samej składni jak klasy, chociaż struktur są bardziej ograniczone niż klasy:</span><span class="sxs-lookup"><span data-stu-id="619f8-104">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="619f8-105">W deklaracji struktury pola nie można zainicjować, chyba że są deklarowane jako const lub statyczną.</span><span class="sxs-lookup"><span data-stu-id="619f8-105">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
  
-   <span data-ttu-id="619f8-106">Domyślny konstruktor (Konstruktor bez parametrów), lub finalizator, nie można zadeklarować struktury.</span><span class="sxs-lookup"><span data-stu-id="619f8-106">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="619f8-107">Struktury są kopiowane w przydziale.</span><span class="sxs-lookup"><span data-stu-id="619f8-107">Structs are copied on assignment.</span></span> <span data-ttu-id="619f8-108">Gdy struktura jest przypisywana nowej zmiennej, wszystkie dane są kopiowane, a wszelkie zmiany nowa kopia nie zmienia danych do oryginalnej kopii.</span><span class="sxs-lookup"><span data-stu-id="619f8-108">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="619f8-109">Ważne jest, aby pamiętać podczas pracy z kolekcjami typów wartości, takich jak słownik\<ciąg, myStruct >.</span><span class="sxs-lookup"><span data-stu-id="619f8-109">This is important to remember when working with collections of value types such as Dictionary\<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="619f8-110">Struktury są typami wartości i klasy są typami odwołań.</span><span class="sxs-lookup"><span data-stu-id="619f8-110">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="619f8-111">W przeciwieństwie do klasy, struktury mogą być utworzone bez użycia `new` operatora.</span><span class="sxs-lookup"><span data-stu-id="619f8-111">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="619f8-112">Struktury można zadeklarować konstruktorów, które mają parametry.</span><span class="sxs-lookup"><span data-stu-id="619f8-112">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="619f8-113">Struktura nie może dziedziczyć z innej struktury lub klasy, a nie może być podstawą klasy.</span><span class="sxs-lookup"><span data-stu-id="619f8-113">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="619f8-114">Wszystkie struktury dziedziczyć bezpośrednio `System.ValueType`, który dziedziczy z `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="619f8-114">All structs inherit directly from `System.ValueType`, which inherits from `System.Object`.</span></span>  
  
-   <span data-ttu-id="619f8-115">Struktura może zaimplementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="619f8-115">A struct can implement interfaces.</span></span>  
  
-   <span data-ttu-id="619f8-116">Struktura może służyć jako typ dopuszczający wartość null i można przypisać wartości null.</span><span class="sxs-lookup"><span data-stu-id="619f8-116">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="619f8-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="619f8-117">Related Sections</span></span>  
 <span data-ttu-id="619f8-118">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="619f8-118">For more information:</span></span>  
  
-   [<span data-ttu-id="619f8-119">Używanie struktur</span><span class="sxs-lookup"><span data-stu-id="619f8-119">Using Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [<span data-ttu-id="619f8-120">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="619f8-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="619f8-121">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="619f8-121">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [<span data-ttu-id="619f8-122">Instrukcje: różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody</span><span class="sxs-lookup"><span data-stu-id="619f8-122">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [<span data-ttu-id="619f8-123">Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="619f8-123">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a><span data-ttu-id="619f8-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="619f8-124">See Also</span></span>

- [<span data-ttu-id="619f8-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="619f8-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="619f8-126">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="619f8-126">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="619f8-127">Klasy</span><span class="sxs-lookup"><span data-stu-id="619f8-127">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
