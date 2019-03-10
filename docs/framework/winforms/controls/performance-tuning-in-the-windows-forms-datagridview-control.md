---
title: Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: d425488adb8569a48333de4f8c0312143029fbe0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703178"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="b0b25-102">Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b0b25-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b0b25-103">Podczas pracy z dużymi ilościami danych, `DataGridView` kontroli może zużywać dużą ilość pamięci w koszty, chyba że ostrożne korzystanie.</span><span class="sxs-lookup"><span data-stu-id="b0b25-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="b0b25-104">Na komputerach klienckich z ograniczoną ilością pamięci można uniknąć niektórych to obciążenie, unikając funkcje, które mają dużą ilość pamięci, kosztów.</span><span class="sxs-lookup"><span data-stu-id="b0b25-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="b0b25-105">Można również zarządzać niektórych lub wszystkich funkcji obsługi danych i pobierania zadania samodzielnie przy użyciu trybu wirtualnego w celu dostosowania użycia pamięci dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="b0b25-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0b25-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b0b25-106">In This Section</span></span>  
 [<span data-ttu-id="b0b25-107">Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0b25-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b0b25-108">Opisuje sposób używania `DataGridView` formantu w taki sposób, aby uniknąć kar pamięci niepotrzebne użycia i wydajności, podczas pracy z dużymi ilościami danych.</span><span class="sxs-lookup"><span data-stu-id="b0b25-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="b0b25-109">Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0b25-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="b0b25-110">W tym artykule opisano sposób użycia trybu wirtualnego w celu uzupełnienia lub zastąpienia standardowego mechanizmu wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="b0b25-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="b0b25-111">Przewodnik: Implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0b25-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="b0b25-112">W tym artykule opisano, jak zaimplementować obsługę dla kilku zdarzenia trybu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="b0b25-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="b0b25-113">Ilustruje też sposób wdrażać wycofywania na poziomie wiersza i zatwierdzenia do edycji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b0b25-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="b0b25-114">Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0b25-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="b0b25-115">W tym artykule opisano sposób ładowania danych na żądanie, co jest przydatne, jeśli masz więcej danych do wyświetlenia, nie mogą być przechowywane w pamięci dostępne klienta.</span><span class="sxs-lookup"><span data-stu-id="b0b25-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b0b25-116">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="b0b25-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="b0b25-117">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b0b25-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="b0b25-118">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0b25-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0b25-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0b25-119">See also</span></span>
- [<span data-ttu-id="b0b25-120">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="b0b25-120">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="b0b25-121">Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b0b25-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
