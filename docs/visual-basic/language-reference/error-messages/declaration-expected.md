---
title: Oczekiwano deklaracji
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords: BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97bd1701a8a07c39d08a9276cdb929bc9425c1f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="declaration-expected"></a><span data-ttu-id="0519e-102">Oczekiwano deklaracji</span><span class="sxs-lookup"><span data-stu-id="0519e-102">Declaration expected</span></span>
<span data-ttu-id="0519e-103">Zestawienie nondeclarative, takich jak przypisanie ani instrukcji pętli jest wykonywane poza dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="0519e-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="0519e-104">Tylko deklaracji są dozwolone zewnętrznej procedury.</span><span class="sxs-lookup"><span data-stu-id="0519e-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="0519e-105">Alternatywnie elementu programistycznego została zadeklarowana bez słowa kluczowego deklaracji takich jak `Dim` lub `Const`.</span><span class="sxs-lookup"><span data-stu-id="0519e-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="0519e-106">**Identyfikator błędu:** BC30188</span><span class="sxs-lookup"><span data-stu-id="0519e-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0519e-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0519e-107">To correct this error</span></span>  
  
-   <span data-ttu-id="0519e-108">Przenieś nondeclarative instrukcji w treści procedury.</span><span class="sxs-lookup"><span data-stu-id="0519e-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
-   <span data-ttu-id="0519e-109">Rozpocznij deklaracji z odpowiednią deklarację słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="0519e-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
-   <span data-ttu-id="0519e-110">Upewnij się, że słowo kluczowe deklaracja nie jest błędna.</span><span class="sxs-lookup"><span data-stu-id="0519e-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0519e-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0519e-111">See Also</span></span>  
 [<span data-ttu-id="0519e-112">Procedury</span><span class="sxs-lookup"><span data-stu-id="0519e-112">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="0519e-113">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="0519e-113">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
