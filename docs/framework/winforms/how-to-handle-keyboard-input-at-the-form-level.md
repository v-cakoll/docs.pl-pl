---
title: 'Instrukcje: Obsługa wprowadzania z klawiatury na poziomie formularza'
description: Dowiedz się, jak obsłużyć dane wejściowe z klawiatury dla Windows Forms na poziomie formularza, zanim komunikaty docierają do kontrolki.
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
ms.openlocfilehash: 6f0695b6f665a613e0e4e001a4f9bbfc09dd45ed
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904159"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a><span data-ttu-id="08482-103">Instrukcje: Obsługa wprowadzania z klawiatury na poziomie formularza</span><span class="sxs-lookup"><span data-stu-id="08482-103">How to: Handle Keyboard Input at the Form Level</span></span>
<span data-ttu-id="08482-104">Windows Forms zapewnia możliwość obsługi komunikatów klawiatury na poziomie formularza, zanim komunikaty docierają do formantu.</span><span class="sxs-lookup"><span data-stu-id="08482-104">Windows Forms provides the ability to handle keyboard messages at the form level, before the messages reach a control.</span></span> <span data-ttu-id="08482-105">W tym temacie pokazano, jak wykonać to zadanie.</span><span class="sxs-lookup"><span data-stu-id="08482-105">This topic shows how to accomplish this task.</span></span>  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a><span data-ttu-id="08482-106">Aby obsłużyć komunikat klawiatury na poziomie formularza</span><span class="sxs-lookup"><span data-stu-id="08482-106">To handle a keyboard message at the form level</span></span>  
  
- <span data-ttu-id="08482-107">Obsłuż <xref:System.Windows.Forms.Control.KeyPress> <xref:System.Windows.Forms.Control.KeyDown> zdarzenie lub formularz uruchamiania, a następnie ustaw <xref:System.Windows.Forms.Form.KeyPreview%2A> Właściwość formularza na tak, aby `true` komunikaty klawiatury były odbierane przez formularz przed osiągnięciem jakichkolwiek kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="08482-107">Handle the <xref:System.Windows.Forms.Control.KeyPress> or <xref:System.Windows.Forms.Control.KeyDown> event of the startup form, and set the <xref:System.Windows.Forms.Form.KeyPreview%2A> property of the form to `true` so that keyboard messages are received by the form before they reach any controls on the form.</span></span> <span data-ttu-id="08482-108">Poniższy przykład kodu obsługuje <xref:System.Windows.Forms.Control.KeyPress> zdarzenie przez wykrycie wszystkich kluczy liczbowych i zużywanie "1", "4" i "7".</span><span class="sxs-lookup"><span data-stu-id="08482-108">The following code example handles the <xref:System.Windows.Forms.Control.KeyPress> event by detecting all of the number keys and consuming '1', '4', and '7'.</span></span>  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="08482-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="08482-109">Example</span></span>  
 <span data-ttu-id="08482-110">Poniższy przykład kodu to cała aplikacja dla powyższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="08482-110">The following code example is the entire application for the above example.</span></span> <span data-ttu-id="08482-111">Aplikacja zawiera a <xref:System.Windows.Forms.TextBox> wraz z kilkoma innymi kontrolkami, które umożliwiają przeniesienie fokusu z <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="08482-111">The application includes a <xref:System.Windows.Forms.TextBox> along with several other controls that allow you to move focus from the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="08482-112">W <xref:System.Windows.Forms.Control.KeyPress> przypadku użycia wartości " <xref:System.Windows.Forms.Form> 1", "4" i "7" oraz <xref:System.Windows.Forms.Control.KeyPress> zdarzenia <xref:System.Windows.Forms.TextBox> "2", "5" i "8" podczas wyświetlania pozostałych kluczy.</span><span class="sxs-lookup"><span data-stu-id="08482-112">The <xref:System.Windows.Forms.Control.KeyPress> event of the main <xref:System.Windows.Forms.Form> consumes '1', '4', and '7', and the <xref:System.Windows.Forms.Control.KeyPress> event of the <xref:System.Windows.Forms.TextBox> consumes '2', '5', and '8' while displaying the remaining keys.</span></span> <span data-ttu-id="08482-113">Porównaj <xref:System.Windows.Forms.MessageBox> dane wyjściowe po naciśnięciu klawisza liczbowego, gdy <xref:System.Windows.Forms.TextBox> ma fokus z <xref:System.Windows.Forms.MessageBox> danymi wyjściowymi po naciśnięciu klawisza liczbowego, gdy fokus jest ustawiony na jednej z innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="08482-113">Compare the <xref:System.Windows.Forms.MessageBox> output when you press a number key while the <xref:System.Windows.Forms.TextBox> has focus with the <xref:System.Windows.Forms.MessageBox> output when you press a number key while focus is on one of the other controls.</span></span>  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="08482-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="08482-114">Compiling the Code</span></span>  
 <span data-ttu-id="08482-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="08482-115">This example requires:</span></span>  
  
- <span data-ttu-id="08482-116">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="08482-116">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08482-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08482-117">See also</span></span>

- [<span data-ttu-id="08482-118">Wprowadzanie z klawiatury w aplikacjach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="08482-118">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
