---
title: Oczekiwano deklaracji
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: c5c9b665b78c7c63c55292e38cc96ee8b2962a61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="declaration-expected"></a><span data-ttu-id="d2852-102">Oczekiwano deklaracji</span><span class="sxs-lookup"><span data-stu-id="d2852-102">Declaration expected</span></span>
<span data-ttu-id="d2852-103">Zestawienie nondeclarative, takich jak przypisanie ani instrukcji pętli jest wykonywane poza dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="d2852-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="d2852-104">Tylko deklaracji są dozwolone zewnętrznej procedury.</span><span class="sxs-lookup"><span data-stu-id="d2852-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="d2852-105">Alternatywnie elementu programistycznego została zadeklarowana bez słowa kluczowego deklaracji takich jak `Dim` lub `Const`.</span><span class="sxs-lookup"><span data-stu-id="d2852-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="d2852-106">**Identyfikator błędu:** BC30188</span><span class="sxs-lookup"><span data-stu-id="d2852-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d2852-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d2852-107">To correct this error</span></span>  
  
-   <span data-ttu-id="d2852-108">Przenieś nondeclarative instrukcji w treści procedury.</span><span class="sxs-lookup"><span data-stu-id="d2852-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
-   <span data-ttu-id="d2852-109">Rozpocznij deklaracji z odpowiednią deklarację słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="d2852-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
-   <span data-ttu-id="d2852-110">Upewnij się, że słowo kluczowe deklaracja nie jest błędna.</span><span class="sxs-lookup"><span data-stu-id="d2852-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2852-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2852-111">See Also</span></span>  
 [<span data-ttu-id="d2852-112">Procedury</span><span class="sxs-lookup"><span data-stu-id="d2852-112">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="d2852-113">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d2852-113">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
