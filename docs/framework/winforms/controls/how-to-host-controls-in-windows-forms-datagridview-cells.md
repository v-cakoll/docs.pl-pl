---
title: 'Instrukcje: kontrolki hosta w komórkach DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: a97af9bf0ef4016e54f877d934ed401b8dde7d4e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966605"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="ecec0-102">Instrukcje: kontrolki hosta w komórkach DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ecec0-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="ecec0-103"><xref:System.Windows.Forms.DataGridView> Formant zawiera kilka typów kolumn, umożliwiając użytkownikom wprowadzanie i edytowanie wartości na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="ecec0-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="ecec0-104">Jeśli te typy kolumn nie spełniają wymagań związanych z wprowadzaniem danych, można jednak utworzyć własne typy kolumn z komórkami, które obsługują wybrane przez siebie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ecec0-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="ecec0-105">Aby to zrobić, należy zdefiniować klasy, które pochodzą z <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="ecec0-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="ecec0-106">Należy również zdefiniować klasę, która dziedziczy z <xref:System.Windows.Forms.Control> i <xref:System.Windows.Forms.IDataGridViewEditingControl> implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="ecec0-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="ecec0-107">Poniższy przykład kodu pokazuje, jak utworzyć kolumnę kalendarza.</span><span class="sxs-lookup"><span data-stu-id="ecec0-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="ecec0-108">Komórki tej kolumny wyświetlają daty w zwykłych komórkach pól tekstowych, ale gdy użytkownik edytuje komórkę, <xref:System.Windows.Forms.DateTimePicker> zostanie wyświetlony formant.</span><span class="sxs-lookup"><span data-stu-id="ecec0-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="ecec0-109">Aby uniknąć konieczności ponownego wdrożenia funkcji wyświetlania pól tekstowych, `CalendarCell` Klasa pochodzi <xref:System.Windows.Forms.DataGridViewTextBoxCell> od klasy, <xref:System.Windows.Forms.DataGridViewCell> a nie dziedziczy bezpośrednio klasy.</span><span class="sxs-lookup"><span data-stu-id="ecec0-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecec0-110">Gdy pochodzą z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodajesz nowe właściwości do klasy pochodnej, pamiętaj, aby zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas klonowania operacji.</span><span class="sxs-lookup"><span data-stu-id="ecec0-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="ecec0-111">Należy również wywołać `Clone` metodę klasy bazowej, aby właściwości klasy bazowej były kopiowane do nowej komórki lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="ecec0-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecec0-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="ecec0-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ecec0-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ecec0-113">Compiling the Code</span></span>  
 <span data-ttu-id="ecec0-114">Poniższy przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ecec0-114">The following example requires:</span></span>  
  
- <span data-ttu-id="ecec0-115">Odwołania do zestawów system i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="ecec0-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecec0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecec0-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="ecec0-117">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ecec0-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="ecec0-118">DataGridView, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="ecec0-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="ecec0-119">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ecec0-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
