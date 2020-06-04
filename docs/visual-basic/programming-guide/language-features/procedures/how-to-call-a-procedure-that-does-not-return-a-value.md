---
title: 'Porady: wywoływanie procedury, która nie zwraca wartości'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 514d6e576b9b782387840ae04dcefa00de876aa9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388741"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="1c389-102">Porady: wywoływanie procedury, która nie zwraca wartości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c389-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="1c389-103">`Sub`Procedura nie zwraca wartości do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="1c389-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="1c389-104">Należy wywołać ją jawnie z autonomiczną instrukcją wywołującą.</span><span class="sxs-lookup"><span data-stu-id="1c389-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="1c389-105">Nie można go wywołać za pomocą jego nazwy w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="1c389-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="1c389-106">Aby wywołać procedurę sub</span><span class="sxs-lookup"><span data-stu-id="1c389-106">To call a Sub procedure</span></span>  
  
1. <span data-ttu-id="1c389-107">Określ nazwę `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="1c389-107">Specify the name of the `Sub` procedure.</span></span>  
  
2. <span data-ttu-id="1c389-108">Postępuj zgodnie z nazwą procedury z nawiasami, aby ująć listę argumentów.</span><span class="sxs-lookup"><span data-stu-id="1c389-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="1c389-109">Jeśli nie ma żadnych argumentów, możesz opcjonalnie pominąć nawiasy.</span><span class="sxs-lookup"><span data-stu-id="1c389-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="1c389-110">Jednak użycie nawiasów sprawia, że kod można ułatwić odczytywanie.</span><span class="sxs-lookup"><span data-stu-id="1c389-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="1c389-111">Umieść argumenty na liście argumentów w nawiasach rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="1c389-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="1c389-112">Upewnij się, że podasz argumenty w tej samej kolejności, w której `Sub` procedura definiuje odpowiednie parametry.</span><span class="sxs-lookup"><span data-stu-id="1c389-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="1c389-113">Poniższy przykład wywołuje <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> funkcję Visual Basic w celu aktywowania okna aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1c389-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="1c389-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>przyjmuje tytuł okna jako jedyny argument.</span><span class="sxs-lookup"><span data-stu-id="1c389-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="1c389-115">Nie zwraca wartości do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="1c389-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="1c389-116">Jeśli proces Notatnika nie jest uruchomiony, przykład zgłasza <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="1c389-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="1c389-117">W `Shell` procedurze przyjęto założenie, że aplikacje znajdują się w określonych ścieżkach.</span><span class="sxs-lookup"><span data-stu-id="1c389-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="1c389-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c389-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [<span data-ttu-id="1c389-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="1c389-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="1c389-120">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="1c389-120">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="1c389-121">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="1c389-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="1c389-122">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1c389-122">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="1c389-123">Porady: tworzenie procedury</span><span class="sxs-lookup"><span data-stu-id="1c389-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="1c389-124">Instrukcje: wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="1c389-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="1c389-125">Porady: wywoływanie programu do obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c389-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
