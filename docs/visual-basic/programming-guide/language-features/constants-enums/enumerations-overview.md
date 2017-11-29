---
title: "Enumerations — Przegląd (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, enumerations
- enumerations [Visual Basic], about enumerations
ms.assetid: b42a38ee-5e77-4f99-a037-e3a127ead89c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d50e6bae880e5dc4dcde203708c6b07c05bb4e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="enumerations-overview-visual-basic"></a><span data-ttu-id="5b2b0-102">Enumerations — Przegląd (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b2b0-102">Enumerations Overview (Visual Basic)</span></span>
<span data-ttu-id="5b2b0-103">Wyliczenia zapewnić wygodny sposób pracy z zestawów powiązanych stałych i do skojarzenia z nazwami wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="5b2b0-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="5b2b0-104">Na przykład można zadeklarować wyliczenia dla zestawu stałe całkowite skojarzone z dni tygodnia, a następnie użyć nazwy dni, a nie ich wartości całkowite w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5b2b0-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="tasks-involving-enumerations"></a><span data-ttu-id="5b2b0-105">Zadania obejmujące wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5b2b0-105">Tasks involving Enumerations</span></span>  
 <span data-ttu-id="5b2b0-106">Poniższa tabela zawiera listę typowych zadań dotyczących wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5b2b0-106">The following table lists common tasks involving enumerations.</span></span>  
  
|<span data-ttu-id="5b2b0-107">Wymagana czynność</span><span class="sxs-lookup"><span data-stu-id="5b2b0-107">To do this</span></span>|<span data-ttu-id="5b2b0-108">Zobacz</span><span class="sxs-lookup"><span data-stu-id="5b2b0-108">See</span></span>|  
|----------------|---------|  
|<span data-ttu-id="5b2b0-109">Znajdź wyliczenie wstępnie zdefiniowane</span><span class="sxs-lookup"><span data-stu-id="5b2b0-109">Find a pre-defined enumeration</span></span>|[<span data-ttu-id="5b2b0-110">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5b2b0-110">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)|  
|<span data-ttu-id="5b2b0-111">Deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="5b2b0-111">Declare an enumeration</span></span>|[<span data-ttu-id="5b2b0-112">Porady: deklarowanie wyliczeń</span><span class="sxs-lookup"><span data-stu-id="5b2b0-112">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)|  
|<span data-ttu-id="5b2b0-113">Pełnej nazwy wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5b2b0-113">Fully qualify an enumeration's name</span></span>|[<span data-ttu-id="5b2b0-114">Wyliczenie i kwantyfikacja nazwy</span><span class="sxs-lookup"><span data-stu-id="5b2b0-114">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)|  
|<span data-ttu-id="5b2b0-115">Odwołuje się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5b2b0-115">Refer to an enumeration member</span></span>|[<span data-ttu-id="5b2b0-116">Porady: odwołuje się do elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5b2b0-116">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)|  
|<span data-ttu-id="5b2b0-117">Iterowanie za pomocą — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5b2b0-117">Iterate through an enumeration</span></span>|[<span data-ttu-id="5b2b0-118">Porady: iterowanie za pomocą wyliczania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b2b0-118">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)|  
|<span data-ttu-id="5b2b0-119">Określanie ciągu skojarzonego z wyliczeniem</span><span class="sxs-lookup"><span data-stu-id="5b2b0-119">Determine the string associated with an enumeration</span></span>|[<span data-ttu-id="5b2b0-120">Porady: Określanie ciągu skojarzonego z wartością wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5b2b0-120">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)|  
|<span data-ttu-id="5b2b0-121">Zdecyduj, kiedy należy używać wyliczania</span><span class="sxs-lookup"><span data-stu-id="5b2b0-121">Decide when to use an enumeration</span></span>|[<span data-ttu-id="5b2b0-122">Kiedy stosować wyliczanie</span><span class="sxs-lookup"><span data-stu-id="5b2b0-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)|  
  
## <a name="see-also"></a><span data-ttu-id="5b2b0-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b2b0-123">See Also</span></span>  
 [<span data-ttu-id="5b2b0-124">Stałe — Przegląd</span><span class="sxs-lookup"><span data-stu-id="5b2b0-124">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="5b2b0-125">Stałe zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="5b2b0-125">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [<span data-ttu-id="5b2b0-126">Porady: deklarowanie stałej</span><span class="sxs-lookup"><span data-stu-id="5b2b0-126">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [<span data-ttu-id="5b2b0-127">Stała i typy literałów</span><span class="sxs-lookup"><span data-stu-id="5b2b0-127">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="5b2b0-128">Enum — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5b2b0-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
