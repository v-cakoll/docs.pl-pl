---
title: 'Instrukcje: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource'
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
ms.openlocfilehash: 19505c690728147d2a67c26371e1cea4c281ab08
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154873"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="2ace4-102">Instrukcje: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource</span><span class="sxs-lookup"><span data-stu-id="2ace4-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="2ace4-103">Dane mogą łatwo udostępniać w wielu formularzach za <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="2ace4-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="2ace4-104">Na przykład można wyświetlić jeden formularz tylko do odczytu, który podsumowuje dane źródło danych i innym edytowalnego formularza, który zawiera szczegółowe informacje dotyczące aktualnie wybranego elementu w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="2ace4-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="2ace4-105">Ten przykład pokazuje, w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="2ace4-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ace4-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ace4-106">Example</span></span>  
 <span data-ttu-id="2ace4-107">Poniższy przykład kodu demonstruje sposób udostępniania <xref:System.Windows.Forms.BindingSource> i jego danych powiązanych w wielu formularzach.</span><span class="sxs-lookup"><span data-stu-id="2ace4-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="2ace4-108">W tym przykładzie wspólnie <xref:System.Windows.Forms.BindingSource> jest przekazywany do konstruktora formularza podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2ace4-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="2ace4-109">Formularz podrzędny umożliwia użytkownikowi edytowanie danych dla aktualnie wybranego elementu w formularzu głównym.</span><span class="sxs-lookup"><span data-stu-id="2ace4-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ace4-110"><xref:System.Windows.Forms.BindingSource.BindingComplete> Zdarzenie <xref:System.Windows.Forms.BindingSource> składnika odbywa się w przykładzie, aby upewnić się, że dwie formy pozostają zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="2ace4-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="2ace4-111">Aby uzyskać więcej informacji na temat przyczyn jest to zrobić, zobacz [jak: Upewnij się, wiele formantów powiązanych z tym samym źródłem danych pozostają zsynchronizowane](../multiple-controls-bound-to-data-source-synchronized.md).</span><span class="sxs-lookup"><span data-stu-id="2ace4-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ace4-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2ace4-112">Compiling the Code</span></span>  
 <span data-ttu-id="2ace4-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="2ace4-113">This example requires:</span></span>  
  
-   <span data-ttu-id="2ace4-114">Odwołania do zestawów systemu, przestrzeń nazw System.Windows.Forms, System.Drawing, dane systemowe i System.Xml.</span><span class="sxs-lookup"><span data-stu-id="2ace4-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="2ace4-115">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2ace4-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2ace4-116">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="2ace4-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ace4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ace4-117">See also</span></span>

- [<span data-ttu-id="2ace4-118">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="2ace4-118">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="2ace4-119">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ace4-119">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="2ace4-120">Instrukcje: Obsługa błędów i wyjątków występujących za powodu powiązania danych</span><span class="sxs-lookup"><span data-stu-id="2ace4-120">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
