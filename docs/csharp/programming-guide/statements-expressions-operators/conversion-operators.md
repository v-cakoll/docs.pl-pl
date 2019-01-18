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
ms.openlocfilehash: 927640b63773d24be93cc90427668f9568a39652
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362733"
---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="f1b0c-102">Operatory konwersji (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="f1b0c-102">Conversion operators (C# Programming Guide)</span></span>

<span data-ttu-id="f1b0c-103">C# umożliwia programistom deklarowania konwersje na klasy lub struktury, tak aby klasy lub struktury mogą być konwertowane do lub z innych klas lub struktur lub typy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="f1b0c-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="f1b0c-104">Konwersje są zdefiniowane like — operatory i są nazywane dla typu, do którego konwertują.</span><span class="sxs-lookup"><span data-stu-id="f1b0c-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="f1b0c-105">Typ argumentu, który ma zostać przekonwertowany lub typ wyniku konwersji, ale nie obu musi być typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="f1b0c-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="f1b0c-106">Omówienie operatorów konwersji</span><span class="sxs-lookup"><span data-stu-id="f1b0c-106">Conversion operators overview</span></span>

 <span data-ttu-id="f1b0c-107">Operatory konwersji mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="f1b0c-107">Conversion operators have the following properties:</span></span>  
  
-   <span data-ttu-id="f1b0c-108">Konwersje zadeklarowane jako `implicit` wykonywane automatycznie, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="f1b0c-108">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
-   <span data-ttu-id="f1b0c-109">Konwersje zadeklarowane jako `explicit` wymaga rzutowania do wywołania.</span><span class="sxs-lookup"><span data-stu-id="f1b0c-109">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
-   <span data-ttu-id="f1b0c-110">Wszystkie konwersje musi być zadeklarowany jako `static`.</span><span class="sxs-lookup"><span data-stu-id="f1b0c-110">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f1b0c-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="f1b0c-111">Related sections</span></span>

 <span data-ttu-id="f1b0c-112">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="f1b0c-112">For more information:</span></span>  
  
-   [<span data-ttu-id="f1b0c-113">Używanie operatorów konwersji</span><span class="sxs-lookup"><span data-stu-id="f1b0c-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [<span data-ttu-id="f1b0c-114">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="f1b0c-114">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [<span data-ttu-id="f1b0c-115">Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="f1b0c-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="f1b0c-116">explicit</span><span class="sxs-lookup"><span data-stu-id="f1b0c-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [<span data-ttu-id="f1b0c-117">implicit</span><span class="sxs-lookup"><span data-stu-id="f1b0c-117">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [<span data-ttu-id="f1b0c-118">static</span><span class="sxs-lookup"><span data-stu-id="f1b0c-118">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="f1b0c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1b0c-119">See also</span></span>

- <xref:System.Convert>  
- [<span data-ttu-id="f1b0c-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f1b0c-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f1b0c-121">Tworzenie łańcucha zdefiniowanych przez użytkownika Konwersje jawne w języku C#</span><span class="sxs-lookup"><span data-stu-id="f1b0c-121">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
