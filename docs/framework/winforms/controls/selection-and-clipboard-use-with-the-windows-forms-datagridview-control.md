---
title: Wybór i używanie schowka za pomocą składnika DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], Clipboard use
- cells [Windows Forms], selecting in grids
- Clipboard [Windows Forms], in DataGridView control
- selection [Windows Forms], in DataGridView control
- data grids [Windows Forms], selecting cells
- DataGridView control [Windows Forms], selecting cells
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
ms.openlocfilehash: 1836fbc1887082ca685c49bef2bc42bdb167578f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902255"
---
# <a name="selection-and-clipboard-use-with-the-windows-forms-datagridview-control"></a><span data-ttu-id="0f1fc-102">Wybór i używanie schowka za pomocą składnika DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0f1fc-102">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0f1fc-103">`DataGridView` Kontroli udostępnia szereg opcji dotyczących konfigurowania, jak użytkownicy mogą wybrać komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-103">The `DataGridView` control provides you with a variety of options for configuring how users can select cells, rows, and columns.</span></span> <span data-ttu-id="0f1fc-104">Na przykład można włączyć wybór jednego lub wielu, wybranych całych wierszy lub kolumn, gdy użytkownik kliknie komórki lub wybór całych wierszy lub kolumn tylko wtedy, gdy użytkownik kliknie ich nagłówki, co umożliwia także zaznaczenie komórki.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-104">For example, you can enable single or multiple selection, selection of whole rows or columns when users click cells, or selection of whole rows or columns only when users click their headers, which enables cell selection as well.</span></span> <span data-ttu-id="0f1fc-105">Jeśli chcesz udostępnić interfejs użytkownika do wyboru, można wyłączyć zwykłych wybór i obsługiwać wszystkie zaznaczenia programowo.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-105">If you want to provide your own user interface for selection, you can disable ordinary selection and handle all selection programmatically.</span></span> <span data-ttu-id="0f1fc-106">Ponadto można umożliwić użytkownikom skopiuj wybrane wartości do Schowka.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-106">Additionally, you can enable users to copy the selected values to the Clipboard.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f1fc-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0f1fc-107">In This Section</span></span>  
 [<span data-ttu-id="0f1fc-108">Tryby wyboru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f1fc-108">Selection Modes in the Windows Forms DataGridView Control</span></span>](selection-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0f1fc-109">W tym artykule opisano opcje użytkownika i programowe zaznaczenie w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-109">Describes the options for user and programmatic selection in the control.</span></span>  
  
 [<span data-ttu-id="0f1fc-110">Instrukcje: Ustawianie trybu zaznaczania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f1fc-110">How to: Set the Selection Mode of the Windows Forms DataGridView Control</span></span>](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0f1fc-111">W tym artykule opisano sposób konfigurowania kontroli do wyboru pojedynczy wiersz tabeli, gdy użytkownik kliknie komórki.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-111">Describes how to configure the control for single-row selection when a user clicks a cell.</span></span>  
  
 [<span data-ttu-id="0f1fc-112">Instrukcje: Pobieranie wybranych komórek, wierszy i kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f1fc-112">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](selected-cells-rows-and-columns-datagridview.md)  
 <span data-ttu-id="0f1fc-113">W tym artykule opisano sposób pracy z wybranymi kolekcjami komórek, wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-113">Describes how to work with the selected cell, row, and column collections.</span></span>  
  
 [<span data-ttu-id="0f1fc-114">Instrukcje: Umożliwianie użytkownikom kopiowania wielu komórek do Schowka z kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f1fc-114">How to: Enable Users to Copy Multiple Cells to the Clipboard from the Windows Forms DataGridView Control</span></span>](enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 <span data-ttu-id="0f1fc-115">W tym artykule opisano sposób włączania Obsługa schowka w formancie.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-115">Describes how to enable Clipboard support in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0f1fc-116">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="0f1fc-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="0f1fc-117">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="0f1fc-118">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <span data-ttu-id="0f1fc-119">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <span data-ttu-id="0f1fc-120">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <span data-ttu-id="0f1fc-121">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <span data-ttu-id="0f1fc-122">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="0f1fc-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f1fc-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f1fc-123">See also</span></span>

- [<span data-ttu-id="0f1fc-124">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="0f1fc-124">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="0f1fc-125">Domyślna obsługa myszy i klawiatury w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f1fc-125">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
