---
title: Zmień rozmiar kolumn i wierszy w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: 8f8394a837ccc11c469f9ad4feeb60464d0014fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742414"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b28b0-102">Zmiana rozmiaru wierszy i kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b28b0-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b28b0-103">Kontrolka `DataGridView` udostępnia wiele opcji dostosowywania zachowania rozmiarów kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="b28b0-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="b28b0-104">Zwykle komórki `DataGridView` nie są zmieniane na podstawie ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="b28b0-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="b28b0-105">Zamiast tego obcinają wartość wyświetlaną, która jest większa niż komórka.</span><span class="sxs-lookup"><span data-stu-id="b28b0-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="b28b0-106">Jeśli zawartość może być wyświetlana jako ciąg, komórka wyświetla ją w etykietce narzędzia.</span><span class="sxs-lookup"><span data-stu-id="b28b0-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="b28b0-107">Domyślnie użytkownicy mogą przeciągać podziały wierszy, kolumn i nagłówków za pomocą myszy, aby wyświetlić więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b28b0-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="b28b0-108">Użytkownicy mogą również dwukrotnie kliknąć dzielnik, aby automatycznie zmienić rozmiar skojarzonego wiersza, kolumny lub pasma nagłówka na podstawie jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="b28b0-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="b28b0-109">Kontrolka `DataGridView` zawiera właściwości, metody i zdarzenia umożliwiające dostosowanie lub wyłączenie wszystkich zachowań ukierunkowanych na użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b28b0-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="b28b0-110">Ponadto można programistycznie zmienić rozmiar wierszy, kolumn i nagłówków, aby dopasować ich zawartość, lub można je skonfigurować tak, aby zmieniały się automatycznie po zmianie ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="b28b0-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="b28b0-111">Możesz również skonfigurować kolumny, aby automatycznie dzielić dostępną szerokość formantu w proporcjach, które określisz.</span><span class="sxs-lookup"><span data-stu-id="b28b0-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b28b0-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b28b0-112">In This Section</span></span>  
 [<span data-ttu-id="b28b0-113">Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b28b0-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b28b0-114">Opisuje opcje ustalania rozmiarów wierszy, kolumn i nagłówków.</span><span class="sxs-lookup"><span data-stu-id="b28b0-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="b28b0-115">Ponadto zawiera szczegółowe informacje dotyczące właściwości i metod związanych z wymiarami oraz opisuje typowe scenariusze użycia.</span><span class="sxs-lookup"><span data-stu-id="b28b0-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="b28b0-116">Tryb wypełniania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b28b0-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b28b0-117">Opisuje tryb wypełniania kolumn szczegółowo i zawiera kod demonstracyjny, którego można użyć do eksperymentowania z trybem wypełniania kolumn i innymi trybami.</span><span class="sxs-lookup"><span data-stu-id="b28b0-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="b28b0-118">Instrukcje: ustawianie trybów zmieniania rozmiaru kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b28b0-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b28b0-119">Opisuje sposób konfigurowania trybów ustalania rozmiarów w typowych celach.</span><span class="sxs-lookup"><span data-stu-id="b28b0-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="b28b0-120">Instrukcje: zmienianie w sposób programowy rozmiaru komórek w celu dopasowania do zawartości w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b28b0-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="b28b0-121">Zawiera kod demonstracyjny, którego można użyć do eksperymentowania z programistyczną zmianą rozmiarów.</span><span class="sxs-lookup"><span data-stu-id="b28b0-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="b28b0-122">Instrukcje: automatyczne zmienianie rozmiaru komórek przy zmianie zawartości w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b28b0-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="b28b0-123">Zawiera kod demonstracyjny, którego można użyć do eksperymentowania z trybami automatycznego ustalania rozmiarów.</span><span class="sxs-lookup"><span data-stu-id="b28b0-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b28b0-124">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="b28b0-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="b28b0-125">Zawiera dokumentację referencyjną dla kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="b28b0-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b28b0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b28b0-126">See also</span></span>

- [<span data-ttu-id="b28b0-127">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="b28b0-127">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
