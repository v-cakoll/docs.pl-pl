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
ms.openlocfilehash: e3ca2ab4be95a77bd2549ae8435d8158434532da
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220247"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="43275-102">Instrukcje: Powiązanie obiektów do kontrolek DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43275-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="43275-103">Poniższy przykład kodu pokazuje, jak powiązać kolekcji obiektów do <xref:System.Windows.Forms.DataGridView> sterowania, aby każdy obiekt jest wyświetlany jako oddzielny wiersz.</span><span class="sxs-lookup"><span data-stu-id="43275-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="43275-104">Ten przykład ilustruje także sposób wyświetlania właściwości dla typu wyliczenia w <xref:System.Windows.Forms.DataGridViewComboBoxColumn> tak, aby listy rozwijanej pola kombi zawiera wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="43275-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43275-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="43275-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43275-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="43275-106">Compiling the Code</span></span>  
 <span data-ttu-id="43275-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="43275-107">This example requires:</span></span>  
  
-   <span data-ttu-id="43275-108">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="43275-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="43275-109">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="43275-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="43275-110">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="43275-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43275-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43275-111">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="43275-112">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43275-112">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="43275-113">Instrukcje: Uzyskiwanie dostępu do obiektów powiązanych z Windows Forms wierszami formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="43275-113">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](../../../../docs/framework/winforms/controls/how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
