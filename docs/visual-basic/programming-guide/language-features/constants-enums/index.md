---
title: Stałe i wyliczenia
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
ms.openlocfilehash: 858f22df26d44f47848921ee862c1d4c1ca1fc60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353984"
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="6163b-102">Stałe i wyliczenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6163b-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="6163b-103">Stałe są sposobem używania nazw znaczących zamiast wartości, która nie jest zmieniana.</span><span class="sxs-lookup"><span data-stu-id="6163b-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="6163b-104">Stałe wartości magazynu, których nazwa to oznacza, pozostają stałe przez cały czas wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6163b-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="6163b-105">Możesz użyć stałych, aby podać znaczące nazwy, a nie liczby, co sprawia, że kod jest bardziej czytelny.</span><span class="sxs-lookup"><span data-stu-id="6163b-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="6163b-106">Wyliczenia zapewniają wygodny sposób pracy z zestawami powiązanych stałych i kojarzenia wartości stałych z nazwami.</span><span class="sxs-lookup"><span data-stu-id="6163b-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="6163b-107">Na przykład można zadeklarować Wyliczenie dla zestawu stałych całkowitych skojarzonych z dniami tygodnia, a następnie użyć nazw dni, a nie ich wartości całkowitych w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6163b-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6163b-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6163b-108">In This Section</span></span>  
  
|<span data-ttu-id="6163b-109">Termin</span><span class="sxs-lookup"><span data-stu-id="6163b-109">Term</span></span>|<span data-ttu-id="6163b-110">Definicja</span><span class="sxs-lookup"><span data-stu-id="6163b-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="6163b-111">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="6163b-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="6163b-112">W tematach w tej sekcji opisano stałe i ich zastosowania.</span><span class="sxs-lookup"><span data-stu-id="6163b-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="6163b-113">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="6163b-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="6163b-114">Tematy w tej sekcji opisują wyliczenia i ich zastosowania.</span><span class="sxs-lookup"><span data-stu-id="6163b-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="6163b-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="6163b-115">Related Sections</span></span>  
  
|<span data-ttu-id="6163b-116">Termin</span><span class="sxs-lookup"><span data-stu-id="6163b-116">Term</span></span>|<span data-ttu-id="6163b-117">Definicja</span><span class="sxs-lookup"><span data-stu-id="6163b-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="6163b-118">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6163b-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="6163b-119">Opisuje instrukcję `Const`, która jest używana do deklarowania stałych.</span><span class="sxs-lookup"><span data-stu-id="6163b-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="6163b-120">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6163b-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="6163b-121">Opisuje instrukcję `Enum`, która jest używana do tworzenia wyliczeń.</span><span class="sxs-lookup"><span data-stu-id="6163b-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="6163b-122">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6163b-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="6163b-123">Opisuje instrukcję `Option Explicit`, która jest używana na poziomie modułu, aby wymusić jawną deklarację wszystkich zmiennych w tym module.</span><span class="sxs-lookup"><span data-stu-id="6163b-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="6163b-124">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6163b-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="6163b-125">Opisuje instrukcję `Option Infer`, która umożliwia korzystanie z wnioskowania o typie lokalnym podczas deklarowania zmiennych.</span><span class="sxs-lookup"><span data-stu-id="6163b-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="6163b-126">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6163b-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="6163b-127">Opisuje instrukcje `Option Strict`, które ograniczają niejawne konwersje typów danych tylko w celu rozszerzania konwersji, uniemożliwiają późne wiązanie i nie dopuszczają niejawnego wpisywania w wyniku typu `Object`.</span><span class="sxs-lookup"><span data-stu-id="6163b-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
