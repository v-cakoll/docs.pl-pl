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
ms.openlocfilehash: 80d6734945324f3f517b256051486273f6b687ec
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827994"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="b385d-102">Stop — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b385d-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="b385d-103">Wstrzymuje wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="b385d-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b385d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b385d-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="b385d-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b385d-105">Remarks</span></span>  
 <span data-ttu-id="b385d-106">Instrukcję `Stop` można umieścić w dowolnym miejscu procedur, aby wstrzymać ich wykonanie.</span><span class="sxs-lookup"><span data-stu-id="b385d-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="b385d-107">Użycie instrukcji `Stop` przypomina ustawienie punktu przerwania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b385d-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="b385d-108">Instrukcja `Stop` wstrzymuje wykonywanie, ale w przeciwieństwie do `End` nie zamyka żadnych plików ani nie czyści żadnych zmiennych — chyba że występuje w skompilowanym pliku wykonywalnym (.exe).</span><span class="sxs-lookup"><span data-stu-id="b385d-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b385d-109">Jeśli instrukcja `Stop` występuje w kodzie, który działa poza zintegrowanym środowiskiem programistycznym (IDE), wywoływany jest debuger.</span><span class="sxs-lookup"><span data-stu-id="b385d-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="b385d-110">Stanie się tak niezależnie od tego, czy kod został skompilowany w trybie debugowania, czy wersji wdrożeniowej.</span><span class="sxs-lookup"><span data-stu-id="b385d-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b385d-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="b385d-111">Example</span></span>  
 <span data-ttu-id="b385d-112">W tym przykładzie użyto instrukcji `Stop`, aby wstrzymać wykonanie każdej iteracji w pętli `For...Next`.</span><span class="sxs-lookup"><span data-stu-id="b385d-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="b385d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b385d-113">See also</span></span>

- [<span data-ttu-id="b385d-114">Instrukcja End</span><span class="sxs-lookup"><span data-stu-id="b385d-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
