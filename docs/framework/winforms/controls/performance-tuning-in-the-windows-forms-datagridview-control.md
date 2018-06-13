---
title: Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 97bf6f36ce029f879c3524fa92df08a483c2cb77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536985"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9e203-102">Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9e203-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9e203-103">Podczas pracy z dużą ilością danych, `DataGridView` kontroli może używać dużej ilości pamięci w obciążenie, chyba że ostrożnie korzystaj.</span><span class="sxs-lookup"><span data-stu-id="9e203-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="9e203-104">Na komputerach klienckich z ograniczoną pamięcią można uniknąć niektórych ten narzut, unikając funkcje, które mają pamięci wysokiej kosztów.</span><span class="sxs-lookup"><span data-stu-id="9e203-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="9e203-105">Można również zarządzać niektórych lub wszystkich danych konserwacji i pobieranie zadań samodzielnie przy użyciu trybu wirtualnego w celu dostosowania użycia pamięci dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="9e203-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e203-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9e203-106">In This Section</span></span>  
 [<span data-ttu-id="9e203-107">Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e203-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9e203-108">Informacje dotyczące używania `DataGridView` formantu w taki sposób, aby uniknąć kar użycia i wydajności pamięci niepotrzebnych podczas pracy z dużą ilością danych.</span><span class="sxs-lookup"><span data-stu-id="9e203-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="9e203-109">Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e203-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9e203-110">Informacje dotyczące używania trybu wirtualnego do uzupełnienia lub zastąpienia standardowego mechanizmu powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="9e203-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="9e203-111">Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e203-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="9e203-112">Opisuje sposób wdrożenia obsługi kilka zdarzeń w trybie wirtualnym.</span><span class="sxs-lookup"><span data-stu-id="9e203-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="9e203-113">Również przedstawiono sposób wykonania wycofywania na poziomie wiersza i zatwierdzenie dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9e203-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="9e203-114">Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e203-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="9e203-115">Opisuje sposób ładowania danych na żądanie, co jest przydatne, jeśli masz więcej danych do wyświetlenia nie mogą być przechowywane w pamięci dostępne klienta.</span><span class="sxs-lookup"><span data-stu-id="9e203-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9e203-116">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="9e203-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="9e203-117">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="9e203-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="9e203-118">Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9e203-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e203-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e203-119">See Also</span></span>  
 [<span data-ttu-id="9e203-120">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="9e203-120">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="9e203-121">Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e203-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
