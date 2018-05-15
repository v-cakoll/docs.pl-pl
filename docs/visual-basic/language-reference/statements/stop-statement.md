---
title: Stop — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: 955a3b6a2f7dc1d0e9823ed6d500ab7f7f9fe5b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="970ae-102">Stop — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="970ae-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="970ae-103">Wstrzymuje wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="970ae-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="970ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="970ae-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="970ae-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="970ae-105">Remarks</span></span>  
 <span data-ttu-id="970ae-106">Możesz umieścić `Stop` instrukcje w dowolnym miejscu procedury, aby wstrzymać wykonywania.</span><span class="sxs-lookup"><span data-stu-id="970ae-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="970ae-107">Przy użyciu `Stop` instrukcji jest podobne do punktu przerwania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="970ae-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="970ae-108">`Stop` Instrukcji wstrzymuje wykonywanie, lecz w przeciwieństwie do `End`, zamknij wszystkie pliki lub nie wyczyść wszystkie zmienne, chyba że jest wystąpił w pliku skompilowanego pliku wykonywalnego (.exe).</span><span class="sxs-lookup"><span data-stu-id="970ae-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="970ae-109">Jeśli `Stop` napotkano instrukcji w kodzie, który działa poza zintegrowane środowisko programistyczne (IDE), Debuger jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="970ae-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="970ae-110">Dotyczy to niezależnie od tego, czy kod został skompilowany w trybie debugowania lub wersji detalicznej.</span><span class="sxs-lookup"><span data-stu-id="970ae-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="970ae-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="970ae-111">Example</span></span>  
 <span data-ttu-id="970ae-112">W tym przykładzie użyto `Stop` instrukcji, aby wstrzymać wykonywania dla każdej iteracji za pośrednictwem `For...Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="970ae-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="970ae-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="970ae-113">See Also</span></span>  
 [<span data-ttu-id="970ae-114">End Statement</span><span class="sxs-lookup"><span data-stu-id="970ae-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
