---
title: Oczekiwano deklaracji
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 64ee75c93615f57b15fea29f06fff500a395ba0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803834"
---
# <a name="declaration-expected"></a><span data-ttu-id="3385d-102">Oczekiwano deklaracji</span><span class="sxs-lookup"><span data-stu-id="3385d-102">Declaration expected</span></span>
<span data-ttu-id="3385d-103">Nondeclarative instrukcji, takie jak przypisania lub instrukcji pętli jest wykonywane poza dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="3385d-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="3385d-104">Tylko deklaracje mogą poza procedur.</span><span class="sxs-lookup"><span data-stu-id="3385d-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="3385d-105">Alternatywnie elementu programistycznego została zadeklarowana bez słowa kluczowego deklaracji takich jak `Dim` lub `Const`.</span><span class="sxs-lookup"><span data-stu-id="3385d-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="3385d-106">**Identyfikator błędu:** BC30188</span><span class="sxs-lookup"><span data-stu-id="3385d-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3385d-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="3385d-107">To correct this error</span></span>  
  
- <span data-ttu-id="3385d-108">Przenieś instrukcję nondeclarative treści procedury.</span><span class="sxs-lookup"><span data-stu-id="3385d-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
- <span data-ttu-id="3385d-109">Rozpocznij deklaracji z odpowiednią deklarację słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="3385d-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
- <span data-ttu-id="3385d-110">Upewnij się, że deklaracja słowo kluczowe nie jest błędnie wpisana.</span><span class="sxs-lookup"><span data-stu-id="3385d-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3385d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3385d-111">See also</span></span>

- [<span data-ttu-id="3385d-112">Procedury</span><span class="sxs-lookup"><span data-stu-id="3385d-112">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="3385d-113">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3385d-113">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
