---
title: Stałe i wyliczenia w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- Visual Basic code, constants
- constants [Visual Basic]
- object libraries, Object Browser
- Visual Basic code, enumerations
- declaring constants [Visual Basic], enumerations
- naming conventions [Visual Basic], constants
- Visual Basic code, improving readability with constants
ms.assetid: c8aba36e-fa47-4a33-8b68-cb2009218270
ms.openlocfilehash: dfd9330210dd748d739cd8da2985795099beacd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907299"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="2dd2d-102">Stałe i wyliczenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2dd2d-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="2dd2d-103">Stałe są sposobem Użyj nazw opisowych, zamiast wartość, która nie zmienia się.</span><span class="sxs-lookup"><span data-stu-id="2dd2d-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="2dd2d-104">Stałe przechowywać wartości, które jak wskazuje nazwa, pozostają stałe w trakcie wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2dd2d-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="2dd2d-105">Stałe służy do zapewnienia opisowych nazw, a nie liczby, dzięki czemu bardziej czytelny kod.</span><span class="sxs-lookup"><span data-stu-id="2dd2d-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="2dd2d-106">Wyliczenia zapewniają wygodny sposób pracy z zestawami pokrewnych stałych i skojarzyć wartości stałych o nazwach.</span><span class="sxs-lookup"><span data-stu-id="2dd2d-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="2dd2d-107">Na przykład można zadeklarować wyliczenie zbiór stałe całkowite skojarzone z dni tygodnia, a w kodzie następnie używać nazwy dni, a nie ich wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="2dd2d-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2dd2d-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2dd2d-108">In This Section</span></span>  
  
|<span data-ttu-id="2dd2d-109">Termin</span><span class="sxs-lookup"><span data-stu-id="2dd2d-109">Term</span></span>|<span data-ttu-id="2dd2d-110">Definicja</span><span class="sxs-lookup"><span data-stu-id="2dd2d-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="2dd2d-111">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="2dd2d-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="2dd2d-112">Tematy w tej sekcji opisano, stałe i ich zastosowań.</span><span class="sxs-lookup"><span data-stu-id="2dd2d-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="2dd2d-113">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="2dd2d-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="2dd2d-114">Tematy w tej sekcji opisano, wyliczenia i ich zastosowań.</span><span class="sxs-lookup"><span data-stu-id="2dd2d-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="2dd2d-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2dd2d-115">Related Sections</span></span>  
  
|<span data-ttu-id="2dd2d-116">Termin</span><span class="sxs-lookup"><span data-stu-id="2dd2d-116">Term</span></span>|<span data-ttu-id="2dd2d-117">Definicja</span><span class="sxs-lookup"><span data-stu-id="2dd2d-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="2dd2d-118">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2dd2d-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="2dd2d-119">W tym artykule opisano `Const` instrukcję, która służy do deklarowania stałe.</span><span class="sxs-lookup"><span data-stu-id="2dd2d-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="2dd2d-120">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2dd2d-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="2dd2d-121">W tym artykule opisano `Enum` instrukcję, która służy do tworzenia wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2dd2d-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="2dd2d-122">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2dd2d-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="2dd2d-123">W tym artykule opisano `Option Explicit` instrukcję, która jest używana na poziomie modułu w celu wymuszenia jawnej deklaracji wszystkich zmiennych w module.</span><span class="sxs-lookup"><span data-stu-id="2dd2d-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="2dd2d-124">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2dd2d-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="2dd2d-125">W tym artykule opisano `Option Infer` instrukcję, która umożliwia użycie wnioskowania o typie lokalnym w zadeklarowania zmiennych.</span><span class="sxs-lookup"><span data-stu-id="2dd2d-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="2dd2d-126">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2dd2d-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="2dd2d-127">W tym artykule opisano `Option Strict` instrukcję, która ogranicza niejawne konwersje typów danych można tylko konwersje rozszerzające, nie zezwalają na późne powiązania, a nie zezwalają na niejawnego wpisywania, które spowodowało, że `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="2dd2d-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
