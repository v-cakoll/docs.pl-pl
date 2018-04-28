---
title: 'Porady: uzyskiwanie dostępu do obiektów powiązanych z wierszami formantu DataGridView formularzy systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1cd29b04565b29f1cdbc78c070e5cc74baa350f3
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="ae45c-102">Porady: uzyskiwanie dostępu do obiektów powiązanych z wierszami formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ae45c-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="ae45c-103">Czasami jest przydatne wyświetlić tabelę informacji przechowywanych w kolekcji obiektów biznesowych.</span><span class="sxs-lookup"><span data-stu-id="ae45c-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="ae45c-104">Po powiązaniu <xref:System.Windows.Forms.DataGridView> formant do tych kolekcji, każda właściwość publiczna jest wyświetlany w kolumnie, chyba że właściwość jest oznaczona nie można przeglądać z <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ae45c-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="ae45c-105">Na przykład kolekcja `Customer` obiekty takie jak miałoby kolumn **nazwa** i **adres**.</span><span class="sxs-lookup"><span data-stu-id="ae45c-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="ae45c-106">Jeśli te obiekty zawierają dodatkowe informacje i kod, który chcesz uzyskać dostęp, możesz uzyskać do niej dostęp za pośrednictwem obiektów wiersza.</span><span class="sxs-lookup"><span data-stu-id="ae45c-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="ae45c-107">W poniższym przykładzie kodu użytkownicy mogą wybrać wiele wierszy i kliknij przycisk, aby wysłać faktury do każdego z odpowiednich klientów.</span><span class="sxs-lookup"><span data-stu-id="ae45c-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="ae45c-108">Dostęp do obiektów powiązanych z wiersza</span><span class="sxs-lookup"><span data-stu-id="ae45c-108">To access row-bound objects</span></span>  
  
-   <span data-ttu-id="ae45c-109">Użyj <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ae45c-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="ae45c-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae45c-110">Example</span></span>  
 <span data-ttu-id="ae45c-111">Pełny przykład kodu obejmuje prostą `Customer` implementacji i wiązania <xref:System.Windows.Forms.DataGridView> do <xref:System.Collections.ArrayList> zawierającego kilka `Customer` obiektów.</span><span class="sxs-lookup"><span data-stu-id="ae45c-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="ae45c-112"><xref:System.Windows.Forms.Control.Click> Obsługi zdarzeń <xref:System.Windows.Forms.Button?displayProperty=nameWithType> muszą uzyskać dostęp do `Customer` obiektów za pomocą wierszy, ponieważ kolekcja klienta nie jest dostępny na zewnątrz <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ae45c-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae45c-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ae45c-113">Compiling the Code</span></span>  
 <span data-ttu-id="ae45c-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ae45c-114">This example requires:</span></span>  
  
-   <span data-ttu-id="ae45c-115">Odwołania do zestawów systemu i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="ae45c-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="ae45c-116">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ae45c-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ae45c-117">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="ae45c-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="ae45c-118">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ae45c-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae45c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae45c-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="ae45c-120">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ae45c-120">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="ae45c-121">Instrukcje: wiązanie obiektów z kontrolkami DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ae45c-121">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)
