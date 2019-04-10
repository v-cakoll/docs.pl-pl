---
title: 'Instrukcje: uzyskiwanie dostępu do obiektów powiązanych z wierszami kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 50882ab9a1a498bf8f76381e3f4aac53876abbb8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217409"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="005bd-102">Instrukcje: uzyskiwanie dostępu do obiektów powiązanych z wierszami kontrolki DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="005bd-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="005bd-103">Czasami warto wyświetlić tabelę informacji przechowywanych w kolekcji obiektów biznesowych.</span><span class="sxs-lookup"><span data-stu-id="005bd-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="005bd-104">Po powiązaniu <xref:System.Windows.Forms.DataGridView> formantu do tych kolekcji, każda właściwość publiczna jest wyświetlany w kolumnie swój własny, chyba że właściwość jest oznaczona za nie można przeglądać za pomocą <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="005bd-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="005bd-105">Na przykład zbiór `Customer` obiektów takich jak miałoby kolumn **nazwa** i **adres**.</span><span class="sxs-lookup"><span data-stu-id="005bd-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="005bd-106">Jeśli te obiekty zawierają dodatkowe informacje i kod, który chcesz uzyskać dostęp, mógł go osiągnąć za pomocą obiektów wiersza.</span><span class="sxs-lookup"><span data-stu-id="005bd-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="005bd-107">W poniższym przykładzie kodu użytkowników można wybrać wiele wierszy i kliknąć przycisk służący do wysyłania faktur do każdego z odpowiednich klientów.</span><span class="sxs-lookup"><span data-stu-id="005bd-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="005bd-108">Dostęp do obiektów powiązanych z wiersza</span><span class="sxs-lookup"><span data-stu-id="005bd-108">To access row-bound objects</span></span>  
  
-   <span data-ttu-id="005bd-109">Użyj <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="005bd-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="005bd-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="005bd-110">Example</span></span>  
 <span data-ttu-id="005bd-111">Pełny przykład kodu zawiera prosty `Customer` implementacji i powiązań <xref:System.Windows.Forms.DataGridView> do <xref:System.Collections.ArrayList> zawierającego kilka `Customer` obiektów.</span><span class="sxs-lookup"><span data-stu-id="005bd-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="005bd-112"><xref:System.Windows.Forms.Control.Click> Program obsługi zdarzeń <xref:System.Windows.Forms.Button?displayProperty=nameWithType> musi mieć dostęp `Customer` obiektów za pomocą wierszy, ponieważ kolekcja klienta nie jest dostępny na zewnątrz <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="005bd-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="005bd-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="005bd-113">Compiling the Code</span></span>  
 <span data-ttu-id="005bd-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="005bd-114">This example requires:</span></span>  
  
-   <span data-ttu-id="005bd-115">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="005bd-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="005bd-116">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="005bd-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="005bd-117">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="005bd-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="005bd-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="005bd-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [<span data-ttu-id="005bd-119">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="005bd-119">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="005bd-120">Instrukcje: powiązanie obiektów z kontrolkami DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="005bd-120">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
