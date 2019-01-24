---
title: 'Instrukcje: Powiązywanie kontrolek formularzy Windows Forms bazy danych DBNull'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: b2a5c7234d2815da734ee291fef223f20744b81e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658133"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="e6e72-102">Instrukcje: Powiązywanie kontrolek formularzy Windows Forms bazy danych DBNull</span><span class="sxs-lookup"><span data-stu-id="e6e72-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="e6e72-103">Po powiązaniu kontrolek formularzy Windows Forms do źródła danych i źródła danych zwraca <xref:System.DBNull> wartość odpowiednią wartość można zastąpić bez obsługi, formatowanie i analizowanie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e6e72-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="e6e72-104"><xref:System.Windows.Forms.Binding.NullValue%2A> Przekonwertuje właściwość <xref:System.DBNull> podanemu obiektowi podczas formatowania lub analizowania wartości źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e6e72-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6e72-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6e72-105">Example</span></span>  
 <span data-ttu-id="e6e72-106">Poniższy przykład pokazuje jak powiązać <xref:System.DBNull> wartości w dwóch różnych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="e6e72-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="e6e72-107">Pierwszy pokazuje, jak ustawić <xref:System.Windows.Forms.Binding.NullValue%2A> dla właściwości ciągu; drugi pokazuje, jak ustawić <xref:System.Windows.Forms.Binding.NullValue%2A> właściwości obrazu.</span><span class="sxs-lookup"><span data-stu-id="e6e72-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="e6e72-108">Typy właściwości powiązanej i <xref:System.Windows.Forms.Binding.NullValue%2A> właściwości musi być taka sama lub spowoduje błąd żadnych dalszych <xref:System.Windows.Forms.Binding.NullValue%2A> wartości zostaną przetworzone.</span><span class="sxs-lookup"><span data-stu-id="e6e72-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="e6e72-109">W takiej sytuacji nie zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e6e72-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e6e72-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e6e72-110">Compiling the Code</span></span>  
 <span data-ttu-id="e6e72-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e6e72-111">This example requires:</span></span>  
  
-   <span data-ttu-id="e6e72-112">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="e6e72-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="e6e72-113">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e6e72-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="e6e72-114">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="e6e72-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="e6e72-115">Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e6e72-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e72-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6e72-116">See also</span></span>
- [<span data-ttu-id="e6e72-117">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="e6e72-117">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [<span data-ttu-id="e6e72-118">Instrukcje: Obsługa błędów i wyjątków występujących za powodu powiązania danych</span><span class="sxs-lookup"><span data-stu-id="e6e72-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="e6e72-119">Instrukcje: Powiązanie z typem formantu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6e72-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
