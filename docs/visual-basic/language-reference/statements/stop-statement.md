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
ms.openlocfilehash: e9382ee34842fc3a3b4b23f71848bda602c99780
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583225"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="0e0cb-102">Stop — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e0cb-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="0e0cb-103">Wstrzymuje wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="0e0cb-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e0cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e0cb-104">Syntax</span></span>  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="0e0cb-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e0cb-105">Remarks</span></span>  
 <span data-ttu-id="0e0cb-106">Instrukcje `Stop` można umieścić w dowolnym miejscu w procedurach, aby wstrzymać wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="0e0cb-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="0e0cb-107">Użycie instrukcji `Stop` jest podobne do ustawiania punktu przerwania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0e0cb-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="0e0cb-108">Instrukcja `Stop` wstrzymuje wykonywanie, ale w przeciwieństwie do `End`, nie zamyka żadnych plików ani nie czyści żadnych zmiennych, chyba że zostanie napotkana w skompilowanym pliku wykonywalnym (. exe).</span><span class="sxs-lookup"><span data-stu-id="0e0cb-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e0cb-109">Jeśli instrukcja `Stop` występuje w kodzie, który działa poza zintegrowanym środowiskiem programistycznym (IDE), debuger jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="0e0cb-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="0e0cb-110">Ta wartość jest prawdziwa niezależnie od tego, czy kod został skompilowany w trybie debugowania czy sprzedaży detalicznej.</span><span class="sxs-lookup"><span data-stu-id="0e0cb-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e0cb-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0e0cb-111">Example</span></span>  
 <span data-ttu-id="0e0cb-112">Ten przykład używa instrukcji `Stop`, aby zawiesić wykonywanie dla każdej iteracji za pośrednictwem pętli `For...Next`.</span><span class="sxs-lookup"><span data-stu-id="0e0cb-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="0e0cb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e0cb-113">See also</span></span>

- [<span data-ttu-id="0e0cb-114">End, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0e0cb-114">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
