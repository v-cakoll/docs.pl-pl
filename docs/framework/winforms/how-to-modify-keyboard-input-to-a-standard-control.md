---
title: 'Instrukcje: Modyfikowanie sygnału z klawiatury do kontrolki standardowej'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: 81d33234670fb8ae5445cc86a79f5c3b6a647a03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225784"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a><span data-ttu-id="13f0b-102">Instrukcje: Modyfikowanie sygnału z klawiatury do kontrolki standardowej</span><span class="sxs-lookup"><span data-stu-id="13f0b-102">How to: Modify Keyboard Input to a Standard Control</span></span>
<span data-ttu-id="13f0b-103">Windows Forms zapewnia możliwość korzystania i modyfikowanie danych wprowadzonych z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="13f0b-103">Windows Forms provides the ability to consume and modify keyboard input.</span></span> <span data-ttu-id="13f0b-104">Korzystanie z klucza odwołuje się do obsługi klucza w ramach metody lub procedury obsługi zdarzeń, tak, aby inne metody i zdarzenia dalszych szczegółów kolejka komunikatów nie mają wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="13f0b-104">Consuming a key refers to handling a key within a method or event handler so that other methods and events further down the message queue do not receive the key value.</span></span> <span data-ttu-id="13f0b-105">Zmodyfikowanie klucza odwołuje się do modyfikowania wartości klucza, tak aby metody i procedury obsługi zdarzeń dalszych szczegółów kolejki komunikatów odbierać różne wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="13f0b-105">Modifying a key refers to modifying the value of a key so that methods and event handlers further down the message queue receive a different key value.</span></span> <span data-ttu-id="13f0b-106">W tym temacie przedstawiono sposób wykonywania tych zadań.</span><span class="sxs-lookup"><span data-stu-id="13f0b-106">This topic shows how to accomplish these tasks.</span></span>  
  
### <a name="to-consume-a-key"></a><span data-ttu-id="13f0b-107">Korzystanie z klucza</span><span class="sxs-lookup"><span data-stu-id="13f0b-107">To consume a key</span></span>  
  
-   <span data-ttu-id="13f0b-108">W <xref:System.Windows.Forms.Control.KeyPress> ustawić programu obsługi zdarzeń <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> klasy `true`.</span><span class="sxs-lookup"><span data-stu-id="13f0b-108">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to `true`.</span></span>  
  
     <span data-ttu-id="13f0b-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="13f0b-109">-or-</span></span>  
  
     <span data-ttu-id="13f0b-110">W <xref:System.Windows.Forms.Control.KeyDown> ustawić programu obsługi zdarzeń <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.KeyEventArgs> klasy `true`.</span><span class="sxs-lookup"><span data-stu-id="13f0b-110">In a <xref:System.Windows.Forms.Control.KeyDown> event handler, set the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> class to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13f0b-111">Ustawienie <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.Control.KeyDown> program obsługi zdarzeń nie uniemożliwia <xref:System.Windows.Forms.Control.KeyPress> i <xref:System.Windows.Forms.Control.KeyUp> zdarzenia są zgłaszane dla bieżącego naciśnięcia klawisza.</span><span class="sxs-lookup"><span data-stu-id="13f0b-111">Setting the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property in the <xref:System.Windows.Forms.Control.KeyDown> event handler does not prevent the <xref:System.Windows.Forms.Control.KeyPress> and <xref:System.Windows.Forms.Control.KeyUp> events from being raised for the current keystroke.</span></span> <span data-ttu-id="13f0b-112">Użyj <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> właściwości w tym celu.</span><span class="sxs-lookup"><span data-stu-id="13f0b-112">Use the <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> property for this purpose.</span></span>  
  
     <span data-ttu-id="13f0b-113">Poniższy przykład to fragment `switch` instrukcję, która sprawdza, czy <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> odebranych przez <xref:System.Windows.Forms.Control.KeyPress> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="13f0b-113">The following example is an excerpt from a `switch` statement that examines the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> received by a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span> <span data-ttu-id="13f0b-114">Ten kod wykorzystuje "A" i "" klawiszy znaków.</span><span class="sxs-lookup"><span data-stu-id="13f0b-114">This code consumes the 'A' and 'a' character keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a><span data-ttu-id="13f0b-115">Aby zmodyfikować klucz znaków standardowych</span><span class="sxs-lookup"><span data-stu-id="13f0b-115">To modify a standard character key</span></span>  
  
-   <span data-ttu-id="13f0b-116">W <xref:System.Windows.Forms.Control.KeyPress> ustawić programu obsługi zdarzeń <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> klasy wartość nowy klucz znaków.</span><span class="sxs-lookup"><span data-stu-id="13f0b-116">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to the value of the new character key.</span></span>  
  
     <span data-ttu-id="13f0b-117">Poniższy przykład to fragment `switch` instrukcji, która modyfikuje "B", "A" i "b", "a".</span><span class="sxs-lookup"><span data-stu-id="13f0b-117">The following example is an excerpt from a `switch` statement that modifies 'B' to 'A' and 'b' to 'a'.</span></span> <span data-ttu-id="13f0b-118">Należy pamiętać, że <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> parametr ma wartość `false`, dzięki czemu nowe wartości klucza są propagowane do innych metod i zdarzeń w kolejce komunikatów.</span><span class="sxs-lookup"><span data-stu-id="13f0b-118">Note that the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> parameter is set to `false`, so that the new key value is propagated to other methods and events in the message queue.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a><span data-ttu-id="13f0b-119">Aby zmodyfikować nieznakowe klucz</span><span class="sxs-lookup"><span data-stu-id="13f0b-119">To modify a noncharacter key</span></span>  
  
-   <span data-ttu-id="13f0b-120">Zastąpienie <xref:System.Windows.Forms.Control> metody, która przetwarza wiadomości Windows wykrywanie przetłumaczyła lub WM_SYSKEYDOWN wiadomości i ustawić <xref:System.Windows.Forms.Message.WParam%2A> właściwość <xref:System.Windows.Forms.Message> parametr <xref:System.Windows.Forms.Keys> wartość, która reprezentuje nowy klucz nieznakowe.</span><span class="sxs-lookup"><span data-stu-id="13f0b-120">Override a <xref:System.Windows.Forms.Control> method that processes Windows messages, detect the WM_KEYDOWN or WM_SYSKEYDOWN message, and set the <xref:System.Windows.Forms.Message.WParam%2A> property of the <xref:System.Windows.Forms.Message> parameter to the <xref:System.Windows.Forms.Keys> value that represents the new noncharacter key.</span></span>  
  
     <span data-ttu-id="13f0b-121">Poniższy przykład kodu demonstruje sposób zastąpienia <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metodę formantu do wykrywania klucze F1, za pomocą F9 i zmodyfikować wszelkie F3 naciśnięcie klawisza F1 — do.</span><span class="sxs-lookup"><span data-stu-id="13f0b-121">The following code example demonstrates how to override the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method of a control to detect keys F1 through F9 and modify any F3 key press to F1.</span></span> <span data-ttu-id="13f0b-122">Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.Control> metod, które można przesłonić, aby przechwycić komunikaty klawiatury, zobacz [dane wejściowe użytkownika w aplikacji Windows Forms](user-input-in-a-windows-forms-application.md) i [sposób działania wejście klawiatury](how-keyboard-input-works.md).</span><span class="sxs-lookup"><span data-stu-id="13f0b-122">For more information on <xref:System.Windows.Forms.Control> methods that you can override to intercept keyboard messages, see [User Input in a Windows Forms Application](user-input-in-a-windows-forms-application.md) and [How Keyboard Input Works](how-keyboard-input-works.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="13f0b-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="13f0b-123">Example</span></span>  
 <span data-ttu-id="13f0b-124">Poniższy przykład kodu jest kompletnej aplikacji, aby uzyskać przykłady kodu w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="13f0b-124">The following code example is the complete application for the code examples in the previous sections.</span></span> <span data-ttu-id="13f0b-125">Aplikacja korzysta z kontrolki niestandardowej, która jest pochodną <xref:System.Windows.Forms.TextBox> klasy w celu umożliwienia użycia i modyfikowanie danych wprowadzonych z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="13f0b-125">The application uses a custom control derived from the <xref:System.Windows.Forms.TextBox> class to consume and modify keyboard input.</span></span>  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="13f0b-126">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="13f0b-126">Compiling the Code</span></span>  
 <span data-ttu-id="13f0b-127">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="13f0b-127">This example requires:</span></span>  
  
-   <span data-ttu-id="13f0b-128">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="13f0b-128">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="13f0b-129">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="13f0b-129">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="13f0b-130">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="13f0b-130">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f0b-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13f0b-131">See also</span></span>

- [<span data-ttu-id="13f0b-132">Wprowadzanie z klawiatury w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13f0b-132">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="13f0b-133">Wprowadzanie przez użytkownika w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13f0b-133">User Input in a Windows Forms Application</span></span>](user-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="13f0b-134">Działanie wprowadzania z klawiatury</span><span class="sxs-lookup"><span data-stu-id="13f0b-134">How Keyboard Input Works</span></span>](how-keyboard-input-works.md)
