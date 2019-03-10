---
title: 'Instrukcje: Określanie wartości domyślnych dla nowych wierszy w kontrolce DataGridView formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: cc854f0cdbef8373b74a16c7d5bc044cfee5aa84
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708031"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="4e85d-102">Instrukcje: Określanie wartości domyślnych dla nowych wierszy w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e85d-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4e85d-103">Wprowadzanie danych można wprowadzić bardziej wygodne, gdy aplikacja domyślnie wypełnia wartości dla nowo dodanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="4e85d-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="4e85d-104">Za pomocą <xref:System.Windows.Forms.DataGridView> klasy, możesz wpisać w domyślnych wartości za pomocą <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4e85d-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="4e85d-105">To zdarzenie jest wywoływane, gdy użytkownik wprowadzi wiersza dla nowych rekordów.</span><span class="sxs-lookup"><span data-stu-id="4e85d-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="4e85d-106">Kod, obsługując to zdarzenie, możesz wypełnić żądane komórki o wartości wybrane.</span><span class="sxs-lookup"><span data-stu-id="4e85d-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="4e85d-107">Poniższy przykład kodu demonstruje sposób określania wartości domyślne dla nowych wierszy przy użyciu <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4e85d-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e85d-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e85d-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4e85d-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4e85d-109">Compiling the Code</span></span>  
 <span data-ttu-id="4e85d-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4e85d-110">This example requires:</span></span>  
  
-   <span data-ttu-id="4e85d-111">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="4e85d-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="4e85d-112">A `NewCustomerId` funkcji do generowania unikatowych `CustomerID` wartości.</span><span class="sxs-lookup"><span data-stu-id="4e85d-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
-   <span data-ttu-id="4e85d-113">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="4e85d-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e85d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e85d-114">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [<span data-ttu-id="4e85d-115">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e85d-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="4e85d-116">Używanie wiersza dla nowych rekordów w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e85d-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
