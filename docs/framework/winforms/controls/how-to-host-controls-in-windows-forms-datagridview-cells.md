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
ms.openlocfilehash: 008b6da56c3428d0edcc44778b4d3bef1a52c443
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59194204"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="80d91-102">Instrukcje: kontrolki hosta w komórkach DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="80d91-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="80d91-103"><xref:System.Windows.Forms.DataGridView> Control oferuje kilka typów kolumn, aby umożliwić użytkownikom wprowadzanie i edytowanie wartości w na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="80d91-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="80d91-104">Te typy kolumn nie odpowiadają Twoim potrzebom wprowadzanie danych, można jednak utworzyć swój własny typ kolumny, wraz z komórkami, które hostują formantów wybrane.</span><span class="sxs-lookup"><span data-stu-id="80d91-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="80d91-105">Aby to zrobić, należy zdefiniować klas, które wynikają z <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="80d91-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="80d91-106">Należy także zdefiniować klasę, która pochodzi od klasy <xref:System.Windows.Forms.Control> i implementuje <xref:System.Windows.Forms.IDataGridViewEditingControl> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="80d91-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="80d91-107">Poniższy przykład kodu pokazuje sposób tworzenia kolumny kalendarza.</span><span class="sxs-lookup"><span data-stu-id="80d91-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="80d91-108">Komórki w tej kolumnie wyświetlanie dat w komórkach pola zwykły tekst, ale w przypadku, gdy użytkownik edytuje komórkę, <xref:System.Windows.Forms.DateTimePicker> formant jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="80d91-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="80d91-109">Aby uniknąć konieczności implementowania funkcji wyświetlania pola tekstowego ponownie `CalendarCell` klasa pochodzi od <xref:System.Windows.Forms.DataGridViewTextBoxCell> klasy, a nie dziedziczy <xref:System.Windows.Forms.DataGridViewCell> klasy bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="80d91-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80d91-110">Po utworzeniu klasy pochodnej z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodać nowe właściwości do klasy pochodnej, pamiętaj zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas operacji klonowania.</span><span class="sxs-lookup"><span data-stu-id="80d91-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="80d91-111">Należy także wywołać klasy bazowej `Clone` metody, aby właściwości klasy bazowej są kopiowane do nowej komórce lub kolumnie.</span><span class="sxs-lookup"><span data-stu-id="80d91-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80d91-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="80d91-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="80d91-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="80d91-113">Compiling the Code</span></span>  
 <span data-ttu-id="80d91-114">Poniższy przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="80d91-114">The following example requires:</span></span>  
  
-   <span data-ttu-id="80d91-115">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="80d91-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="80d91-116">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="80d91-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="80d91-117">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="80d91-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d91-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80d91-118">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>
- <xref:System.Windows.Forms.IDataGridViewEditingControl>
- <xref:System.Windows.Forms.DateTimePicker>
- [<span data-ttu-id="80d91-119">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80d91-119">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="80d91-120">DataGridView, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="80d91-120">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="80d91-121">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="80d91-121">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
