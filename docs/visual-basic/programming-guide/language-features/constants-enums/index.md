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
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="63d7a-102">Stałe i wyliczenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63d7a-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="63d7a-103">Constants are a way to use meaningful names in place of a value that does not change.</span><span class="sxs-lookup"><span data-stu-id="63d7a-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="63d7a-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span><span class="sxs-lookup"><span data-stu-id="63d7a-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="63d7a-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span><span class="sxs-lookup"><span data-stu-id="63d7a-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="63d7a-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span><span class="sxs-lookup"><span data-stu-id="63d7a-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="63d7a-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span><span class="sxs-lookup"><span data-stu-id="63d7a-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63d7a-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="63d7a-108">In This Section</span></span>  
  
|<span data-ttu-id="63d7a-109">Termin</span><span class="sxs-lookup"><span data-stu-id="63d7a-109">Term</span></span>|<span data-ttu-id="63d7a-110">Definicja</span><span class="sxs-lookup"><span data-stu-id="63d7a-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="63d7a-111">Stałe — przegląd</span><span class="sxs-lookup"><span data-stu-id="63d7a-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="63d7a-112">Topics in this section describe constants and their uses.</span><span class="sxs-lookup"><span data-stu-id="63d7a-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="63d7a-113">Wyliczenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="63d7a-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="63d7a-114">Topics in this section describe enumerations and their uses.</span><span class="sxs-lookup"><span data-stu-id="63d7a-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="63d7a-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="63d7a-115">Related Sections</span></span>  
  
|<span data-ttu-id="63d7a-116">Termin</span><span class="sxs-lookup"><span data-stu-id="63d7a-116">Term</span></span>|<span data-ttu-id="63d7a-117">Definicja</span><span class="sxs-lookup"><span data-stu-id="63d7a-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="63d7a-118">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="63d7a-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="63d7a-119">Describes the `Const` statement, which is used to declare constants.</span><span class="sxs-lookup"><span data-stu-id="63d7a-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="63d7a-120">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="63d7a-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="63d7a-121">Describes the `Enum` statement, which is used to create enumerations.</span><span class="sxs-lookup"><span data-stu-id="63d7a-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="63d7a-122">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="63d7a-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="63d7a-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span><span class="sxs-lookup"><span data-stu-id="63d7a-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="63d7a-124">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="63d7a-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="63d7a-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span><span class="sxs-lookup"><span data-stu-id="63d7a-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="63d7a-126">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="63d7a-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="63d7a-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span><span class="sxs-lookup"><span data-stu-id="63d7a-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
