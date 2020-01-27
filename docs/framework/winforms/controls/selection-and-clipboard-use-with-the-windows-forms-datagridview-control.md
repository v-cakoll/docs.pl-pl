---
title: Wybór i używanie schowka za pomocą kontrolki DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
ms.openlocfilehash: 6993f77e8ce532d8df1bdc7e6b6abc1cc3268e49
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743063"
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="3cb21-102">Wybór i używanie schowka za pomocą składnika DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3cb21-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="3cb21-103">Formant `DataGridView` zapewnia różne opcje konfigurowania, w jaki sposób użytkownicy mogą wybierać komórki, wiersze i kolumny.</span><span class="sxs-lookup"><span data-stu-id="3cb21-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="3cb21-104">Na przykład można włączyć zaznaczanie pojedyncze lub wielokrotne, wybór całych wierszy lub kolumn, gdy użytkownicy będą klikać komórki lub zaznaczać całe wiersze lub kolumny tylko wtedy, gdy użytkownicy klikają nagłówki, co umożliwia również wybór komórek.</span><span class="sxs-lookup"><span data-stu-id="3cb21-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="3cb21-105">Jeśli chcesz podać własny interfejs użytkownika do wyboru, możesz wyłączyć zwykły wybór i programowo obsłużyć wszystkie wybrane opcje.</span><span class="sxs-lookup"><span data-stu-id="3cb21-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="3cb21-106">Ponadto można umożliwić użytkownikom kopiowanie wybranych wartości do Schowka.</span><span class="sxs-lookup"><span data-stu-id="3cb21-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3cb21-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3cb21-107">In This Section</span></span>  
 [<span data-ttu-id="3cb21-108">Tryby wyboru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3cb21-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3cb21-109">W tym artykule opisano opcje dla użytkownika i wybór programistyczny w formancie.</span><span class="sxs-lookup"><span data-stu-id="3cb21-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="3cb21-110">Instrukcje: ustawianie trybu zaznaczania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3cb21-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3cb21-111">Opisuje sposób skonfigurowania kontrolki wyboru pojedynczego wiersza, gdy użytkownik kliknie komórkę.</span><span class="sxs-lookup"><span data-stu-id="3cb21-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="3cb21-112">Instrukcje: pobieranie wybranych komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3cb21-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="3cb21-113">Opisuje sposób pracy z zaznaczonymi komórkami, wierszami i kolekcjami kolumn.</span><span class="sxs-lookup"><span data-stu-id="3cb21-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="3cb21-114">Instrukcje: umożliwianie użytkownikom kopiowania wielu komórek do schowka z kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3cb21-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="3cb21-115">Opisuje sposób włączania obsługi Schowka w formancie.</span><span class="sxs-lookup"><span data-stu-id="3cb21-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3cb21-116">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="3cb21-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="3cb21-117">Zawiera dokumentację referencyjną dla kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="3cb21-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="3cb21-118">Zawiera dokumentację referencyjną dla właściwości <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="3cb21-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="3cb21-119">Zawiera dokumentację referencyjną dla właściwości <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="3cb21-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="3cb21-120">Zawiera dokumentację referencyjną dla klasy <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>.</span><span class="sxs-lookup"><span data-stu-id="3cb21-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="3cb21-121">Zawiera dokumentację referencyjną dla klasy <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>.</span><span class="sxs-lookup"><span data-stu-id="3cb21-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="3cb21-122">Zawiera dokumentację referencyjną dla klasy <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>.</span><span class="sxs-lookup"><span data-stu-id="3cb21-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb21-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3cb21-123">See also</span></span>

- [<span data-ttu-id="3cb21-124">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="3cb21-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="3cb21-125">Domyślna obsługa myszy i klawiatury w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3cb21-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
