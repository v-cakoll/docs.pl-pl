---
title: "Porady: kontrolki hosta w komórkach DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7fd74b54a4e8c91762a3f32c6c89877470c10960
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a><span data-ttu-id="6282e-102">Porady: kontrolki hosta w komórkach DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6282e-102">How to: Host Controls in Windows Forms DataGridView Cells</span></span>
<span data-ttu-id="6282e-103"><xref:System.Windows.Forms.DataGridView> Kontrola zapewnia kilka typów kolumn, aby umożliwić użytkownikom wprowadzanie i edytowanie wartości w różny sposób.</span><span class="sxs-lookup"><span data-stu-id="6282e-103">The <xref:System.Windows.Forms.DataGridView> control provides several column types, enabling your users to enter and edit values in a variety of ways.</span></span> <span data-ttu-id="6282e-104">Jeśli te typy kolumn nie spełniają potrzeb wprowadzania danych, można jednak utworzyć własnych typów kolumn z komórek obsługujących formanty wybrane.</span><span class="sxs-lookup"><span data-stu-id="6282e-104">If these column types do not meet your data-entry needs, however, you can create your own column types with cells that host controls of your choosing.</span></span> <span data-ttu-id="6282e-105">Aby to zrobić, należy zdefiniować klasy, które pochodzą z <xref:System.Windows.Forms.DataGridViewColumn> i <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="6282e-105">To do this, you must define classes that derive from <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewCell>.</span></span> <span data-ttu-id="6282e-106">Należy również zdefiniować klasą pochodzącą z <xref:System.Windows.Forms.Control> i implementuje <xref:System.Windows.Forms.IDataGridViewEditingControl> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6282e-106">You must also define a class that derives from <xref:System.Windows.Forms.Control> and implements the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
 <span data-ttu-id="6282e-107">Poniższy przykład kodu pokazuje, jak można utworzyć kolumny kalendarza.</span><span class="sxs-lookup"><span data-stu-id="6282e-107">The following code example shows how to create a calendar column.</span></span> <span data-ttu-id="6282e-108">Komórki w tej kolumnie wyświetlanie dat w komórkach pole zwykłego tekstu, ale, gdy użytkownik edytuje komórki, <xref:System.Windows.Forms.DateTimePicker> formant jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="6282e-108">The cells of this column display dates in ordinary text box cells, but when the user edits a cell, a <xref:System.Windows.Forms.DateTimePicker> control appears.</span></span> <span data-ttu-id="6282e-109">Aby uniknąć konieczności ponownego implementowania funkcji wyświetlania pola tekstowego `CalendarCell` pochodną klasy <xref:System.Windows.Forms.DataGridViewTextBoxCell> klasa dziedziczy <xref:System.Windows.Forms.DataGridViewCell> bezpośrednio klasa.</span><span class="sxs-lookup"><span data-stu-id="6282e-109">In order to avoid having to implement text box display functionality again, the `CalendarCell` class derives from the <xref:System.Windows.Forms.DataGridViewTextBoxCell> class rather than inheriting the <xref:System.Windows.Forms.DataGridViewCell> class directly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6282e-110">Jeśli pochodzi od <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodać nowe właściwości do klasy pochodnej, należy zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas operacji klonowania.</span><span class="sxs-lookup"><span data-stu-id="6282e-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="6282e-111">Należy także wywołać klasy podstawowej `Clone` metody, aby właściwości klasy podstawowej są kopiowane do nowej komórki lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="6282e-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6282e-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="6282e-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6282e-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6282e-113">Compiling the Code</span></span>  
 <span data-ttu-id="6282e-114">Poniższy przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6282e-114">The following example requires:</span></span>  
  
-   <span data-ttu-id="6282e-115">Odwołania do zestawów systemu i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="6282e-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="6282e-116">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6282e-116">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="6282e-117">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="6282e-117">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="6282e-118">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="6282e-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6282e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6282e-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <xref:System.Windows.Forms.DateTimePicker>  
 [<span data-ttu-id="6282e-120">Dostosowywanie formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6282e-120">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="6282e-121">DataGridView — architektura formantu</span><span class="sxs-lookup"><span data-stu-id="6282e-121">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [<span data-ttu-id="6282e-122">Typy kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6282e-122">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
