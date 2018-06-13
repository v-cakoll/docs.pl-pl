---
title: 'Porady: wyświetlanie godziny za pomocą formantu DateTimePicker'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: 16e09225c9447f9ec8be3b658ac0ed1aa3b2edab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531833"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="05293-102">Porady: wyświetlanie godziny za pomocą formantu DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="05293-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="05293-103">Jeśli mają aplikację, aby umożliwić użytkownikom wybierz datę i godzinę, a do wyświetlenia daty i godziny w określonym formacie, użyj <xref:System.Windows.Forms.DateTimePicker> formantu.</span><span class="sxs-lookup"><span data-stu-id="05293-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="05293-104">Poniższa procedura przedstawia sposób użycia <xref:System.Windows.Forms.DateTimePicker> sterowania, aby wyświetlić godzinę.</span><span class="sxs-lookup"><span data-stu-id="05293-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="05293-105">Aby wyświetlić godzinę za pomocą formantu DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="05293-105">To display the time with the DateTimePicker control</span></span>  
  
1.  <span data-ttu-id="05293-106">Ustaw <xref:System.Windows.Forms.DateTimePicker.Format%2A> właściwości <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="05293-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="05293-107">Ustaw <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> właściwość <xref:System.Windows.Forms.DateTimePicker> do `true`.</span><span class="sxs-lookup"><span data-stu-id="05293-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="05293-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="05293-108">Example</span></span>  
 <span data-ttu-id="05293-109">Poniższy przykładowy kod przedstawia sposób tworzenia <xref:System.Windows.Forms.DateTimePicker> , umożliwia użytkownikom wybór tylko raz.</span><span class="sxs-lookup"><span data-stu-id="05293-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="05293-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="05293-110">Compiling the Code</span></span>  
 <span data-ttu-id="05293-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="05293-111">This example requires:</span></span>  
  
-   <span data-ttu-id="05293-112">Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="05293-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="05293-113">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="05293-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="05293-114">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="05293-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="05293-115">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="05293-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05293-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05293-116">See Also</span></span>  
 [<span data-ttu-id="05293-117">DateTimePicker, kontrolka</span><span class="sxs-lookup"><span data-stu-id="05293-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)
