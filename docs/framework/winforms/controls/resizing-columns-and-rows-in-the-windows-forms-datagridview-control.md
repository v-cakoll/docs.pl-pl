---
title: Zmiana rozmiaru wierszy i kolumn w formancie DataGridView formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3621b05f1faae671d93106f50dfef1311959e48e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7d0b2-102">Zmiana rozmiaru wierszy i kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7d0b2-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7d0b2-103">`DataGridView` Kontroli udostępnia wiele opcji dostosowywania zachowanie ustalania rozmiaru kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="7d0b2-104">Zazwyczaj `DataGridView` rozmiary komórki nie są zmieniane na podstawie ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="7d0b2-105">Zamiast tego należy ich Przytnij żadnych wartości wyświetlania, która jest większa niż komórki.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="7d0b2-106">Jeśli zawartość może być wyświetlana jako ciąg, komórki wyświetla go w etykietce narzędzia.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="7d0b2-107">Domyślnie użytkownicy przeciągnąć wierszy, kolumny i separatorów nagłówka przy użyciu myszy, aby wyświetlić więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="7d0b2-108">Użytkownicy można także kliknąć dwukrotnie linię podziału, aby automatycznie zmienić rozmiar skojarzony wierszy, kolumny lub nagłówek grupy na podstawie jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="7d0b2-109">`DataGridView` Kontroli udostępnia właściwości, metody i zdarzenia, które pozwalają dostosować lub wyłączyć wszystkie te zachowania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="7d0b2-110">Ponadto należy programowo zmienić rozmiar wierszy, kolumny i nagłówki do ich zawartości lub można skonfigurować je, aby automatycznie zmieniać wielkość zmianie ich zawartość.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="7d0b2-111">Można również skonfigurować kolumny do automatycznego dzielenia dostępne szerokość formantu w proporcjach przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d0b2-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7d0b2-112">In This Section</span></span>  
 [<span data-ttu-id="7d0b2-113">Opcje rozmiaru w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7d0b2-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7d0b2-114">Opisuje opcje zmiana rozmiaru wierszy, kolumny i nagłówków.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="7d0b2-115">Również szczegółowe informacje dotyczące ustalania rozmiaru właściwości i metod i opisano typowe scenariusze użycia.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="7d0b2-116">Kolumna wypełnienia trybu w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7d0b2-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7d0b2-117">Tryb wypełniania kolumny szczegółowo opisano i udostępnia pokaz kod, który służy do eksperymentów z tryb wypełniania kolumny i innych trybów.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="7d0b2-118">Porady: Ustawianie trybów zmieniania rozmiaru formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7d0b2-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="7d0b2-119">Zawiera opis sposobu konfigurowania trybów zmieniania rozmiaru dla wspólnych celów.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="7d0b2-120">Porady: programowane formantu DataGridView formularzy rozmiaru komórek w celu dopasowania do zawartości w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="7d0b2-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="7d0b2-121">Udostępnia pokaz kod, który służy do eksperymentów z programowe zmiana rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="7d0b2-122">Porady: automatyczne zmienianie rozmiaru komórek, gdy zawartość formantu DataGridView formularzy zmian w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="7d0b2-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="7d0b2-123">Zawiera kod demonstracyjnych, który służy do eksperymentów z trybów automatycznej zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7d0b2-124">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="7d0b2-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="7d0b2-125">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="7d0b2-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d0b2-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d0b2-126">See Also</span></span>  
 [<span data-ttu-id="7d0b2-127">DataGridView — formant</span><span class="sxs-lookup"><span data-stu-id="7d0b2-127">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
