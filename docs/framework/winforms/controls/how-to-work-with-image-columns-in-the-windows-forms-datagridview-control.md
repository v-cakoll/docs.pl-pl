---
title: "Porady: praca z kolumnami obrazów w formancie DataGridView formularzy systemu Windows"
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
- image columns
- image columns [Windows Forms], Windows Forms
- DataGridView control [Windows Forms], image columns
ms.assetid: 8a37aa75-3c6e-4893-91d0-7a5f34bfe287
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f82b1ee3c769e4103f22d877ee399e62a778cbc1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-work-with-image-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ad816-102">Porady: praca z kolumnami obrazów w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ad816-102">How to: Work with Image Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ad816-103">Poniższy przykładowy kod przedstawia sposób użycia <xref:System.Windows.Forms.DataGridView> obrazu kolumn w interaktywnego interfejsu użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="ad816-103">The following code example shows how to use the <xref:System.Windows.Forms.DataGridView> image columns in an interactive user interface (UI).</span></span> <span data-ttu-id="ad816-104">W przykładzie pokazano również możliwości zmiany rozmiaru i Układ obrazu z <xref:System.Windows.Forms.DataGridViewImageColumn>.</span><span class="sxs-lookup"><span data-stu-id="ad816-104">The example also demonstrates image sizing and layout possibilities with the <xref:System.Windows.Forms.DataGridViewImageColumn>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad816-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad816-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ImageColumn_TicTacToe#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ImageColumn_TicTacToe/CPP/tictactoe.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ImageColumn_TicTacToe#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ImageColumn_TicTacToe/CS/tictactoe.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ImageColumn_TicTacToe#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ImageColumn_TicTacToe/VB/tictactoe.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ad816-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ad816-106">Compiling the Code</span></span>  
 <span data-ttu-id="ad816-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ad816-107">This example requires:</span></span>  
  
-   <span data-ttu-id="ad816-108">Odwołania do zestawów systemu i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="ad816-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="ad816-109">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ad816-109">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ad816-110">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="ad816-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="ad816-111">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ad816-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad816-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad816-112">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewImageColumn>  
 [<span data-ttu-id="ad816-113">Programowanie przy użyciu komórek, wierszy i kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ad816-113">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 [<span data-ttu-id="ad816-114">Porady: wyświetlanie obrazów w komórkach systemu Windows do formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="ad816-114">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
