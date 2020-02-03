---
title: Dostrajanie wydajności w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 77ad86c4cd606bcf074473c97371ec27bcc5605b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744278"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="45f6b-102">Dostrajanie wydajności w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="45f6b-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="45f6b-103">Podczas pracy z dużymi ilościami danych kontrolka `DataGridView` może zużywać dużą ilość pamięci, chyba że jest używana uważnie.</span><span class="sxs-lookup"><span data-stu-id="45f6b-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="45f6b-104">Na klientach z ograniczoną ilością pamięci można uniknąć niektórych obciążeń, unikając funkcji mających koszt dużej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="45f6b-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="45f6b-105">Możesz również zarządzać niektórymi lub wszystkimi zadaniami konserwacji i pobierania danych samodzielnie przy użyciu trybu wirtualnego, aby dostosować użycie pamięci dla danego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="45f6b-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45f6b-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="45f6b-106">In This Section</span></span>  
 [<span data-ttu-id="45f6b-107">Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45f6b-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="45f6b-108">Opisuje sposób używania kontrolki `DataGridView` w sposób, który pozwala uniknąć niepotrzebnego użycia pamięci i kar wydajności podczas pracy z dużymi ilościami danych.</span><span class="sxs-lookup"><span data-stu-id="45f6b-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="45f6b-109">Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45f6b-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="45f6b-110">Opisuje, jak używać trybu wirtualnego do uzupełniania lub zastępowania standardowego mechanizmu powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="45f6b-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="45f6b-111">Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45f6b-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="45f6b-112">Opisuje sposób wdrażania programów obsługi dla kilku zdarzeń w trybie wirtualnym.</span><span class="sxs-lookup"><span data-stu-id="45f6b-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="45f6b-113">Ilustruje także sposób implementacji wycofywania i zatwierdzania na poziomie wierszy na potrzeby edycji użytkowników.</span><span class="sxs-lookup"><span data-stu-id="45f6b-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="45f6b-114">Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45f6b-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="45f6b-115">Opisuje sposób ładowania danych na żądanie, co jest przydatne, gdy masz więcej danych do wyświetlenia niż dostępna pamięć klienta może być przechowywana.</span><span class="sxs-lookup"><span data-stu-id="45f6b-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="45f6b-116">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="45f6b-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="45f6b-117">Zawiera dokumentację referencyjną dla kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="45f6b-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="45f6b-118">Zawiera dokumentację referencyjną dla właściwości <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="45f6b-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f6b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45f6b-119">See also</span></span>

- [<span data-ttu-id="45f6b-120">DataGridView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="45f6b-120">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="45f6b-121">Tryby wyświetlania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="45f6b-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
