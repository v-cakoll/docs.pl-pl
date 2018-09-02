---
title: 'Porady: obsługa zdarzeń związanych z danymi użytkownika w kontrolkach formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: 3b15edfec25282d5a0b79ef48cabd2a27c694055
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387812"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="3595a-102">Porady: obsługa zdarzeń związanych z danymi użytkownika w kontrolkach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3595a-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="3595a-103">W tym przykładzie pokazano, jak obsługiwać większość klawiatury, myszy, fokus i zdarzenia sprawdzania poprawności, które mogą wystąpić w kontrolce Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3595a-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="3595a-104">Pole tekstowe o nazwie `TextBoxInput` odbiera zdarzenia, gdy ma ona fokus, a informacje dotyczące każdego zdarzenia są zapisywane w polu tekstowym o nazwie `TextBoxOutput` w kolejności, w której zdarzenia są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="3595a-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="3595a-105">Aplikacja zawiera także zestaw pól wyboru, które mogą służyć do filtrowania zdarzeń do raportu.</span><span class="sxs-lookup"><span data-stu-id="3595a-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3595a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="3595a-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3595a-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3595a-107">Compiling the Code</span></span>  
 <span data-ttu-id="3595a-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="3595a-108">This example requires:</span></span>  
  
-   <span data-ttu-id="3595a-109">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="3595a-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3595a-110">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3595a-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3595a-111">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="3595a-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="3595a-112">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="3595a-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3595a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3595a-113">See Also</span></span>  
 [<span data-ttu-id="3595a-114">Dane użytkownika w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3595a-114">User Input in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-in-windows-forms.md)
