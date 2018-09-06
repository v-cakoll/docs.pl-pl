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
ms.openlocfilehash: c65a1102ccb8b05602d813831745dbcefed8c17d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879240"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="4b0fe-102">Porady: wyświetlanie godziny za pomocą formantu DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="4b0fe-102">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="4b0fe-103">Jeśli chcesz, aby umożliwić użytkownikom wybranie daty i godziny, do wyświetlenia tej daty i godziny w określonym formacie, należy użyć aplikacji <xref:System.Windows.Forms.DateTimePicker> kontroli.</span><span class="sxs-lookup"><span data-stu-id="4b0fe-103">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="4b0fe-104">Poniższa procedura przedstawia sposób użycia <xref:System.Windows.Forms.DateTimePicker> formantu, aby wyświetlić czas.</span><span class="sxs-lookup"><span data-stu-id="4b0fe-104">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="4b0fe-105">Aby wyświetlić czas za pomocą formantu DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="4b0fe-105">To display the time with the DateTimePicker control</span></span>  
  
1.  <span data-ttu-id="4b0fe-106">Ustaw <xref:System.Windows.Forms.DateTimePicker.Format%2A> właściwości <xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="4b0fe-106">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="4b0fe-107">Ustaw <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> właściwość <xref:System.Windows.Forms.DateTimePicker> do `true`.</span><span class="sxs-lookup"><span data-stu-id="4b0fe-107">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="4b0fe-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b0fe-108">Example</span></span>  
 <span data-ttu-id="4b0fe-109">Poniższy przykładowy kod przedstawia sposób tworzenia <xref:System.Windows.Forms.DateTimePicker> który umożliwia użytkownikom wybranie tylko raz.</span><span class="sxs-lookup"><span data-stu-id="4b0fe-109">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b0fe-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4b0fe-110">Compiling the Code</span></span>  
 <span data-ttu-id="4b0fe-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4b0fe-111">This example requires:</span></span>  
  
-   <span data-ttu-id="4b0fe-112">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="4b0fe-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="4b0fe-113">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4b0fe-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4b0fe-114">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="4b0fe-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="4b0fe-115">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="4b0fe-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b0fe-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b0fe-116">See Also</span></span>  
 [<span data-ttu-id="4b0fe-117">DateTimePicker, kontrolka</span><span class="sxs-lookup"><span data-stu-id="4b0fe-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)
