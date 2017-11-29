---
title: "Porady: obsługa zdarzeń związanych z danymi użytkownika w kontrolkach formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f64bfba5bc8c142ab4eadc3fb5c0ca0bb04f30f8
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="ea474-102">Porady: obsługa zdarzeń związanych z danymi użytkownika w kontrolkach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ea474-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="ea474-103">W tym przykładzie pokazano, jak obsługiwać większość klawiatura, mysz, fokus i zdarzenia walidacji, które mogą wystąpić w formancie formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ea474-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="ea474-104">Pole tekstowe o nazwie `TextBoxInput` odbiera zdarzenia, gdy fokus, a informacje o każdym zdarzeniu są zapisywane w polu tekstowym o nazwie `TextBoxOutput` w kolejności, w której zostaną podniesione zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ea474-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="ea474-105">Aplikacja zawiera także zestaw pól wyboru, które mogą służyć do filtrowania zdarzeń do raportu.</span><span class="sxs-lookup"><span data-stu-id="ea474-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea474-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea474-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ea474-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ea474-107">Compiling the Code</span></span>  
 <span data-ttu-id="ea474-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ea474-108">This example requires:</span></span>  
  
-   <span data-ttu-id="ea474-109">Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="ea474-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="ea474-110">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ea474-110">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ea474-111">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="ea474-111">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="ea474-112">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ea474-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea474-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea474-113">See Also</span></span>  
 [<span data-ttu-id="ea474-114">Dane wejściowe użytkownika w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ea474-114">User Input in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-in-windows-forms.md)
