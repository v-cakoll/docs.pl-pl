---
title: End — Instrukcja
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
ms.openlocfilehash: 864ac5ef1713f8ffa93c18accede8ecd5b3b7a8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604435"
---
# <a name="end-statement"></a><span data-ttu-id="bc0b5-102">End — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="bc0b5-102">End Statement</span></span>
<span data-ttu-id="bc0b5-103">Kończy wykonywanie natychmiast.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc0b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc0b5-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="bc0b5-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc0b5-105">Remarks</span></span>  
 <span data-ttu-id="bc0b5-106">Możesz umieścić `End` instrukcji w dowolnym miejscu procedury, aby wymusić cała aplikacja przestanie działać.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="bc0b5-107">`End` Zamyka wszystkie pliki otwarte z `Open` instrukcji i czyści zmienne wszystkich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="bc0b5-108">Aplikacja zamyka nie ma żadnych innych programów zawierający odniesienia do swoich obiektów, a nie działa żadna jego kod.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc0b5-109">`End` Instrukcji nagle zatrzymuje wykonywanie kodu i nie jest wywoływany `Dispose` lub `Finalize` metody lub inny kod Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="bc0b5-110">Odwołania do obiektów przechowywanych przez inne programy są unieważniona.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="bc0b5-111">Jeśli `End` napotkano w instrukcji `Try` lub `Catch` bloku, formantu nie przekazuje do odpowiadającego `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="bc0b5-112">`Stop` Instrukcji wstrzymuje wykonywanie, lecz w przeciwieństwie do `End`, zamknij wszystkie pliki lub nie wyczyść wszystkie zmienne, chyba że jest wystąpił w pliku skompilowanego pliku wykonywalnego (.exe).</span><span class="sxs-lookup"><span data-stu-id="bc0b5-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="bc0b5-113">Ponieważ `End` kończy aplikacji bez uczestnictwa do żadnych zasobów, które mogą być otwarte, należy spróbować wstrzymuje prawidłowo, przed jego użyciem.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="bc0b5-114">Na przykład jeśli aplikacja ma Otwórz formularzy, należy zamknąć je przed osiągnie kontroli `End` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="bc0b5-115">Należy używać `End` oszczędnie i tylko kiedy należy zatrzymać natychmiast.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="bc0b5-116">Normalne sposoby zakończyć procedurę ([zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md) i [instrukcji Zakończ](../../../visual-basic/language-reference/statements/exit-statement.md)) nie tylko prawidłowo zamknięcia procedurą, ale również dawać kod wywołujący możliwość wstrzymuje prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="bc0b5-117">Aplikacji konsoli, na przykład można po prostu `Return` z `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc0b5-118">`End` Wywołania instrukcji <xref:System.Environment.Exit%2A> metody <xref:System.Environment> klasy w <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="bc0b5-119"><xref:System.Environment.Exit%2A> Musisz mieć `UnmanagedCode` uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="bc0b5-120">Jeśli nie, <xref:System.Security.SecurityException> wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="bc0b5-121">Gdy następuje dodatkowe — słowo kluczowe [zakończenia \<— słowo kluczowe > instrukcji](../../../visual-basic/language-reference/statements/end-keyword-statement.md) wyznacza koniec definicji odpowiednią procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="bc0b5-122">Na przykład `End Function` kończy definicję `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc0b5-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc0b5-123">Example</span></span>  
 <span data-ttu-id="bc0b5-124">W poniższym przykładzie użyto `End` instrukcji, aby zakończyć wykonywanie kodu, jeśli użytkownik zażąda tego.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="bc0b5-125">Uwagi dla deweloperów inteligentnych urządzeń</span><span class="sxs-lookup"><span data-stu-id="bc0b5-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="bc0b5-126">Ta instrukcja nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="bc0b5-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0b5-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc0b5-127">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [<span data-ttu-id="bc0b5-128">Stop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="bc0b5-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [<span data-ttu-id="bc0b5-129">Końcowy \<— słowo kluczowe > — instrukcja</span><span class="sxs-lookup"><span data-stu-id="bc0b5-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
