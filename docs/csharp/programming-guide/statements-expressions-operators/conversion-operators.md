---
title: Operatory konwersji - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: a55a2148ce161deca79d8ba8e64a217e474f0284
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236820"
---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="ab9c5-102">Operatory konwersji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ab9c5-102">Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="ab9c5-103">C# umożliwia programistom deklarowania konwersje na klasy lub struktury, tak aby klasy lub struktury mogą być konwertowane do lub z innych klas lub struktur lub typy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="ab9c5-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="ab9c5-104">Konwersje są zdefiniowane like — operatory i są nazywane dla typu, do którego konwertują.</span><span class="sxs-lookup"><span data-stu-id="ab9c5-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="ab9c5-105">Typ argumentu, który ma zostać przekonwertowany lub typ wyniku konwersji, ale nie obu musi być typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="ab9c5-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="ab9c5-106">Omówienie operatorów konwersji</span><span class="sxs-lookup"><span data-stu-id="ab9c5-106">Conversion Operators Overview</span></span>  
 <span data-ttu-id="ab9c5-107">Operatory konwersji mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ab9c5-107">Conversion operators have the following properties:</span></span>  
  
-   <span data-ttu-id="ab9c5-108">Konwersje zadeklarowane jako `implicit` wykonywane automatycznie, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="ab9c5-108">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
-   <span data-ttu-id="ab9c5-109">Konwersje zadeklarowane jako `explicit` wymaga rzutowania do wywołania.</span><span class="sxs-lookup"><span data-stu-id="ab9c5-109">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
-   <span data-ttu-id="ab9c5-110">Wszystkie konwersje musi być zadeklarowany jako `static`.</span><span class="sxs-lookup"><span data-stu-id="ab9c5-110">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ab9c5-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ab9c5-111">Related Sections</span></span>  
 <span data-ttu-id="ab9c5-112">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="ab9c5-112">For more information:</span></span>  
  
-   [<span data-ttu-id="ab9c5-113">Używanie operatorów konwersji</span><span class="sxs-lookup"><span data-stu-id="ab9c5-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [<span data-ttu-id="ab9c5-114">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="ab9c5-114">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [<span data-ttu-id="ab9c5-115">Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="ab9c5-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="ab9c5-116">explicit</span><span class="sxs-lookup"><span data-stu-id="ab9c5-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [<span data-ttu-id="ab9c5-117">implicit</span><span class="sxs-lookup"><span data-stu-id="ab9c5-117">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [<span data-ttu-id="ab9c5-118">static</span><span class="sxs-lookup"><span data-stu-id="ab9c5-118">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="ab9c5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab9c5-119">See Also</span></span>

- <xref:System.Convert>  
- [<span data-ttu-id="ab9c5-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ab9c5-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ab9c5-121">Tworzenie łańcucha zdefiniowanych przez użytkownika Konwersje jawne w języku C#</span><span class="sxs-lookup"><span data-stu-id="ab9c5-121">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
