---
title: Zmiana rozmiaru wierszy i kolumn w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: e1fa2d57cfb2cd374d691fe03a0e0bdbd3ad7141
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138115"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="19b60-102">Zmiana rozmiaru wierszy i kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="19b60-102">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="19b60-103">`DataGridView` Control oferuje wiele opcji dostosowywania zachowania zmiany rozmiaru wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="19b60-103">The `DataGridView` control provides numerous options for customizing the sizing behavior of its columns and rows.</span></span> <span data-ttu-id="19b60-104">Zazwyczaj `DataGridView` komórki nie można zmieniać rozmiaru na podstawie ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="19b60-104">Typically, `DataGridView` cells do not resize based on their contents.</span></span> <span data-ttu-id="19b60-105">Zamiast tego one Przytnij wszystkie wartości wyświetlania, która jest większa niż komórki.</span><span class="sxs-lookup"><span data-stu-id="19b60-105">Instead, they clip any display value that is larger than the cell.</span></span> <span data-ttu-id="19b60-106">Jeśli zawartość mogą być wyświetlane w postaci ciągu, komórki wyświetla je w etykietce narzędzia.</span><span class="sxs-lookup"><span data-stu-id="19b60-106">If the content can be displayed as a string, the cell displays it in a ToolTip.</span></span>  
  
 <span data-ttu-id="19b60-107">Domyślnie użytkownicy można przeciągnąć wierszy, kolumny i separatorów nagłówka myszą, aby wyświetlić więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="19b60-107">By default, users can drag row, column, and header dividers with the mouse to show more information.</span></span> <span data-ttu-id="19b60-108">Użytkownicy mogą także kliknąć dwukrotnie separator automatycznie Zmień rozmiar skojarzone grupy wierszy, kolumny lub nagłówek, na podstawie jego zawartości.</span><span class="sxs-lookup"><span data-stu-id="19b60-108">Users can also double-click a divider to automatically resize the associated row, column, or header band based on its contents.</span></span>  
  
 <span data-ttu-id="19b60-109">`DataGridView` Kontrola udostępnia właściwości, metody i zdarzenia, które pozwalają dostosować lub wyłączyć wszystkie te zachowania przekierowanie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="19b60-109">The `DataGridView` control provides properties, methods, and events that enable you to customize or disable all of these user-directed behaviors.</span></span> <span data-ttu-id="19b60-110">Ponadto możesz programowo zmienić rozmiar wiersze, kolumny i nagłówki, aby zmieścić ich zawartość lub można skonfigurować je, aby automatycznie zmieniać wielkość po każdym wprowadzeniu zmiany ich zawartość.</span><span class="sxs-lookup"><span data-stu-id="19b60-110">Additionally, you can programmatically resize rows, columns, and headers to fit their contents, or you can configure them to automatically resize themselves whenever their contents change.</span></span> <span data-ttu-id="19b60-111">Można również skonfigurować kolumny do automatycznego dzielenia dostępne szerokość formantu w proporcjach, które określisz.</span><span class="sxs-lookup"><span data-stu-id="19b60-111">You can also configure columns to automatically divide the available width of the control in proportions that you specify.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19b60-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="19b60-112">In This Section</span></span>  
 [<span data-ttu-id="19b60-113">Opcje ustalania rozmiaru w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19b60-113">Sizing Options in the Windows Forms DataGridView Control</span></span>](sizing-options-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="19b60-114">W tym artykule opisano opcje ustalania rozmiaru wiersze, kolumny i nagłówki.</span><span class="sxs-lookup"><span data-stu-id="19b60-114">Describes the options for sizing rows, columns, and headers.</span></span> <span data-ttu-id="19b60-115">Ponadto zawiera szczegółowe informacje dotyczące ustalania rozmiaru właściwości i metody i w tym artykule opisano typowe scenariusze użycia.</span><span class="sxs-lookup"><span data-stu-id="19b60-115">Also provides details on sizing-related properties and methods, and describes common usage scenarios.</span></span>  
  
 [<span data-ttu-id="19b60-116">Tryb wypełniania kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19b60-116">Column Fill Mode in the Windows Forms DataGridView Control</span></span>](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="19b60-117">W tym artykule opisano tryb wypełniania kolumny szczegółowo i zawiera kod demonstracji, który służy do eksperymentowania z innych trybach i tryb wypełniania kolumny.</span><span class="sxs-lookup"><span data-stu-id="19b60-117">Describes column fill mode in detail, and provides demonstration code that you can use to experiment with column fill mode and other modes.</span></span>  
  
 [<span data-ttu-id="19b60-118">Instrukcje: Ustawianie trybów zmieniania rozmiaru kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19b60-118">How to: Set the Sizing Modes of the Windows Forms DataGridView Control</span></span>](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="19b60-119">W tym artykule opisano sposób konfigurowania trybów zmieniania rozmiaru dla wspólnych celów.</span><span class="sxs-lookup"><span data-stu-id="19b60-119">Describes how to configure the sizing modes for common purposes.</span></span>  
  
 [<span data-ttu-id="19b60-120">Instrukcje: Programowe zmienianie rozmiaru komórek w celu dopasowania do zawartości w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19b60-120">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 <span data-ttu-id="19b60-121">Zawiera kod demonstracji, który służy do eksperymentowania z programowe Zmienianie rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="19b60-121">Provides demonstration code that you can use to experiment with programmatic resizing.</span></span>  
  
 [<span data-ttu-id="19b60-122">Instrukcje: Automatycznie zmienia rozmiar komórek, gdy zmienia się zawartość w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19b60-122">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 <span data-ttu-id="19b60-123">Zawiera kod demonstracji, który służy do eksperymentowania z trybów automatycznej zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="19b60-123">Provides demonstration code that you can use to experiment with automatic sizing modes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="19b60-124">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="19b60-124">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="19b60-125">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="19b60-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b60-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19b60-126">See also</span></span>

- [<span data-ttu-id="19b60-127">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="19b60-127">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
