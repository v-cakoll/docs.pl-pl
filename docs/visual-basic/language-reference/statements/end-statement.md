---
title: End — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: 9307cf10e6125441bd49baa0e663a5a13f234005
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944464"
---
# <a name="end-statement"></a><span data-ttu-id="de98d-102">End — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="de98d-102">End Statement</span></span>
<span data-ttu-id="de98d-103">Kończy wykonywanie natychmiast.</span><span class="sxs-lookup"><span data-stu-id="de98d-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de98d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de98d-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="de98d-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de98d-105">Remarks</span></span>  
 <span data-ttu-id="de98d-106">Możesz umieścić `End` instrukcję w dowolnym miejscu procedury, aby wymusić, że cała aplikacja przestanie działać.</span><span class="sxs-lookup"><span data-stu-id="de98d-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="de98d-107">`End`zamyka wszystkie pliki otwierane za `Open` pomocą instrukcji i czyści wszystkie zmienne aplikacji.</span><span class="sxs-lookup"><span data-stu-id="de98d-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="de98d-108">Aplikacja jest zamykana natychmiast, gdy nie ma żadnych innych programów przechowujących odwołania do jego obiektów i żaden z jego kodu nie jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="de98d-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de98d-109">Instrukcja kończy wykonywanie kodu nieoczekiwanie i nie `Dispose` wywołuje metody lub `Finalize` ani żadnego innego kodu Visual Basic. `End`</span><span class="sxs-lookup"><span data-stu-id="de98d-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="de98d-110">Odwołania do obiektów przechowywane przez inne programy są unieważnione.</span><span class="sxs-lookup"><span data-stu-id="de98d-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="de98d-111">Jeśli instrukcja jest napotkana `Try` w bloku lub `Catch` , formant nie przechodzi do odpowiadającego `Finally` bloku. `End`</span><span class="sxs-lookup"><span data-stu-id="de98d-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="de98d-112">Instrukcja `Stop` wstrzymuje wykonywanie, ale w przeciwieństwie do `End` nie zamyka żadnych plików ani nie czyści żadnych zmiennych — chyba że występuje w skompilowanym pliku wykonywalnym (.exe).</span><span class="sxs-lookup"><span data-stu-id="de98d-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="de98d-113">Ponieważ `End` kończy działanie aplikacji bez udziału w zasobach, które mogą być otwarte, należy spróbować oczyścić się nieprzerwanie przed użyciem.</span><span class="sxs-lookup"><span data-stu-id="de98d-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="de98d-114">Na przykład jeśli aplikacja ma otwarte jakiekolwiek formularze, należy je zamknąć przed przekroczeniem przez `End` formant.</span><span class="sxs-lookup"><span data-stu-id="de98d-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="de98d-115">Należy używać `End` oszczędnie i tylko wtedy, gdy trzeba natychmiast zatrzymać.</span><span class="sxs-lookup"><span data-stu-id="de98d-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="de98d-116">Normalne metody kończenia procedury (instrukcja[Return](../../../visual-basic/language-reference/statements/return-statement.md) i [Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) nie tylko zamykają procedurę, ale również powodują, że kod wywołujący może czyścić się nieprzerwanie.</span><span class="sxs-lookup"><span data-stu-id="de98d-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="de98d-117">Aplikacja konsolowa, na przykład, może po `Return` prostu `Main` wykonać procedurę.</span><span class="sxs-lookup"><span data-stu-id="de98d-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="de98d-118">`End` Instrukcja<xref:System.Environment.Exit%2A> wywołuje metodę<xref:System.Environment> klasy w<xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="de98d-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="de98d-119"><xref:System.Environment.Exit%2A>`UnmanagedCode` wymaga uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="de98d-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="de98d-120">Jeśli tego nie zrobisz, <xref:System.Security.SecurityException> wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="de98d-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="de98d-121">Po wykonaniu dodatkowego słowa kluczowego [End \<słowo kluczowe > instrukcja](../../../visual-basic/language-reference/statements/end-keyword-statement.md) wyznacza końca definicji odpowiedniej procedury lub bloku.</span><span class="sxs-lookup"><span data-stu-id="de98d-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="de98d-122">Na przykład `End Function` kończy definicję `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="de98d-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de98d-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="de98d-123">Example</span></span>  
 <span data-ttu-id="de98d-124">Poniższy przykład używa instrukcji, `End` aby przerwać wykonywanie kodu, jeśli użytkownik zażąda.</span><span class="sxs-lookup"><span data-stu-id="de98d-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="de98d-125">Uwagi dla deweloperów urządzeń inteligentnych</span><span class="sxs-lookup"><span data-stu-id="de98d-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="de98d-126">Ta instrukcja nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="de98d-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de98d-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de98d-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="de98d-128">Stop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="de98d-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="de98d-129">End \<słowo kluczowe > instrukcji</span><span class="sxs-lookup"><span data-stu-id="de98d-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
