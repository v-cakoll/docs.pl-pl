---
title: 'Instrukcje: Obsługa zdarzenia wejściowe użytkownika w kontrolkach formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: 886558eb33ffbbec65917f15f4da16673518dce9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723962"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="b8790-102">Instrukcje: Obsługa zdarzenia wejściowe użytkownika w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8790-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="b8790-103">W tym przykładzie pokazano, jak obsługiwać większość klawiatury, myszy, fokus i zdarzenia sprawdzania poprawności, które mogą wystąpić w kontrolce Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b8790-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="b8790-104">Pole tekstowe o nazwie `TextBoxInput` odbiera zdarzenia, gdy ma ona fokus, a informacje dotyczące każdego zdarzenia są zapisywane w polu tekstowym o nazwie `TextBoxOutput` w kolejności, w której zdarzenia są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="b8790-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="b8790-105">Aplikacja zawiera także zestaw pól wyboru, które mogą służyć do filtrowania zdarzeń do raportu.</span><span class="sxs-lookup"><span data-stu-id="b8790-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8790-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8790-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b8790-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b8790-107">Compiling the Code</span></span>  
 <span data-ttu-id="b8790-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b8790-108">This example requires:</span></span>  
  
-   <span data-ttu-id="b8790-109">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="b8790-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b8790-110">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b8790-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b8790-111">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="b8790-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8790-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8790-112">See also</span></span>
- [<span data-ttu-id="b8790-113">Dane użytkownika w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8790-113">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)
