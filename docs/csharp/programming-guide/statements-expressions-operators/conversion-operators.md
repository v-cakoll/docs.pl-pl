---
title: Operatory konwersji - C# Programming Guide
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: 071eb75d9bab2b91b9cdb8ecc33df249b01e7ac6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619769"
---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="e9268-102">Operatory konwersji (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="e9268-102">Conversion operators (C# Programming Guide)</span></span>

<span data-ttu-id="e9268-103">C# umożliwia programistom deklarowania konwersje na klasy lub struktury, tak aby klasy lub struktury mogą być konwertowane do lub z innych klas lub struktur lub typy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="e9268-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="e9268-104">Konwersje są zdefiniowane like — operatory i są nazywane dla typu, do którego konwertują.</span><span class="sxs-lookup"><span data-stu-id="e9268-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="e9268-105">Typ argumentu, który ma zostać przekonwertowany lub typ wyniku konwersji, ale nie obu musi być typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="e9268-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="e9268-106">Omówienie operatorów konwersji</span><span class="sxs-lookup"><span data-stu-id="e9268-106">Conversion operators overview</span></span>

 <span data-ttu-id="e9268-107">Operatory konwersji mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="e9268-107">Conversion operators have the following properties:</span></span>  
  
-   <span data-ttu-id="e9268-108">Konwersje zadeklarowane jako `implicit` wykonywane automatycznie, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="e9268-108">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
-   <span data-ttu-id="e9268-109">Konwersje zadeklarowane jako `explicit` wymaga rzutowania do wywołania.</span><span class="sxs-lookup"><span data-stu-id="e9268-109">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
-   <span data-ttu-id="e9268-110">Wszystkie konwersje musi być zadeklarowany jako `static`.</span><span class="sxs-lookup"><span data-stu-id="e9268-110">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e9268-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e9268-111">Related sections</span></span>

 <span data-ttu-id="e9268-112">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="e9268-112">For more information:</span></span>  
  
-   [<span data-ttu-id="e9268-113">Używanie operatorów konwersji</span><span class="sxs-lookup"><span data-stu-id="e9268-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [<span data-ttu-id="e9268-114">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="e9268-114">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [<span data-ttu-id="e9268-115">Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="e9268-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="e9268-116">explicit</span><span class="sxs-lookup"><span data-stu-id="e9268-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [<span data-ttu-id="e9268-117">implicit</span><span class="sxs-lookup"><span data-stu-id="e9268-117">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [<span data-ttu-id="e9268-118">static</span><span class="sxs-lookup"><span data-stu-id="e9268-118">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="e9268-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9268-119">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="e9268-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e9268-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e9268-121">Tworzenie łańcucha zdefiniowanych przez użytkownika Konwersje jawne w języku C#</span><span class="sxs-lookup"><span data-stu-id="e9268-121">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
