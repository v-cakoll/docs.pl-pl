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
ms.openlocfilehash: 539a554da2ea2f785a54bd7e5ff81d09b908c9e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678611"
---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="d46f3-102">Operatory konwersji (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="d46f3-102">Conversion operators (C# Programming Guide)</span></span>

<span data-ttu-id="d46f3-103">C# umożliwia programistom deklarowania konwersje na klasy lub struktury, tak aby klasy lub struktury mogą być konwertowane do lub z innych klas lub struktur lub typy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="d46f3-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="d46f3-104">Konwersje są zdefiniowane like — operatory i są nazywane dla typu, do którego konwertują.</span><span class="sxs-lookup"><span data-stu-id="d46f3-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="d46f3-105">Typ argumentu, który ma zostać przekonwertowany lub typ wyniku konwersji, ale nie obu musi być typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="d46f3-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 [!code-csharp[csProgGuideStatements#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#10)]  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="d46f3-106">Omówienie operatorów konwersji</span><span class="sxs-lookup"><span data-stu-id="d46f3-106">Conversion operators overview</span></span>

 <span data-ttu-id="d46f3-107">Operatory konwersji mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="d46f3-107">Conversion operators have the following properties:</span></span>  
  
- <span data-ttu-id="d46f3-108">Konwersje zadeklarowane jako `implicit` wykonywane automatycznie, gdy jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="d46f3-108">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
- <span data-ttu-id="d46f3-109">Konwersje zadeklarowane jako `explicit` wymaga rzutowania do wywołania.</span><span class="sxs-lookup"><span data-stu-id="d46f3-109">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
- <span data-ttu-id="d46f3-110">Wszystkie konwersje musi być zadeklarowany jako `static`.</span><span class="sxs-lookup"><span data-stu-id="d46f3-110">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d46f3-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d46f3-111">Related sections</span></span>

 <span data-ttu-id="d46f3-112">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="d46f3-112">For more information:</span></span>  
  
- [<span data-ttu-id="d46f3-113">Używanie operatorów konwersji</span><span class="sxs-lookup"><span data-stu-id="d46f3-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
- [<span data-ttu-id="d46f3-114">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="d46f3-114">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
- [<span data-ttu-id="d46f3-115">Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="d46f3-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
- [<span data-ttu-id="d46f3-116">explicit</span><span class="sxs-lookup"><span data-stu-id="d46f3-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
- [<span data-ttu-id="d46f3-117">implicit</span><span class="sxs-lookup"><span data-stu-id="d46f3-117">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
- [<span data-ttu-id="d46f3-118">static</span><span class="sxs-lookup"><span data-stu-id="d46f3-118">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="d46f3-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d46f3-119">See also</span></span>

- <xref:System.Convert>
- [<span data-ttu-id="d46f3-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d46f3-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d46f3-121">Tworzenie łańcucha zdefiniowanych przez użytkownika Konwersje jawne w języku C#</span><span class="sxs-lookup"><span data-stu-id="d46f3-121">Chained user-defined explicit conversions in C#</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
