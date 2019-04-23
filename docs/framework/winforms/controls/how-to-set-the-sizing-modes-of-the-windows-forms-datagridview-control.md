---
title: 'Instrukcje: ustawianie trybów zmieniania rozmiaru kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: d92322da6644c110f5e3177acebea62799a0ed89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977876"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="6092e-102">Instrukcje: ustawianie trybów zmieniania rozmiaru kontrolki DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6092e-102">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6092e-103">Poniższe procedury przedstawiają kilka typowych scenariuszy, dostosować można też połączyć dostępne opcje zmiany rozmiaru, które <xref:System.Windows.Forms.DataGridView> kontroli i określonych kolumn w formancie.</span><span class="sxs-lookup"><span data-stu-id="6092e-103">The following procedures demonstrate some common scenarios that customize or combine the sizing options available for the <xref:System.Windows.Forms.DataGridView> control and for specific columns in a control.</span></span>  
  
### <a name="to-create-a-fixed-width-column"></a><span data-ttu-id="6092e-104">Aby utworzyć kolumnę o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="6092e-104">To create a fixed-width column</span></span>  
  
-   <span data-ttu-id="6092e-105">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> właściwości <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> właściwości `true`i <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> właściwość do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="6092e-105">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, the <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> property to <xref:System.Windows.Forms.DataGridViewTriState.False>, the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property to `true`, and the <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> property to an appropriate value.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a><span data-ttu-id="6092e-106">Aby utworzyć kolumnę, który dostosowuje jego rozmiar w celu dopasowania do jego zawartości</span><span class="sxs-lookup"><span data-stu-id="6092e-106">To create a column that adjusts its size to fit its content</span></span>  
  
-   <span data-ttu-id="6092e-107">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> właściwość trybu ustalania rozmiaru na podstawie zawartości.</span><span class="sxs-lookup"><span data-stu-id="6092e-107">Set the <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> property to a content-based sizing mode.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a><span data-ttu-id="6092e-108">Aby utworzyć tryb wypełniania kolumny wartości różnych rozmiarach i ich znaczenie</span><span class="sxs-lookup"><span data-stu-id="6092e-108">To create fill-mode columns for values of varying size and importance</span></span>  
  
-   <span data-ttu-id="6092e-109">Ustaw <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> właściwość <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> można ustawić tryb zmiany rozmiaru dla wszystkich kolumn, które nie zastąpić tę wartość.</span><span class="sxs-lookup"><span data-stu-id="6092e-109">Set the <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> to set the sizing mode for all columns that do not override this value.</span></span> <span data-ttu-id="6092e-110">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> właściwości kolumn do wartości, które są proporcjonalne do ich średniej zawartości szerokości.</span><span class="sxs-lookup"><span data-stu-id="6092e-110">Set the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> properties of the columns to values that are proportional to their average content widths.</span></span> <span data-ttu-id="6092e-111">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> właściwości ważnych kolumnach, aby zapewnić wyświetlanie zawartości częściowej.</span><span class="sxs-lookup"><span data-stu-id="6092e-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> properties of important columns to ensure partial content display.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="6092e-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="6092e-112">Example</span></span>  
 <span data-ttu-id="6092e-113">Poniższy przykład kompletny kod zapewnia aplikacji demonstracyjnych, która może pomóc Ci zrozumieć opcje zmiany rozmiaru, opisane w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="6092e-113">The following complete code example provides a demonstration application that can help you understand the sizing options described in this topic.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 <span data-ttu-id="6092e-114">Aby użyć tej aplikacji demonstracyjnych:</span><span class="sxs-lookup"><span data-stu-id="6092e-114">To use this demonstration application:</span></span>  
  
-   <span data-ttu-id="6092e-115">Zmień rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="6092e-115">Change the size of the form.</span></span> <span data-ttu-id="6092e-116">Sprawdź, jak tryb wypełniania kolumn zmienić ich szerokości, gdy zachowanie proporcji wskazywanym przez <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="6092e-116">Observe how the fill-mode columns change their widths while retaining the proportions indicated by the <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> property values.</span></span> <span data-ttu-id="6092e-117">Sprawdź, jak w kolumnie <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> uniemożliwia zmianę, gdy formularz jest za mały.</span><span class="sxs-lookup"><span data-stu-id="6092e-117">Observe how a column's <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> prevents it from changing when the form is too small.</span></span>  
  
-   <span data-ttu-id="6092e-118">Zmień rozmiary kolumn, przeciągając separator kolumn za pomocą myszy.</span><span class="sxs-lookup"><span data-stu-id="6092e-118">Change the column sizes by dragging the column dividers with the mouse.</span></span> <span data-ttu-id="6092e-119">Sprawdź, jak niektóre kolumny nie może być o zmienionym rozmiarze i jak o zmiennym rozmiarze kolumn nie może zostać wykonana węższe niż ich minimalne szerokości.</span><span class="sxs-lookup"><span data-stu-id="6092e-119">Observe how some columns cannot be resized, and how resizable columns cannot be made narrower than their minimum widths.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6092e-120">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6092e-120">Compiling the Code</span></span>  
 <span data-ttu-id="6092e-121">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6092e-121">This example requires:</span></span>  
  
-   <span data-ttu-id="6092e-122">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6092e-122">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6092e-123">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6092e-123">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6092e-124">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="6092e-124">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6092e-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6092e-125">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
