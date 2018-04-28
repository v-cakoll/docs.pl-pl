---
title: 'Porady: modyfikowanie sygnału z klawiatury do kontrolki standardowej'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc6d9bd6f1d5e1a7472a538b2a579766cee92c93
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a><span data-ttu-id="fcf40-102">Porady: modyfikowanie sygnału z klawiatury do kontrolki standardowej</span><span class="sxs-lookup"><span data-stu-id="fcf40-102">How to: Modify Keyboard Input to a Standard Control</span></span>
<span data-ttu-id="fcf40-103">Program Windows Forms zapewnia możliwość zużywają i modyfikowanie danych wprowadzonych z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="fcf40-103">Windows Forms provides the ability to consume and modify keyboard input.</span></span> <span data-ttu-id="fcf40-104">Korzystanie z klucza odwołuje się do obsługi klucza wewnątrz obsługi metody lub zdarzenia, dzięki czemu innych metod i zdarzeń dalsze dół kolejki wiadomości nie mają wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="fcf40-104">Consuming a key refers to handling a key within a method or event handler so that other methods and events further down the message queue do not receive the key value.</span></span> <span data-ttu-id="fcf40-105">Modyfikowanie klucza odwołuje się do modyfikowania wartości klucza, aby metody i obsługi zdarzeń dalsze dół kolejki wiadomości odbierać różne wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="fcf40-105">Modifying a key refers to modifying the value of a key so that methods and event handlers further down the message queue receive a different key value.</span></span> <span data-ttu-id="fcf40-106">W tym temacie przedstawiono sposób wykonywania tych zadań.</span><span class="sxs-lookup"><span data-stu-id="fcf40-106">This topic shows how to accomplish these tasks.</span></span>  
  
### <a name="to-consume-a-key"></a><span data-ttu-id="fcf40-107">Użycie klucza</span><span class="sxs-lookup"><span data-stu-id="fcf40-107">To consume a key</span></span>  
  
-   <span data-ttu-id="fcf40-108">W <xref:System.Windows.Forms.Control.KeyPress> ustawiony program obsługi zdarzeń, <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> klasy do `true`.</span><span class="sxs-lookup"><span data-stu-id="fcf40-108">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to `true`.</span></span>  
  
     <span data-ttu-id="fcf40-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="fcf40-109">-or-</span></span>  
  
     <span data-ttu-id="fcf40-110">W <xref:System.Windows.Forms.Control.KeyDown> ustawiony program obsługi zdarzeń, <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.KeyEventArgs> klasy do `true`.</span><span class="sxs-lookup"><span data-stu-id="fcf40-110">In a <xref:System.Windows.Forms.Control.KeyDown> event handler, set the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> class to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fcf40-111">Ustawienie <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> właściwości w <xref:System.Windows.Forms.Control.KeyDown> program obsługi zdarzeń nie zapobiega <xref:System.Windows.Forms.Control.KeyPress> i <xref:System.Windows.Forms.Control.KeyUp> zdarzenia z są zgłaszane dla bieżącego naciśnięcie klawisza.</span><span class="sxs-lookup"><span data-stu-id="fcf40-111">Setting the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property in the <xref:System.Windows.Forms.Control.KeyDown> event handler does not prevent the <xref:System.Windows.Forms.Control.KeyPress> and <xref:System.Windows.Forms.Control.KeyUp> events from being raised for the current keystroke.</span></span> <span data-ttu-id="fcf40-112">Użyj <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> właściwości w tym celu.</span><span class="sxs-lookup"><span data-stu-id="fcf40-112">Use the <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> property for this purpose.</span></span>  
  
     <span data-ttu-id="fcf40-113">Poniższy przykład zawiera fragment `switch` instrukcji, która sprawdza <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> odebranych przez <xref:System.Windows.Forms.Control.KeyPress> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcf40-113">The following example is an excerpt from a `switch` statement that examines the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> received by a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span> <span data-ttu-id="fcf40-114">Ten kod zużywa "A" i "" klawiszy znaków.</span><span class="sxs-lookup"><span data-stu-id="fcf40-114">This code consumes the 'A' and 'a' character keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a><span data-ttu-id="fcf40-115">Aby zmodyfikować klucz znaków</span><span class="sxs-lookup"><span data-stu-id="fcf40-115">To modify a standard character key</span></span>  
  
-   <span data-ttu-id="fcf40-116">W <xref:System.Windows.Forms.Control.KeyPress> ustawiony program obsługi zdarzeń, <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> klasy wartości nowy klucz znaków.</span><span class="sxs-lookup"><span data-stu-id="fcf40-116">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to the value of the new character key.</span></span>  
  
     <span data-ttu-id="fcf40-117">Poniższy przykład zawiera fragment `switch` instrukcji, która modyfikuje "B" na "A" i "b", "a".</span><span class="sxs-lookup"><span data-stu-id="fcf40-117">The following example is an excerpt from a `switch` statement that modifies 'B' to 'A' and 'b' to 'a'.</span></span> <span data-ttu-id="fcf40-118">Należy pamiętać, że <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> właściwość <xref:System.Windows.Forms.KeyPressEventArgs> ustawiono parametr `false`, dzięki czemu nowe wartości klucza są propagowane do innych metod i zdarzeń w kolejce wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fcf40-118">Note that the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> parameter is set to `false`, so that the new key value is propagated to other methods and events in the message queue.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a><span data-ttu-id="fcf40-119">Aby zmodyfikować klucz nieznakowe</span><span class="sxs-lookup"><span data-stu-id="fcf40-119">To modify a noncharacter key</span></span>  
  
-   <span data-ttu-id="fcf40-120">Zastąpienie <xref:System.Windows.Forms.Control> metody, która przetwarza komunikatów systemu Windows, wykrywanie komunikat WM_KEYDOWN lub WM_SYSKEYDOWN i ustawić <xref:System.Windows.Forms.Message.WParam%2A> właściwość <xref:System.Windows.Forms.Message> parametr <xref:System.Windows.Forms.Keys> wartość, która reprezentuje nieznakowe nowego klucza.</span><span class="sxs-lookup"><span data-stu-id="fcf40-120">Override a <xref:System.Windows.Forms.Control> method that processes Windows messages, detect the WM_KEYDOWN or WM_SYSKEYDOWN message, and set the <xref:System.Windows.Forms.Message.WParam%2A> property of the <xref:System.Windows.Forms.Message> parameter to the <xref:System.Windows.Forms.Keys> value that represents the new noncharacter key.</span></span>  
  
     <span data-ttu-id="fcf40-121">W poniższym przykładzie pokazano, jak zastąpić <xref:System.Windows.Forms.Control.PreProcessMessage%2A> metody kontroli wykrywania klucze F1 za pomocą F9 i zmodyfikować wszystkie naciśnięcie klawisza F3, aby F1.</span><span class="sxs-lookup"><span data-stu-id="fcf40-121">The following code example demonstrates how to override the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method of a control to detect keys F1 through F9 and modify any F3 key press to F1.</span></span> <span data-ttu-id="fcf40-122">Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.Control> metody, które można zastąpić, aby przechwycić komunikaty klawiatury, zobacz [dane wejściowe użytkownika w aplikacji Windows Forms](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) i [sposób działania wejście klawiatury](../../../docs/framework/winforms/how-keyboard-input-works.md).</span><span class="sxs-lookup"><span data-stu-id="fcf40-122">For more information on <xref:System.Windows.Forms.Control> methods that you can override to intercept keyboard messages, see [User Input in a Windows Forms Application](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) and [How Keyboard Input Works](../../../docs/framework/winforms/how-keyboard-input-works.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="fcf40-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="fcf40-123">Example</span></span>  
 <span data-ttu-id="fcf40-124">Poniższy przykładowy kod jest kompletna aplikacja przykłady kodu w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="fcf40-124">The following code example is the complete application for the code examples in the previous sections.</span></span> <span data-ttu-id="fcf40-125">Aplikacja używa kontrolki niestandardowej pochodną <xref:System.Windows.Forms.TextBox> klasy do wykorzystania i modyfikowanie danych wprowadzonych z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="fcf40-125">The application uses a custom control derived from the <xref:System.Windows.Forms.TextBox> class to consume and modify keyboard input.</span></span>  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fcf40-126">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fcf40-126">Compiling the Code</span></span>  
 <span data-ttu-id="fcf40-127">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="fcf40-127">This example requires:</span></span>  
  
-   <span data-ttu-id="fcf40-128">Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="fcf40-128">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="fcf40-129">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fcf40-129">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="fcf40-130">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="fcf40-130">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="fcf40-131">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="fcf40-131">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf40-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcf40-132">See Also</span></span>  
 [<span data-ttu-id="fcf40-133">Wprowadzanie z klawiatury w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcf40-133">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="fcf40-134">Wprowadzanie przez użytkownika w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcf40-134">User Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="fcf40-135">Działanie wprowadzania z klawiatury</span><span class="sxs-lookup"><span data-stu-id="fcf40-135">How Keyboard Input Works</span></span>](../../../docs/framework/winforms/how-keyboard-input-works.md)
