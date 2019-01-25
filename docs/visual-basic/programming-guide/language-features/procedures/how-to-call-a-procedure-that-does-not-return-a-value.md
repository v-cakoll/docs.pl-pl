---
title: 'Instrukcje: Wywoływanie procedury, która nie zwraca wartości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: f85c7a7edf4d05dc50166ad4f30080c2e595cf65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590646"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="05362-102">Instrukcje: Wywoływanie procedury, która nie zwraca wartości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05362-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="05362-103">A `Sub` procedury nie zwraca wartości do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="05362-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="05362-104">Możesz wywołać ją jawnie za pomocą autonomicznego instrukcji wywołujące.</span><span class="sxs-lookup"><span data-stu-id="05362-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="05362-105">Nie można jej wywołać przy użyciu jego nazwy w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="05362-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="05362-106">Aby wywołać procedurę Sub</span><span class="sxs-lookup"><span data-stu-id="05362-106">To call a Sub procedure</span></span>  
  
1.  <span data-ttu-id="05362-107">Określ nazwę `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="05362-107">Specify the name of the `Sub` procedure.</span></span>  
  
2.  <span data-ttu-id="05362-108">Postępuj zgodnie z nazwą procedury należy umieścić na liście argumentów za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="05362-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="05362-109">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="05362-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="05362-110">Jednak przy użyciu nawiasów sprawia, że Twój kod łatwiejsza do odczytania.</span><span class="sxs-lookup"><span data-stu-id="05362-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="05362-111">Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="05362-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="05362-112">Należy podać argumenty w tej samej kolejności, `Sub` procedura określa odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="05362-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="05362-113">Poniższy przykład wywołuje Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> funkcję, aby aktywować okna aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05362-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="05362-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> pobiera tytuł okna jako jedyny argument.</span><span class="sxs-lookup"><span data-stu-id="05362-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="05362-115">Nie zwraca wartości do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="05362-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="05362-116">Jeśli nie jest uruchomiony proces Notatnik, przykład generuje <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="05362-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="05362-117">`Shell` Procedurze przyjęto założenie, znajdują się w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="05362-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="05362-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05362-118">See also</span></span>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [<span data-ttu-id="05362-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="05362-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="05362-120">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="05362-120">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="05362-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="05362-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="05362-122">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="05362-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="05362-123">Instrukcje: Tworzenie procedury</span><span class="sxs-lookup"><span data-stu-id="05362-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="05362-124">Instrukcje: Wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="05362-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="05362-125">Instrukcje: Wywoływanie programu do obsługi zdarzeń w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05362-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
