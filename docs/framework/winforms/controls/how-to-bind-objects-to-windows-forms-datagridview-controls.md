---
title: 'Instrukcje: Powiązanie obiektów do kontrolek DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: 9f3ce61b3692f0b83298bdf9a19cb98fb5d5ab7f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723806"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="8a6df-102">Instrukcje: Powiązanie obiektów do kontrolek DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a6df-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="8a6df-103">Poniższy przykład kodu pokazuje, jak powiązać kolekcji obiektów do <xref:System.Windows.Forms.DataGridView> sterowania, aby każdy obiekt jest wyświetlany jako oddzielny wiersz.</span><span class="sxs-lookup"><span data-stu-id="8a6df-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="8a6df-104">Ten przykład ilustruje także sposób wyświetlania właściwości dla typu wyliczenia w <xref:System.Windows.Forms.DataGridViewComboBoxColumn> tak, aby listy rozwijanej pola kombi zawiera wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="8a6df-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a6df-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a6df-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8a6df-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8a6df-106">Compiling the Code</span></span>  
 <span data-ttu-id="8a6df-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="8a6df-107">This example requires:</span></span>  
  
-   <span data-ttu-id="8a6df-108">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="8a6df-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8a6df-109">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8a6df-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8a6df-110">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="8a6df-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a6df-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a6df-111">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="8a6df-112">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8a6df-112">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="8a6df-113">Instrukcje: Uzyskiwanie dostępu do obiektów powiązanych z Windows Forms wierszami formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="8a6df-113">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
