---
title: 'Porady: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: a0c68372301d984fc388f37a5ce798cbf99d802b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536595"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="aefb0-102">Porady: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource</span><span class="sxs-lookup"><span data-stu-id="aefb0-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="aefb0-103">Dane można łatwo udostępniać wielu formularzach za pomocą <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="aefb0-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="aefb0-104">Na przykład można wyświetlić jeden formularz tylko do odczytu, który znajduje się podsumowanie danych źródła danych oraz innej formy można edytować, który zawiera szczegółowe informacje dotyczące aktualnie wybranego elementu w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="aefb0-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="aefb0-105">W tym przykładzie pokazano, w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="aefb0-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aefb0-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="aefb0-106">Example</span></span>  
 <span data-ttu-id="aefb0-107">W poniższym przykładzie pokazano, jak udostępnić <xref:System.Windows.Forms.BindingSource> i jego danych powiązanych w wielu formularzach.</span><span class="sxs-lookup"><span data-stu-id="aefb0-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="aefb0-108">W tym przykładzie udostępnionego <xref:System.Windows.Forms.BindingSource> jest przekazany do konstruktora formularza podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="aefb0-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="aefb0-109">Formularz podrzędny umożliwia użytkownikowi edytowanie danych dla aktualnie wybranego elementu w formularzu głównym.</span><span class="sxs-lookup"><span data-stu-id="aefb0-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aefb0-110"><xref:System.Windows.Forms.BindingSource.BindingComplete> Zdarzenia dla <xref:System.Windows.Forms.BindingSource> składnika jest obsługiwany w tym przykładzie, aby upewnić się, że dwa formularze pozostają zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="aefb0-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="aefb0-111">Aby uzyskać więcej informacji na temat przyczyn jest to zrobić, zobacz [porady: Upewnij się, wiele formanty powiązane z tym samym dane źródła pozostają zsynchronizowane](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span><span class="sxs-lookup"><span data-stu-id="aefb0-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="aefb0-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="aefb0-112">Compiling the Code</span></span>  
 <span data-ttu-id="aefb0-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="aefb0-113">This example requires:</span></span>  
  
-   <span data-ttu-id="aefb0-114">Odwołania do zestawów systemu, System.Windows.Forms System.Drawing, dane systemowe i zestawów System.Xml.</span><span class="sxs-lookup"><span data-stu-id="aefb0-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="aefb0-115">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="aefb0-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="aefb0-116">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="aefb0-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="aefb0-117">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="aefb0-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefb0-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aefb0-118">See Also</span></span>  
 [<span data-ttu-id="aefb0-119">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="aefb0-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="aefb0-120">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aefb0-120">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="aefb0-121">Instrukcje: obsługa błędów i wyjątków występujących za powodu powiązania danych</span><span class="sxs-lookup"><span data-stu-id="aefb0-121">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
