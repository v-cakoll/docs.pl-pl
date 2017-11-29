---
title: "Operatory konwersji (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5277c1160c604ee56ff575df5bd603e115588d21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-operators-c-programming-guide"></a><span data-ttu-id="ed9c3-102">Operatory konwersji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ed9c3-102">Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="ed9c3-103">C# umożliwia deweloperom zadeklarować konwersje klasy lub struktury, dzięki czemu mogą być konwertowane klasy lub struktury, aby lub z innych klas lub struktur lub typy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="ed9c3-103">C# enables programmers to declare conversions on classes or structs so that classes or structs can be converted to and/or from other classes or structs, or basic types.</span></span> <span data-ttu-id="ed9c3-104">Konwersje zdefiniowano like — operatory o nazwie dla typu, które umożliwiają one konwertowanie.</span><span class="sxs-lookup"><span data-stu-id="ed9c3-104">Conversions are defined like operators and are named for the type to which they convert.</span></span> <span data-ttu-id="ed9c3-105">Typ argumentu, który ma zostać przekonwertowany lub typ wyniku konwersji, ale nie oba musi być typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="ed9c3-105">Either the type of the argument to be converted, or the type of the result of the conversion, but not both, must be the containing type.</span></span>  
  
 [!code-csharp[csProgGuideStatements#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/conversion-operators_1.cs)]  
  
## <a name="conversion-operators-overview"></a><span data-ttu-id="ed9c3-106">Omówienie operatorów konwersji</span><span class="sxs-lookup"><span data-stu-id="ed9c3-106">Conversion Operators Overview</span></span>  
 <span data-ttu-id="ed9c3-107">Operatory konwersji mieć następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ed9c3-107">Conversion operators have the following properties:</span></span>  
  
-   <span data-ttu-id="ed9c3-108">Konwersje zadeklarowany jako `implicit` wykonywane automatycznie, gdy jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="ed9c3-108">Conversions declared as `implicit` occur automatically when it is required.</span></span>  
  
-   <span data-ttu-id="ed9c3-109">Konwersje zadeklarowany jako `explicit` wymagają rzutowanie do wywołania.</span><span class="sxs-lookup"><span data-stu-id="ed9c3-109">Conversions declared as `explicit` require a cast to be called.</span></span>  
  
-   <span data-ttu-id="ed9c3-110">Wszystkie konwersje musi być zadeklarowany jako `static`.</span><span class="sxs-lookup"><span data-stu-id="ed9c3-110">All conversions must be declared as `static`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ed9c3-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ed9c3-111">Related Sections</span></span>  
 <span data-ttu-id="ed9c3-112">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="ed9c3-112">For more information:</span></span>  
  
-   [<span data-ttu-id="ed9c3-113">Używanie operatorów konwersji</span><span class="sxs-lookup"><span data-stu-id="ed9c3-113">Using Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [<span data-ttu-id="ed9c3-114">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="ed9c3-114">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [<span data-ttu-id="ed9c3-115">Porady: Implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="ed9c3-115">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [<span data-ttu-id="ed9c3-116">jawne</span><span class="sxs-lookup"><span data-stu-id="ed9c3-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [<span data-ttu-id="ed9c3-117">niejawne</span><span class="sxs-lookup"><span data-stu-id="ed9c3-117">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [<span data-ttu-id="ed9c3-118">statyczne</span><span class="sxs-lookup"><span data-stu-id="ed9c3-118">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a><span data-ttu-id="ed9c3-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed9c3-119">See Also</span></span>  
 <xref:System.Convert>  
 [<span data-ttu-id="ed9c3-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ed9c3-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ed9c3-121">Tworzenie łańcucha zdefiniowane przez użytkownika Konwersje jawne w języku C#</span><span class="sxs-lookup"><span data-stu-id="ed9c3-121">Chained user-defined explicit conversions in C#</span></span>](http://go.microsoft.com/fwlink/?LinkId=112384)
