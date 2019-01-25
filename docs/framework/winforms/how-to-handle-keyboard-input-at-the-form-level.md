---
title: 'Instrukcje: Obsługa wprowadzania z klawiatury na poziomie formularza'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: ba17788933cb87215dc66d248357b3333ec04838
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573375"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="0841d-102">Instrukcje: Obsługa wprowadzania z klawiatury na poziomie formularza</span><span class="sxs-lookup"><span data-stu-id="0841d-102">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="0841d-103">Windows Forms zapewnia możliwość obsłużyć komunikaty klawiatury na poziomie formularza, zanim komunikaty do formantu.</span><span class="sxs-lookup"><span data-stu-id="0841d-103">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="0841d-104">W tym temacie przedstawiono sposób wykonania tego zadania.</span><span class="sxs-lookup"><span data-stu-id="0841d-104">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="0841d-105">Do obsługi komunikatu z klawiatury na poziomie formularza</span><span class="sxs-lookup"><span data-stu-id="0841d-105">To handle a keyboard message at the form level</span></span>  
  
-   <span data-ttu-id="0841d-106">Obsługa <xref:System.Windows.Forms.Control.KeyPress> lub <xref:System.Windows.Forms.Control.KeyDown> zdarzenia, formularz początkowy i zestaw <xref:System.Windows.Forms.Form.KeyPreview%2A> właściwości formularza w celu `true` tak, aby komunikaty klawiatury są odbierane przez formularz, zanim osiągną one wszystkie formanty w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0841d-106">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="0841d-107">Poniższy kod obsługuje przykład <xref:System.Windows.Forms.Control.KeyPress> zdarzeń, wykrywając, wszystkie klawisze numeryczne i wykorzystywanie '1', '4' i '7'.</span><span class="sxs-lookup"><span data-stu-id="0841d-107">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="0841d-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0841d-108">Example</span></span>  
 <span data-ttu-id="0841d-109">Poniższy przykład kodu jest całej aplikacji, na przykład powyżej.</span><span class="sxs-lookup"><span data-stu-id="0841d-109">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="0841d-110">Aplikacja zawiera <xref:System.Windows.Forms.TextBox> wraz z innych kontrolek, które pozwalają przenieść fokus z <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="0841d-110">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="0841d-111"><xref:System.Windows.Forms.Control.KeyPress> Zdarzeń głównego <xref:System.Windows.Forms.Form> zużywa '1', '4' i '7' i <xref:System.Windows.Forms.Control.KeyPress> zdarzenia <xref:System.Windows.Forms.TextBox> zużywa "2", "5" i "8" podczas wyświetlania pozostałe klucze.</span><span class="sxs-lookup"><span data-stu-id="0841d-111">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="0841d-112">Porównaj <xref:System.Windows.Forms.MessageBox> dane wyjściowe po naciśnięciu klawisza chwilę liczba kluczy <xref:System.Windows.Forms.TextBox> ma fokus z <xref:System.Windows.Forms.MessageBox> dane wyjściowe, gdy ponownie naciśniesz klawisz liczby podczas, gdy fokus jest ustawiony na jedną z innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="0841d-112">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0841d-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0841d-113">Compiling the Code</span></span>  
 <span data-ttu-id="0841d-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="0841d-114">This example requires:</span></span>  
  
-   <span data-ttu-id="0841d-115">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="0841d-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0841d-116">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0841d-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0841d-117">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="0841d-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="0841d-118">Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="0841d-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0841d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0841d-119">See also</span></span>
- [<span data-ttu-id="0841d-120">Wprowadzanie z klawiatury w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0841d-120">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
