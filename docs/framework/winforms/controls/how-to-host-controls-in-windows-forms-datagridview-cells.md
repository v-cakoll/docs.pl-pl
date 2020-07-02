---
title: Kontrolki hosta w komórkach DataGridView
description: Dowiedz się, jak hostować kontrolki w Windows Forms komórkach DataGridView, aby umożliwić użytkownikom wprowadzanie i edytowanie wartości na różne sposoby.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 87901cbf86689bec49f5692feeabdae79f6b93ba
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619549"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="6226c-103">Porady: formanty hosta w komórkach DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6226c-103">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="6226c-104"><xref:System.Windows.Forms.DataGridView>Formant zawiera kilka typów kolumn, umożliwiając użytkownikom wprowadzanie i edytowanie wartości na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="6226c-104">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="6226c-105">Jeśli te typy kolumn nie spełniają wymagań związanych z wprowadzaniem danych, można jednak utworzyć własne typy kolumn z komórkami, które obsługują wybrane przez siebie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="6226c-105">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="6226c-106">Aby to zrobić, należy zdefiniować klasy, które pochodzą z <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewCell> .</span><span class="sxs-lookup"><span data-stu-id="6226c-106">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="6226c-107">Należy również zdefiniować klasę, która dziedziczy z <xref:System.Windows.Forms.Control> i implementuje <xref:System.Windows.Forms.IDataGridViewEditingControl> interfejs.</span><span class="sxs-lookup"><span data-stu-id="6226c-107">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="6226c-108">Poniższy przykład kodu pokazuje, jak utworzyć kolumnę kalendarza.</span><span class="sxs-lookup"><span data-stu-id="6226c-108">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="6226c-109">Komórki tej kolumny wyświetlają daty w zwykłych komórkach pól tekstowych, ale gdy użytkownik edytuje komórkę, <xref:System.Windows.Forms.DateTimePicker> zostanie wyświetlony formant.</span><span class="sxs-lookup"><span data-stu-id="6226c-109">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="6226c-110">Aby uniknąć konieczności ponownego wdrożenia funkcji wyświetlania pól tekstowych, `CalendarCell` Klasa pochodzi od <xref:System.Windows.Forms.DataGridViewTextBoxCell> klasy, a nie dziedziczy <xref:System.Windows.Forms.DataGridViewCell> bezpośrednio klasy.</span><span class="sxs-lookup"><span data-stu-id="6226c-110">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6226c-111">Gdy pochodzą z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodajesz nowe właściwości do klasy pochodnej, pamiętaj, aby zastąpić metodę, `Clone` Aby skopiować nowe właściwości podczas klonowania operacji.</span><span class="sxs-lookup"><span data-stu-id="6226c-111">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="6226c-112">Należy również wywołać metodę klasy bazowej, `Clone` Aby właściwości klasy bazowej były kopiowane do nowej komórki lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="6226c-112">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6226c-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="6226c-113">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6226c-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6226c-114">Compiling the Code</span></span>  
 <span data-ttu-id="6226c-115">Poniższy przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6226c-115">The following example requires:</span></span>  
  
- <span data-ttu-id="6226c-116">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="6226c-116">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6226c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6226c-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="6226c-118">Dostosowywanie formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6226c-118">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6226c-119">DataGridView, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="6226c-119">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="6226c-120">Typy kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6226c-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
