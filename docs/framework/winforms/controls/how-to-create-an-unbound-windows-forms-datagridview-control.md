---
title: 'Instrukcje: Tworzenie formantu DataGridView formularzy Windows niepowiązanych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
ms.assetid: b5d4b47d-9a28-4d88-9dba-0a3c90fba71d
ms.openlocfilehash: a1752be8aaac71dff62fe0e4fcd75ab8e386bae5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703107"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a><span data-ttu-id="46518-102">Instrukcje: Tworzenie formantu DataGridView formularzy Windows niepowiązanych</span><span class="sxs-lookup"><span data-stu-id="46518-102">How to: Create an Unbound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="46518-103">Poniższy przykład kodu pokazuje, jak wypełnić <xref:System.Windows.Forms.DataGridView> kontroli programowo bez powiązania go ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="46518-103">The following code example demonstrates how to populate a <xref:System.Windows.Forms.DataGridView> control programmatically without binding it to a data source.</span></span> <span data-ttu-id="46518-104">Jest to przydatne, jeśli masz niewielką ilość danych, które mają być wyświetlane w formacie tabeli.</span><span class="sxs-lookup"><span data-stu-id="46518-104">This is useful when you have a small amount of data that you want to display in a table format.</span></span>  
  
 <span data-ttu-id="46518-105">Aby uzyskać pełne wyjaśnienie ten przykład kodu, zobacz [instruktażu: Tworzenie Windows niezwiązanego formantu DataGridView formularzy](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="46518-105">For a complete explanation of this code example, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="46518-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="46518-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="46518-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="46518-107">Compiling the Code</span></span>  
 <span data-ttu-id="46518-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="46518-108">This example requires:</span></span>  
  
-   <span data-ttu-id="46518-109">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="46518-109">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="46518-110">Aby uzyskać informacje o tworzeniu tego przykładu z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="46518-110">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="46518-111">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="46518-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="46518-112">Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="46518-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46518-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46518-113">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="46518-114">Przewodnik: Tworzenie Windows niezwiązanego formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="46518-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [<span data-ttu-id="46518-115">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46518-115">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="46518-116">Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46518-116">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
