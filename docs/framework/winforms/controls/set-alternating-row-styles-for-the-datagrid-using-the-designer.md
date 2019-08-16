---
title: 'Instrukcje: ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 1be746d4cce36344e034692a0e2e8e6a9e9320d5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040438"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="44b42-102">Instrukcje: ustawianie przemiennych wierszy dla kontrolki DataGridView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="44b42-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer</span></span>

<span data-ttu-id="44b42-103">Dane tabelaryczne często są prezentowane w formacie podobnym do księgi, w którym przemienne wiersze mają różne kolory tła.</span><span class="sxs-lookup"><span data-stu-id="44b42-103">Tabular data is often presented in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="44b42-104">Ten format ułatwia użytkownikom informowanie, które komórki znajdują się w każdym wierszu, szczególnie w przypadku szerokich tabel z wieloma kolumnami.</span><span class="sxs-lookup"><span data-stu-id="44b42-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>

<span data-ttu-id="44b42-105">Za pomocą <xref:System.Windows.Forms.DataGridView> kontrolki można określić pełne informacje o stylu dla przemiennych wierszy.</span><span class="sxs-lookup"><span data-stu-id="44b42-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="44b42-106">Możesz użyć cech stylu, takich jak kolor i czcionka pierwszego planu, oprócz koloru tła w celu odróżnienia przemiennych wierszy.</span><span class="sxs-lookup"><span data-stu-id="44b42-106">You can use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span> <span data-ttu-id="44b42-107">Aby uzyskać więcej informacji, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="44b42-107">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>

<span data-ttu-id="44b42-108">Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym <xref:System.Windows.Forms.DataGridView> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="44b42-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="44b42-109">Aby uzyskać informacje na temat konfigurowania takiego projektu, zobacz [How to: Utwórz projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikacji Windows Forms i [instrukcje: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="44b42-109">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>


### <a name="define-styles-for-alternating-rows"></a><span data-ttu-id="44b42-110">Definiowanie stylów dla przemiennych wierszy</span><span class="sxs-lookup"><span data-stu-id="44b42-110">Define styles for alternating rows</span></span>

1. <span data-ttu-id="44b42-111"><xref:System.Windows.Forms.DataGridView> Wybierz kontrolkę w projektancie.</span><span class="sxs-lookup"><span data-stu-id="44b42-111">Select the <xref:System.Windows.Forms.DataGridView> control in the designer.</span></span>

2. <span data-ttu-id="44b42-112">W oknie **Właściwości** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="44b42-112">In the **Properties** window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> property.</span></span>

3. <span data-ttu-id="44b42-113">W oknie dialogowym **Konstruktor komórek** Zdefiniuj styl, ustawiając właściwości, a następnie użyj okienka **podglądu** , aby potwierdzić wybór.</span><span class="sxs-lookup"><span data-stu-id="44b42-113">In the **CellStyle Builder** dialog box, define the style by setting the properties, and use the **Preview** pane to confirm your choices.</span></span> <span data-ttu-id="44b42-114">Określone style są używane dla każdego innego wiersza wyświetlanego w kontrolce, rozpoczynając od drugiego.</span><span class="sxs-lookup"><span data-stu-id="44b42-114">The styles you specify are used for every other row displayed in the control, starting with the second one.</span></span>

4. <span data-ttu-id="44b42-115">Aby zdefiniować Style dla pozostałych wierszy, powtórz kroki 2 i 3 przy użyciu <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="44b42-115">To define styles for the remaining rows, repeat steps 2 and 3 using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property.</span></span>

    > [!NOTE]
    > <span data-ttu-id="44b42-116">Komórki są wyświetlane przy użyciu stylów dziedziczonych z wielu właściwości.</span><span class="sxs-lookup"><span data-stu-id="44b42-116">Cells are displayed using styles inherited from multiple properties.</span></span> <span data-ttu-id="44b42-117">Aby uzyskać więcej informacji na temat dziedziczenia stylu, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="44b42-117">For more information about style inheritance, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44b42-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44b42-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="44b42-119">Style komórki w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44b42-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="44b42-120">Podstawowe formatowanie i style w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44b42-120">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="44b42-121">Używanie narzędzia Projektant z kontrolką DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44b42-121">Using the Designer with the Windows Forms DataGridView Control</span></span>](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="44b42-122">Instrukcje: Tworzenie projektu aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44b42-122">How to: Create a Windows Forms application project</span></span>](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [<span data-ttu-id="44b42-123">Instrukcje: Dodawanie formantów do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44b42-123">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
