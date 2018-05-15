---
title: Struktury (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: ffb5b8da6c72056620cf890f38af4e7a8116ab3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="0c040-102">Struktury (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="0c040-102">Structs (C# Programming Guide)</span></span>
<span data-ttu-id="0c040-103">Struktury są zdefiniowane przy użyciu [struktury](../../../csharp/language-reference/keywords/struct.md) — słowo kluczowe, na przykład:</span><span class="sxs-lookup"><span data-stu-id="0c040-103">Structs are defined by using the [struct](../../../csharp/language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 <span data-ttu-id="0c040-104">Struktury udziału większość takiej samej składni jak klasy, struktury są bardziej ograniczone niż klasy:</span><span class="sxs-lookup"><span data-stu-id="0c040-104">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="0c040-105">W deklaracji struktury pól nie można zainicjować, chyba że zostały zgłoszone jako const lub statycznej.</span><span class="sxs-lookup"><span data-stu-id="0c040-105">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
  
-   <span data-ttu-id="0c040-106">Struktury nie można zadeklarować konstruktora domyślnego (Konstruktor bez parametrów) lub finalizatora.</span><span class="sxs-lookup"><span data-stu-id="0c040-106">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="0c040-107">Struktury są kopiowane na przypisanie.</span><span class="sxs-lookup"><span data-stu-id="0c040-107">Structs are copied on assignment.</span></span> <span data-ttu-id="0c040-108">Gdy struktury jest przypisany do nowej zmiennej, wszystkie dane zostaną skopiowane, a wszelkie zmiany nowej kopii nie zmienia dane oryginał.</span><span class="sxs-lookup"><span data-stu-id="0c040-108">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="0c040-109">Jest to ważne podczas pracy z kolekcjami typów wartości, takich jak słownik\<ciąg, myStruct >.</span><span class="sxs-lookup"><span data-stu-id="0c040-109">This is important to remember when working with collections of value types such as Dictionary\<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="0c040-110">Struktury są typy wartości i typy referencyjne występują następujące klasy.</span><span class="sxs-lookup"><span data-stu-id="0c040-110">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="0c040-111">W przeciwieństwie do klasy, struktury można wdrożyć bez użycia `new` operatora.</span><span class="sxs-lookup"><span data-stu-id="0c040-111">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="0c040-112">Struktury mogą zadeklarować konstruktorów, które mają parametry.</span><span class="sxs-lookup"><span data-stu-id="0c040-112">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="0c040-113">Struktury nie może dziedziczyć z innego struktury lub klasy, a nie może być podstawą klasy.</span><span class="sxs-lookup"><span data-stu-id="0c040-113">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="0c040-114">Strukturami dziedziczyć bezpośrednio po `System.ValueType`, który dziedziczy z `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="0c040-114">All structs inherit directly from `System.ValueType`, which inherits from `System.Object`.</span></span>  
  
-   <span data-ttu-id="0c040-115">Struktury mogą implementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="0c040-115">A struct can implement interfaces.</span></span>  
  
-   <span data-ttu-id="0c040-116">Struktury mogą być używane jako typ dopuszczający wartość null i można przypisać wartości null.</span><span class="sxs-lookup"><span data-stu-id="0c040-116">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0c040-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0c040-117">Related Sections</span></span>  
 <span data-ttu-id="0c040-118">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="0c040-118">For more information:</span></span>  
  
-   [<span data-ttu-id="0c040-119">Używanie struktur</span><span class="sxs-lookup"><span data-stu-id="0c040-119">Using Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [<span data-ttu-id="0c040-120">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="0c040-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="0c040-121">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="0c040-121">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [<span data-ttu-id="0c040-122">Instrukcje: różnica między przekazywaniem struktury a przekazywaniem odwołań do klas do metody</span><span class="sxs-lookup"><span data-stu-id="0c040-122">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [<span data-ttu-id="0c040-123">Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="0c040-123">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a><span data-ttu-id="0c040-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c040-124">See Also</span></span>  
 [<span data-ttu-id="0c040-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0c040-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0c040-126">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="0c040-126">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="0c040-127">Klasy</span><span class="sxs-lookup"><span data-stu-id="0c040-127">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
