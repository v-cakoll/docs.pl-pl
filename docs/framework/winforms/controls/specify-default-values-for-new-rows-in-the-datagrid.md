---
title: 'Instrukcje: określanie wartości domyślnych dla nowych wierszy w kontrolce DataGridView formularzy systemu Windows'
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
ms.openlocfilehash: 8a90cbef7032fd3753a6c9ec0b856a4e2ea1db27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193697"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="134de-102">Instrukcje: określanie wartości domyślnych dla nowych wierszy w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="134de-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="134de-103">Wprowadzanie danych można wprowadzić bardziej wygodne, gdy aplikacja domyślnie wypełnia wartości dla nowo dodanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="134de-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="134de-104">Za pomocą <xref:System.Windows.Forms.DataGridView> klasy, możesz wpisać w domyślnych wartości za pomocą <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="134de-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="134de-105">To zdarzenie jest wywoływane, gdy użytkownik wprowadzi wiersza dla nowych rekordów.</span><span class="sxs-lookup"><span data-stu-id="134de-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="134de-106">Kod, obsługując to zdarzenie, możesz wypełnić żądane komórki o wartości wybrane.</span><span class="sxs-lookup"><span data-stu-id="134de-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="134de-107">Poniższy przykład kodu demonstruje sposób określania wartości domyślne dla nowych wierszy przy użyciu <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="134de-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="134de-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="134de-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="134de-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="134de-109">Compiling the Code</span></span>  
 <span data-ttu-id="134de-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="134de-110">This example requires:</span></span>  
  
-   <span data-ttu-id="134de-111">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="134de-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="134de-112">A `NewCustomerId` funkcji do generowania unikatowych `CustomerID` wartości.</span><span class="sxs-lookup"><span data-stu-id="134de-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
-   <span data-ttu-id="134de-113">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="134de-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="134de-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="134de-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [<span data-ttu-id="134de-115">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="134de-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="134de-116">Używanie wiersza dla nowych rekordów w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="134de-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
