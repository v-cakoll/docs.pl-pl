---
title: Określ wartości domyślne dla nowych wierszy w formancie DataGridView
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
ms.openlocfilehash: 364f922aefc10e57f2ed7f3a0c2a5b25c922d87a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742929"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b7a57-102">Porady: określanie wartości domyślnych dla nowych wierszy w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b7a57-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b7a57-103">Wprowadzanie danych może być wygodniejsze, gdy aplikacja wypełnia wartości domyślne dla nowo dodanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="b7a57-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="b7a57-104">Za pomocą klasy <xref:System.Windows.Forms.DataGridView> można wypełnić wartości domyślne za pomocą zdarzenia <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.</span><span class="sxs-lookup"><span data-stu-id="b7a57-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="b7a57-105">To zdarzenie jest zgłaszane, gdy użytkownik wprowadzi wiersz dla nowych rekordów.</span><span class="sxs-lookup"><span data-stu-id="b7a57-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="b7a57-106">Gdy kod obsługuje to zdarzenie, można wypełniać odpowiednie komórki wybranymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="b7a57-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="b7a57-107">Poniższy przykład kodu demonstruje sposób określania wartości domyślnych dla nowych wierszy przy użyciu zdarzenia <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.</span><span class="sxs-lookup"><span data-stu-id="b7a57-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7a57-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7a57-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b7a57-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b7a57-109">Compiling the Code</span></span>  
 <span data-ttu-id="b7a57-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b7a57-110">This example requires:</span></span>  
  
- <span data-ttu-id="b7a57-111">Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="b7a57-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="b7a57-112">Funkcja `NewCustomerId` do generowania unikatowych wartości `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="b7a57-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
- <span data-ttu-id="b7a57-113">Odwołania do zestawów <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7a57-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a57-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7a57-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [<span data-ttu-id="b7a57-115">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b7a57-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="b7a57-116">Używanie wiersza dla nowych rekordów w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b7a57-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
