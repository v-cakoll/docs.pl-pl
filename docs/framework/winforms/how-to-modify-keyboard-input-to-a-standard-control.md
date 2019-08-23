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
ms.openlocfilehash: 1aa22501eb3d15b30be4ea4918473cf5a48cfe94
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964290"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a><span data-ttu-id="f3a53-102">Instrukcje: Modyfikowanie sygnału z klawiatury do kontrolki standardowej</span><span class="sxs-lookup"><span data-stu-id="f3a53-102">How to: Modify Keyboard Input to a Standard Control</span></span>
<span data-ttu-id="f3a53-103">Windows Forms zapewnia możliwość użycia i modyfikacji danych wejściowych z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="f3a53-103">Windows Forms provides the ability to consume and modify keyboard input.</span></span> <span data-ttu-id="f3a53-104">Korzystanie z klucza odnosi się do obsługi klucza w metodzie lub obsłudze zdarzeń, tak aby inne metody i zdarzenia w dalszej kolejce kolejki komunikatów nie otrzymywały wartości klucza.</span><span class="sxs-lookup"><span data-stu-id="f3a53-104">Consuming a key refers to handling a key within a method or event handler so that other methods and events further down the message queue do not receive the key value.</span></span> <span data-ttu-id="f3a53-105">Modyfikacja klucza polega na zmodyfikowaniu wartości klucza, aby metody i programy obsługi zdarzeń w dalszej części kolejki komunikatów miały inną wartość klucza.</span><span class="sxs-lookup"><span data-stu-id="f3a53-105">Modifying a key refers to modifying the value of a key so that methods and event handlers further down the message queue receive a different key value.</span></span> <span data-ttu-id="f3a53-106">W tym temacie pokazano, jak wykonać te zadania.</span><span class="sxs-lookup"><span data-stu-id="f3a53-106">This topic shows how to accomplish these tasks.</span></span>  
  
### <a name="to-consume-a-key"></a><span data-ttu-id="f3a53-107">Aby użyć klucza</span><span class="sxs-lookup"><span data-stu-id="f3a53-107">To consume a key</span></span>  
  
- <span data-ttu-id="f3a53-108">W programie obsługi <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> <xref:System.Windows.Forms.KeyPressEventArgs> zdarzeń ustaw właściwość klasy na `true`. <xref:System.Windows.Forms.Control.KeyPress></span><span class="sxs-lookup"><span data-stu-id="f3a53-108">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to `true`.</span></span>  
  
     <span data-ttu-id="f3a53-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="f3a53-109">-or-</span></span>  
  
     <span data-ttu-id="f3a53-110">W programie obsługi <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> <xref:System.Windows.Forms.KeyEventArgs> zdarzeń ustaw właściwość klasy na `true`. <xref:System.Windows.Forms.Control.KeyDown></span><span class="sxs-lookup"><span data-stu-id="f3a53-110">In a <xref:System.Windows.Forms.Control.KeyDown> event handler, set the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> class to `true`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f3a53-111">Ustawienie właściwości w programie<xref:System.Windows.Forms.Control.KeyPress> obsługi <xref:System.Windows.Forms.Control.KeyUp> zdarzeń nie zapobiega wywoływaniu zdarzeń i dla bieżącego naciśnięcia klawisza. <xref:System.Windows.Forms.Control.KeyDown> <xref:System.Windows.Forms.KeyEventArgs.Handled%2A></span><span class="sxs-lookup"><span data-stu-id="f3a53-111">Setting the <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> property in the <xref:System.Windows.Forms.Control.KeyDown> event handler does not prevent the <xref:System.Windows.Forms.Control.KeyPress> and <xref:System.Windows.Forms.Control.KeyUp> events from being raised for the current keystroke.</span></span> <span data-ttu-id="f3a53-112">W tym celu użyj właściwości.<xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A></span><span class="sxs-lookup"><span data-stu-id="f3a53-112">Use the <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> property for this purpose.</span></span>  
  
     <span data-ttu-id="f3a53-113">Poniższy `switch` przykład jest fragmentem instrukcji, która analizuje <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> Właściwość <xref:System.Windows.Forms.KeyPressEventArgs> odebraną przez <xref:System.Windows.Forms.Control.KeyPress> procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f3a53-113">The following example is an excerpt from a `switch` statement that examines the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> received by a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span> <span data-ttu-id="f3a53-114">Ten kod wykorzystuje klucze znaku "A" i "a".</span><span class="sxs-lookup"><span data-stu-id="f3a53-114">This code consumes the 'A' and 'a' character keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a><span data-ttu-id="f3a53-115">Aby zmodyfikować klucz znaku standardowego</span><span class="sxs-lookup"><span data-stu-id="f3a53-115">To modify a standard character key</span></span>  
  
- <span data-ttu-id="f3a53-116">W programie obsługi <xref:System.Windows.Forms.KeyPressEventArgs> <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> <xref:System.Windows.Forms.Control.KeyPress> zdarzeń ustaw właściwość klasy na wartość nowego klucza znaku.</span><span class="sxs-lookup"><span data-stu-id="f3a53-116">In a <xref:System.Windows.Forms.Control.KeyPress> event handler, set the <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> class to the value of the new character key.</span></span>  
  
     <span data-ttu-id="f3a53-117">Poniższy przykład jest fragmentem `switch` instrukcji, która modyfikuje wartość "B" na "a" i "B" na "a".</span><span class="sxs-lookup"><span data-stu-id="f3a53-117">The following example is an excerpt from a `switch` statement that modifies 'B' to 'A' and 'b' to 'a'.</span></span> <span data-ttu-id="f3a53-118">Należy pamiętać, <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> że właściwość <xref:System.Windows.Forms.KeyPressEventArgs> parametru jest ustawiona na `false`, więc nowa wartość klucza jest propagowana do innych metod i zdarzeń w kolejce komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f3a53-118">Note that the <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> property of the <xref:System.Windows.Forms.KeyPressEventArgs> parameter is set to `false`, so that the new key value is propagated to other methods and events in the message queue.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a><span data-ttu-id="f3a53-119">Aby zmodyfikować klucz nieznakowy</span><span class="sxs-lookup"><span data-stu-id="f3a53-119">To modify a noncharacter key</span></span>  
  
- <span data-ttu-id="f3a53-120">Zastąp <xref:System.Windows.Forms.Message.WParam%2A> <xref:System.Windows.Forms.Message> <xref:System.Windows.Forms.Keys> metodę, która przetwarza komunikaty systemu Windows, Wykryj komunikat przetłumaczyła lub WM_SYSKEYDOWN, a następnie ustaw właściwość parametru na wartość reprezentującą nowy klucz nieznakowy. <xref:System.Windows.Forms.Control></span><span class="sxs-lookup"><span data-stu-id="f3a53-120">Override a <xref:System.Windows.Forms.Control> method that processes Windows messages, detect the WM_KEYDOWN or WM_SYSKEYDOWN message, and set the <xref:System.Windows.Forms.Message.WParam%2A> property of the <xref:System.Windows.Forms.Message> parameter to the <xref:System.Windows.Forms.Keys> value that represents the new noncharacter key.</span></span>  
  
     <span data-ttu-id="f3a53-121">Poniższy przykład kodu demonstruje, jak zastąpić metodę kontrolki, <xref:System.Windows.Forms.Control.PreProcessMessage%2A> aby wykryć klucze F1 przez F9 i zmodyfikować dowolny klawisz F3, naciskając klawisz F1.</span><span class="sxs-lookup"><span data-stu-id="f3a53-121">The following code example demonstrates how to override the <xref:System.Windows.Forms.Control.PreProcessMessage%2A> method of a control to detect keys F1 through F9 and modify any F3 key press to F1.</span></span> <span data-ttu-id="f3a53-122">Aby uzyskać więcej informacji <xref:System.Windows.Forms.Control> na temat metod, które można przesłonić w celu przechwycenia komunikatów klawiatury, zobacz [dane wejściowe użytkownika w aplikacji Windows Forms](user-input-in-a-windows-forms-application.md) i [sposób działania wprowadzania z klawiatury](how-keyboard-input-works.md).</span><span class="sxs-lookup"><span data-stu-id="f3a53-122">For more information on <xref:System.Windows.Forms.Control> methods that you can override to intercept keyboard messages, see [User Input in a Windows Forms Application](user-input-in-a-windows-forms-application.md) and [How Keyboard Input Works](how-keyboard-input-works.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="f3a53-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3a53-123">Example</span></span>  
 <span data-ttu-id="f3a53-124">Poniższy przykład kodu jest kompletną aplikacją przykładów kodu w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="f3a53-124">The following code example is the complete application for the code examples in the previous sections.</span></span> <span data-ttu-id="f3a53-125">Aplikacja używa kontrolki niestandardowej pochodnej od <xref:System.Windows.Forms.TextBox> klasy, aby używać i modyfikować dane wejściowe z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="f3a53-125">The application uses a custom control derived from the <xref:System.Windows.Forms.TextBox> class to consume and modify keyboard input.</span></span>  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f3a53-126">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f3a53-126">Compiling the Code</span></span>  
 <span data-ttu-id="f3a53-127">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="f3a53-127">This example requires:</span></span>  
  
- <span data-ttu-id="f3a53-128">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="f3a53-128">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a53-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3a53-129">See also</span></span>

- [<span data-ttu-id="f3a53-130">Wprowadzanie z klawiatury w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3a53-130">Keyboard Input in a Windows Forms Application</span></span>](keyboard-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="f3a53-131">Wprowadzanie przez użytkownika w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f3a53-131">User Input in a Windows Forms Application</span></span>](user-input-in-a-windows-forms-application.md)
- [<span data-ttu-id="f3a53-132">Działanie wprowadzania z klawiatury</span><span class="sxs-lookup"><span data-stu-id="f3a53-132">How Keyboard Input Works</span></span>](how-keyboard-input-works.md)
