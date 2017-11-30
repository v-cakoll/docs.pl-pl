---
title: "Stałe i wyliczenia w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5bbba6434d8b0a5c02882d1ac858296fd8eeb346
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="constants-and-enumerations-in-visual-basic"></a><span data-ttu-id="96a50-102">Stałe i wyliczenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="96a50-102">Constants and Enumerations in Visual Basic</span></span>
<span data-ttu-id="96a50-103">Stałe są sposobem użycia łatwy do rozpoznania nazwy zamiast wartości, który nie ulega zmianie.</span><span class="sxs-lookup"><span data-stu-id="96a50-103">Constants are a way to use meaningful names in place of a value that does not change.</span></span> <span data-ttu-id="96a50-104">Stałe przechowywać wartości, które, jak nazwa wskazuje, pozostają stałe w trakcie wykonywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="96a50-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="96a50-105">Stałe służy do nadania łatwy do rozpoznania nazwy, zamiast numery wprowadzania czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="96a50-105">You can use constants to provide meaningful names, instead of numbers, making your code more readable.</span></span>  
  
 <span data-ttu-id="96a50-106">Wyliczenia oferują wygodny do pracy z zestawów powiązanych stałych i do skojarzenia z nazwami wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="96a50-106">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="96a50-107">Na przykład można zadeklarować wyliczenia dla zestawu stałe całkowite skojarzone z dni tygodnia, a następnie użyć nazwy dni, a nie ich wartości całkowite w kodzie.</span><span class="sxs-lookup"><span data-stu-id="96a50-107">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="96a50-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="96a50-108">In This Section</span></span>  
  
|<span data-ttu-id="96a50-109">Termin</span><span class="sxs-lookup"><span data-stu-id="96a50-109">Term</span></span>|<span data-ttu-id="96a50-110">Definicja</span><span class="sxs-lookup"><span data-stu-id="96a50-110">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="96a50-111">Stałe — Przegląd</span><span class="sxs-lookup"><span data-stu-id="96a50-111">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)|<span data-ttu-id="96a50-112">Tematy w tej sekcji opisano, stałe i ich zastosowań.</span><span class="sxs-lookup"><span data-stu-id="96a50-112">Topics in this section describe constants and their uses.</span></span>|  
|[<span data-ttu-id="96a50-113">Enumerations — Przegląd</span><span class="sxs-lookup"><span data-stu-id="96a50-113">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)|<span data-ttu-id="96a50-114">Tematy w tej sekcji opisano, wyliczenia i ich zastosowań.</span><span class="sxs-lookup"><span data-stu-id="96a50-114">Topics in this section describe enumerations and their uses.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="96a50-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="96a50-115">Related Sections</span></span>  
  
|<span data-ttu-id="96a50-116">Termin</span><span class="sxs-lookup"><span data-stu-id="96a50-116">Term</span></span>|<span data-ttu-id="96a50-117">Definicja</span><span class="sxs-lookup"><span data-stu-id="96a50-117">Definition</span></span>|  
|---|---|  
|[<span data-ttu-id="96a50-118">Const — instrukcja</span><span class="sxs-lookup"><span data-stu-id="96a50-118">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="96a50-119">W tym artykule opisano `Const` instrukcja, która służy do deklarowania stałe.</span><span class="sxs-lookup"><span data-stu-id="96a50-119">Describes the `Const` statement, which is used to declare constants.</span></span>|  
|[<span data-ttu-id="96a50-120">Enum — instrukcja</span><span class="sxs-lookup"><span data-stu-id="96a50-120">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)|<span data-ttu-id="96a50-121">W tym artykule opisano `Enum` instrukcja, która służy do tworzenia wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="96a50-121">Describes the `Enum` statement, which is used to create enumerations.</span></span>|  
|[<span data-ttu-id="96a50-122">Option Explicit — instrukcja</span><span class="sxs-lookup"><span data-stu-id="96a50-122">Option Explicit Statement</span></span>](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)|<span data-ttu-id="96a50-123">W tym artykule opisano `Option Explicit` instrukcja, która jest używana na poziomie modułu, aby wymusić jawnej deklaracji wszystkich zmiennych w module.</span><span class="sxs-lookup"><span data-stu-id="96a50-123">Describes the `Option Explicit` statement, which is used at module level to force explicit declaration of all variables in that module.</span></span>|  
|[<span data-ttu-id="96a50-124">Option Infer — instrukcja</span><span class="sxs-lookup"><span data-stu-id="96a50-124">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)|<span data-ttu-id="96a50-125">W tym artykule opisano `Option Infer` instrukcja, która umożliwia użycie wnioskowania o typie lokalnym przy deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="96a50-125">Describes the `Option Infer` statement, which enables the use of local type inference in declaring variables.</span></span>|  
|[<span data-ttu-id="96a50-126">Option Strict — instrukcja</span><span class="sxs-lookup"><span data-stu-id="96a50-126">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="96a50-127">W tym artykule opisano `Option Strict` instrukcja, która ogranicza niejawne konwersje typów danych można tylko rozszerzanie konwersji, uniemożliwia późne wiązanie i nie zezwala na niejawne wpisanie, który daje w `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="96a50-127">Describes the `Option Strict` statement, which restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.</span></span>|
