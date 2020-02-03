---
title: Ustawianie trybów ustalania rozmiarów kontrolki DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 15b084afa4149ac43d40aeae7f35f0eaff5ac0e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738390"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="961ea-102">Porady: ustawianie trybów zmieniania rozmiaru formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="961ea-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="961ea-103">W poniższych procedurach przedstawiono niektóre typowe scenariusze, które dostosowują lub łączą opcje ustalania rozmiarów dostępne dla kontrolki <xref:System.Windows.Forms.DataGridView> i dla konkretnych kolumn w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="961ea-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="961ea-104">Aby utworzyć kolumnę o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="961ea-104">To create a fixed-width column</span></span>  
  
- <span data-ttu-id="961ea-105">Ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, właściwość <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> na <xref:System.Windows.Forms.DataGridViewTriState.False>, właściwość <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> na `true`i Właściwość <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="961ea-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="961ea-106">Aby utworzyć kolumnę, która dostosowuje jej rozmiar w celu dopasowania jej do zawartości</span><span class="sxs-lookup"><span data-stu-id="961ea-106">To create a column that adjusts its size to fit its content</span></span>  
  
- <span data-ttu-id="961ea-107">Ustaw właściwość <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> na tryb ustalania wielkości na podstawie zawartości.</span><span class="sxs-lookup"><span data-stu-id="961ea-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="961ea-108">Aby utworzyć kolumny trybu wypełniania dla wartości o różnej wielkości i ważności</span><span class="sxs-lookup"><span data-stu-id="961ea-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
- <span data-ttu-id="961ea-109">Ustaw właściwość <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> na <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>, aby ustawić tryb ustalania szerokości dla wszystkich kolumn, które nie przesłaniają tej wartości.</span><span class="sxs-lookup"><span data-stu-id="961ea-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="961ea-110">Ustaw właściwości <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> kolumn na wartości proporcjonalnie do ich średnich szerokości zawartości.</span><span class="sxs-lookup"><span data-stu-id="961ea-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="961ea-111">Ustaw właściwości <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> ważnych kolumn, aby zapewnić wyświetlanie częściowej zawartości.</span><span class="sxs-lookup"><span data-stu-id="961ea-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="961ea-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="961ea-112">Example</span></span>  
 <span data-ttu-id="961ea-113">Poniższy kompletny przykład kodu zawiera aplikację demonstracyjną, która może pomóc w zrozumieniu opcji zmiany wielkości opisanej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="961ea-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="961ea-114">Aby użyć tej aplikacji demonstracyjnej:</span><span class="sxs-lookup"><span data-stu-id="961ea-114">To use this demonstration application:</span></span>  
  
- <span data-ttu-id="961ea-115">Zmień rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="961ea-115">Change the size of the form.</span></span> <span data-ttu-id="961ea-116">Obserwuj, jak kolumny trybu wypełniania zmieniają ich szerokości, zachowując proporcje wskazywane przez wartości właściwości <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="961ea-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="961ea-117">Obserwuj, jak <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> kolumny uniemożliwiają jej zmianę, gdy formularz jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="961ea-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
- <span data-ttu-id="961ea-118">Zmień rozmiary kolumn, przeciągając rozdzielacze kolumn za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="961ea-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="961ea-119">Zwróć uwagę na to, jak nie można zmienić rozmiaru niektórych kolumn i jak kolumny o zmiennym rozmiarze nie mogą być węższe niż ich minimalne szerokości.</span><span class="sxs-lookup"><span data-stu-id="961ea-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="961ea-120">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="961ea-120">Compiling the Code</span></span>  
 <span data-ttu-id="961ea-121">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="961ea-121">This example requires:</span></span>  
  
- <span data-ttu-id="961ea-122">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="961ea-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="961ea-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="961ea-123">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
