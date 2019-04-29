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
ms.openlocfilehash: 4fc4fd36fb6b057195e9d8a79eb0a5b3ac9ff95c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638145"
---
# <a name="end-statement"></a><span data-ttu-id="2a7c4-102">End — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a7c4-102">End Statement</span></span>
<span data-ttu-id="2a7c4-103">Kończy wykonywanie natychmiast.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a7c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a7c4-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="2a7c4-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a7c4-105">Remarks</span></span>  
 <span data-ttu-id="2a7c4-106">Możesz umieścić `End` instrukcji procedury, aby wymusić całej aplikacji, aby zatrzymać w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="2a7c4-107">`End` Zamyka wszystkie pliki otwarte z `Open` instrukcji i czyści zmienne wszystkich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="2a7c4-108">Aplikacja zostanie zamknięta, nie są żadne inne programy, zawierający odwołania do obiektów, a nie działa żadna jego kodu.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a7c4-109">`End` Instrukcji zatrzymuje wykonywanie kodu nagle i nie wywołuje `Dispose` lub `Finalize` metody i wszelki inny kod języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="2a7c4-110">Odwołania do obiektów przechowywanych przez inne programy nie są unieważniane.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="2a7c4-111">Jeśli `End` instrukcji występuje w ciągu `Try` lub `Catch` bloku, formant nie przekaże do odpowiednich `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="2a7c4-112">Instrukcja `Stop` wstrzymuje wykonywanie, ale w przeciwieństwie do `End` nie zamyka żadnych plików ani nie czyści żadnych zmiennych — chyba że występuje w skompilowanym pliku wykonywalnym (.exe).</span><span class="sxs-lookup"><span data-stu-id="2a7c4-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="2a7c4-113">Ponieważ `End` kończy działanie aplikacji bez uczestniczenia do żadnych zasobów, które mogą być otwarte, należy starać się wstrzymuje prawidłowo, przed jego użyciem.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="2a7c4-114">Na przykład, jeśli aplikacja ma wszystkie formularze, Otwórz, należy zamknąć je przed kontrola osiąga `End` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="2a7c4-115">Należy używać `End` oszczędnie i tylko wtedy kiedy należy zatrzymać natychmiast.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="2a7c4-116">Normalne sposobów, aby zakończyć procedurę ([instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md) i [instrukcji zakończenia](../../../visual-basic/language-reference/statements/exit-statement.md)) nie tylko zamknięcia w procedurze nie pozostawia żadnych śladów, ale również przyznać kod wywołujący możliwość wstrzymuje nie pozostawia żadnych śladów.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="2a7c4-117">Aplikację konsolową w języku, na przykład, można po prostu `Return` z `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2a7c4-118">`End` Instrukcja wywołuje <xref:System.Environment.Exit%2A> metody <xref:System.Environment> klasy w <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="2a7c4-119"><xref:System.Environment.Exit%2A> Musisz mieć `UnmanagedCode` uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="2a7c4-120">W takim przypadku, <xref:System.Security.SecurityException> wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="2a7c4-121">Gdy następuje dodatkowego kluczowego [zakończenia \<— słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md) wyznacza koniec definicji odpowiednią procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="2a7c4-122">Na przykład `End Function` kończy definicję `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a7c4-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a7c4-123">Example</span></span>  
 <span data-ttu-id="2a7c4-124">W poniższym przykładzie użyto `End` instrukcję, aby zakończyć wykonywanie kodu, jeśli użytkownik żąda ona.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="2a7c4-125">Uwagi dla deweloperów urządzeń inteligentnych</span><span class="sxs-lookup"><span data-stu-id="2a7c4-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="2a7c4-126">Ta instrukcja nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="2a7c4-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a7c4-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a7c4-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="2a7c4-128">Stop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a7c4-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="2a7c4-129">Koniec \<— słowo kluczowe > — instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a7c4-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
