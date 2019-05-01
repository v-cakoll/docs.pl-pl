---
title: 'Instrukcje: Tworzenie standardowego okna dialogowego interfejsu użytkownika przy użyciu siatki'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 0ade908e92e552017acb9ba242ccba2c28c3c995
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051055"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="14312-102">Instrukcje: Tworzenie standardowego okna dialogowego interfejsu użytkownika przy użyciu siatki</span><span class="sxs-lookup"><span data-stu-id="14312-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="14312-103">W tym przykładzie przedstawiono sposób tworzenia standardowego [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] okno dialogowe, za pomocą <xref:System.Windows.Controls.Grid> elementu.</span><span class="sxs-lookup"><span data-stu-id="14312-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14312-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="14312-104">Example</span></span>  
 <span data-ttu-id="14312-105">Poniższy przykład tworzy okno dialogowe, takich jak **Uruchom** okno dialogowe w [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="14312-105">The following example creates a dialog box like the **Run** dialog box in the [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="14312-106">W przykładzie jest tworzony <xref:System.Windows.Controls.Grid> i używa <xref:System.Windows.Controls.ColumnDefinition> i <xref:System.Windows.Controls.RowDefinition> klasy zdefiniowanie pięciu kolumn i cztery wiersze.</span><span class="sxs-lookup"><span data-stu-id="14312-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="14312-107">Przykład następnie dodaje i umieszcza <xref:System.Windows.Controls.Image>, `RunIcon.png`, do reprezentowania obraz, który znajduje się w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="14312-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="14312-108">Obraz jest umieszczany w pierwszej kolumnie, a wiersz <xref:System.Windows.Controls.Grid> (lewy górny róg).</span><span class="sxs-lookup"><span data-stu-id="14312-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="14312-109">Następnie w przykładzie dodano <xref:System.Windows.Controls.TextBlock> element do pierwszej kolumny, która obejmuje pozostałych kolumnach pierwszego wiersza.</span><span class="sxs-lookup"><span data-stu-id="14312-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="14312-110">Dodaje, kolejny <xref:System.Windows.Controls.TextBlock> elementu do drugiego wiersza w pierwszej kolumnie do reprezentowania **Otwórz** pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="14312-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="14312-111">A <xref:System.Windows.Controls.TextBlock> poniżej, które reprezentuje obszaru wprowadzania danych.</span><span class="sxs-lookup"><span data-stu-id="14312-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="14312-112">Ponadto w przykładzie dodano trzy <xref:System.Windows.Controls.Button> elementów w ostatnim wierszu, które reprezentują **OK**, **anulować**, i **Przeglądaj** zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="14312-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="14312-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14312-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [<span data-ttu-id="14312-114">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="14312-114">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="14312-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="14312-115">How-to Topics</span></span>](grid-how-to-topics.md)
