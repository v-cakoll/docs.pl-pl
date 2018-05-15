---
title: 'Porady: wywoływanie procedury, która nie zwraca wartości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: cf136f1486645d6e8e4b5856c0b1baf9e99f6c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="8d12c-102">Porady: wywoływanie procedury, która nie zwraca wartości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d12c-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="8d12c-103">A `Sub` procedury nie zwraca wartości do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="8d12c-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="8d12c-104">Należy wywołać ją jawnie autonomicznej instrukcją wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8d12c-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="8d12c-105">Nie można wywołać go, używając po prostu swojej nazwy w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="8d12c-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="8d12c-106">Aby wywołać procedurę Sub</span><span class="sxs-lookup"><span data-stu-id="8d12c-106">To call a Sub procedure</span></span>  
  
1.  <span data-ttu-id="8d12c-107">Określ nazwę `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="8d12c-107">Specify the name of the `Sub` procedure.</span></span>  
  
2.  <span data-ttu-id="8d12c-108">Po nazwie procedury nawiasami ujmij listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="8d12c-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="8d12c-109">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="8d12c-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="8d12c-110">Jednak za pomocą nawiasów ułatwia kodu do odczytu.</span><span class="sxs-lookup"><span data-stu-id="8d12c-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="8d12c-111">Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty.</span><span class="sxs-lookup"><span data-stu-id="8d12c-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="8d12c-112">Należy podać argumenty w tej samej kolejności, która `Sub` procedury definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="8d12c-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="8d12c-113">Poniższy przykład wywołuje Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> funkcji, aby aktywować okna aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8d12c-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="8d12c-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> pobiera tytuł okna jako jedynego argumentu.</span><span class="sxs-lookup"><span data-stu-id="8d12c-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="8d12c-115">Zwraca wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="8d12c-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="8d12c-116">Jeśli nie jest uruchomiony proces Notatnik, zgłasza przykładzie <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="8d12c-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="8d12c-117">`Shell` Procedurze przyjęto założenie, znajdują się w określonej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="8d12c-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8d12c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d12c-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [<span data-ttu-id="8d12c-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="8d12c-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="8d12c-120">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="8d12c-120">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="8d12c-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="8d12c-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="8d12c-122">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8d12c-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="8d12c-123">Instrukcje: tworzenie procedury</span><span class="sxs-lookup"><span data-stu-id="8d12c-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)  
 [<span data-ttu-id="8d12c-124">Instrukcje: wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="8d12c-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="8d12c-125">Porady: wywoływanie procedury obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8d12c-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
