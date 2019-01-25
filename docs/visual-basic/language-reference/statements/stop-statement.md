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
ms.openlocfilehash: fa9a1942903dff6f673d87b67ebcad047a410425
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624785"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="f65cb-102">Stop — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f65cb-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="f65cb-103">Wstrzymuje wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="f65cb-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f65cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f65cb-104">Syntax</span></span>  
  
```  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="f65cb-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f65cb-105">Remarks</span></span>  
 <span data-ttu-id="f65cb-106">Instrukcję `Stop` można umieścić w dowolnym miejscu procedur, aby wstrzymać ich wykonanie.</span><span class="sxs-lookup"><span data-stu-id="f65cb-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="f65cb-107">Użycie instrukcji `Stop` przypomina ustawienie punktu przerwania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f65cb-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="f65cb-108">Instrukcja `Stop` wstrzymuje wykonywanie, ale w przeciwieństwie do `End` nie zamyka żadnych plików ani nie czyści żadnych zmiennych — chyba że występuje w skompilowanym pliku wykonywalnym (.exe).</span><span class="sxs-lookup"><span data-stu-id="f65cb-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f65cb-109">Jeśli instrukcja `Stop` występuje w kodzie, który działa poza zintegrowanym środowiskiem programistycznym (IDE), wywoływany jest debuger.</span><span class="sxs-lookup"><span data-stu-id="f65cb-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="f65cb-110">Stanie się tak niezależnie od tego, czy kod został skompilowany w trybie debugowania, czy wersji wdrożeniowej.</span><span class="sxs-lookup"><span data-stu-id="f65cb-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f65cb-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="f65cb-111">Example</span></span>  
 <span data-ttu-id="f65cb-112">W tym przykładzie użyto instrukcji `Stop`, aby wstrzymać wykonanie każdej iteracji w pętli `For...Next`.</span><span class="sxs-lookup"><span data-stu-id="f65cb-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f65cb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f65cb-113">See also</span></span>
- [<span data-ttu-id="f65cb-114">Instrukcja End</span><span class="sxs-lookup"><span data-stu-id="f65cb-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
