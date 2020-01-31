---
title: Uzyskiwanie dostępu do obiektów powiązanych z wierszami kontrolki DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 0b9a4becb78ae817141728467c1e9ea5b693476d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743165"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="b25fa-102">Porady: uzyskiwanie dostępu do obiektów powiązanych z wierszami formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b25fa-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="b25fa-103">Czasami warto wyświetlić tabelę informacji przechowywanych w kolekcji obiektów biznesowych.</span><span class="sxs-lookup"><span data-stu-id="b25fa-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="b25fa-104">Po powiązaniu formantu <xref:System.Windows.Forms.DataGridView> z taką kolekcją Każda właściwość publiczna jest wyświetlana we własnej kolumnie, chyba że właściwość została oznaczona jako nieumożliwia przeglądania z <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b25fa-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="b25fa-105">Na przykład kolekcja obiektów `Customer` powinna zawierać kolumny, takie jak **Nazwa** i **adres**.</span><span class="sxs-lookup"><span data-stu-id="b25fa-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="b25fa-106">Jeśli te obiekty zawierają dodatkowe informacje i kod, do których chcesz uzyskać dostęp, możesz dotrzeć do niego za poorednictwem obiektów wierszy.</span><span class="sxs-lookup"><span data-stu-id="b25fa-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="b25fa-107">W poniższym przykładzie kodu użytkownicy mogą wybrać wiele wierszy i kliknąć przycisk, aby wysłać fakturę do każdego z odpowiednich klientów.</span><span class="sxs-lookup"><span data-stu-id="b25fa-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="b25fa-108">Aby uzyskać dostęp do obiektów powiązanych z wierszem</span><span class="sxs-lookup"><span data-stu-id="b25fa-108">To access row-bound objects</span></span>  
  
- <span data-ttu-id="b25fa-109">Użyj właściwości <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b25fa-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="b25fa-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="b25fa-110">Example</span></span>  
 <span data-ttu-id="b25fa-111">Pełny przykład kodu zawiera prostą implementację `Customer` i wiąże <xref:System.Windows.Forms.DataGridView> z <xref:System.Collections.ArrayList> zawierającą kilka `Customer` obiektów.</span><span class="sxs-lookup"><span data-stu-id="b25fa-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="b25fa-112">Procedura obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.Button?displayProperty=nameWithType> musi uzyskiwać dostęp do obiektów `Customer` za pomocą wierszy, ponieważ kolekcja klienta nie jest dostępna poza programem obsługi zdarzeń <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b25fa-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b25fa-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b25fa-113">Compiling the Code</span></span>  
 <span data-ttu-id="b25fa-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b25fa-114">This example requires:</span></span>  
  
- <span data-ttu-id="b25fa-115">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="b25fa-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b25fa-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b25fa-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b25fa-117">Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b25fa-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b25fa-118">Instrukcje: wiązanie obiektów z kontrolkami DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b25fa-118">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
