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
ms.openlocfilehash: f4f36622d16ee7b1fcbd743f73e376283d04e76a
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261053"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a><span data-ttu-id="fd22f-102">Instrukcje: Tworzenie formantu DataGridView formularzy Windows niepowiązanych</span><span class="sxs-lookup"><span data-stu-id="fd22f-102">How to: Create an Unbound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fd22f-103">Poniższy przykład kodu pokazuje, jak wypełnić <xref:System.Windows.Forms.DataGridView> kontroli programowo bez powiązania go ze źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="fd22f-103">The following code example demonstrates how to populate a <xref:System.Windows.Forms.DataGridView> control programmatically without binding it to a data source.</span></span> <span data-ttu-id="fd22f-104">Jest to przydatne, jeśli masz niewielką ilość danych, które mają być wyświetlane w formacie tabeli.</span><span class="sxs-lookup"><span data-stu-id="fd22f-104">This is useful when you have a small amount of data that you want to display in a table format.</span></span>  
  
 <span data-ttu-id="fd22f-105">Aby uzyskać pełne wyjaśnienie ten przykład kodu, zobacz [instruktażu: Tworzenie Windows niezwiązanego formantu DataGridView formularzy](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="fd22f-105">For a complete explanation of this code example, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd22f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd22f-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fd22f-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="fd22f-107">Compiling the Code</span></span>  
 <span data-ttu-id="fd22f-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="fd22f-108">This example requires:</span></span>  
  
-   <span data-ttu-id="fd22f-109">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="fd22f-109">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="fd22f-110">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fd22f-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="fd22f-111">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="fd22f-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  

## <a name="see-also"></a><span data-ttu-id="fd22f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd22f-112">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="fd22f-113">Przewodnik: Tworzenie Windows niezwiązanego formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="fd22f-113">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [<span data-ttu-id="fd22f-114">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fd22f-114">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="fd22f-115">Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fd22f-115">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
