---
title: Stop, instrukcja
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
ms.openlocfilehash: 2ef1e2f9045e5509e11557c9fdaf3edd2786b72c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404229"
---
# <a name="stop-statement-visual-basic"></a><span data-ttu-id="5f33e-102">Stop — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f33e-102">Stop Statement (Visual Basic)</span></span>
<span data-ttu-id="5f33e-103">Wstrzymuje wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="5f33e-103">Suspends execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f33e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f33e-104">Syntax</span></span>  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a><span data-ttu-id="5f33e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f33e-105">Remarks</span></span>  
 <span data-ttu-id="5f33e-106">Możesz umieścić `Stop` instrukcje w dowolnym miejscu procedury, aby wstrzymać wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="5f33e-106">You can place `Stop` statements anywhere in procedures to suspend execution.</span></span> <span data-ttu-id="5f33e-107">Użycie `Stop` instrukcji jest podobne do ustawiania punktu przerwania w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5f33e-107">Using the `Stop` statement is similar to setting a breakpoint in the code.</span></span>  
  
 <span data-ttu-id="5f33e-108">`Stop`Instrukcja zawiesza wykonywanie, ale w przeciwieństwie do `End` siebie nie zamyka żadnych plików ani nie czyści żadnych zmiennych, chyba że występuje w skompilowanym pliku wykonywalnym (. exe).</span><span class="sxs-lookup"><span data-stu-id="5f33e-108">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f33e-109">Jeśli `Stop` instrukcja jest napotkana w kodzie, który działa poza zintegrowanym środowiskiem programistycznym (IDE), debuger jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="5f33e-109">If the `Stop` statement is encountered in code that is running outside of the integrated development environment (IDE), the debugger is invoked.</span></span> <span data-ttu-id="5f33e-110">Ta wartość jest prawdziwa niezależnie od tego, czy kod został skompilowany w trybie debugowania czy sprzedaży detalicznej.</span><span class="sxs-lookup"><span data-stu-id="5f33e-110">This is true regardless of whether the code was compiled in debug or retail mode.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f33e-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f33e-111">Example</span></span>  
 <span data-ttu-id="5f33e-112">W tym przykładzie używa `Stop` instrukcji, aby wstrzymać wykonywanie dla każdej iteracji za pośrednictwem `For...Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="5f33e-112">This example uses the `Stop` statement to suspend execution for each iteration through the `For...Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="5f33e-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f33e-113">See also</span></span>

- [<span data-ttu-id="5f33e-114">End — instrukcja</span><span class="sxs-lookup"><span data-stu-id="5f33e-114">End Statement</span></span>](end-statement.md)
