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
ms.openlocfilehash: 639ba51ee02f6ecbc82fae15abbd699d1168ae3e
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219116"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="01457-102">Instrukcje: Powiązywanie kontrolek formularzy Windows Forms bazy danych DBNull</span><span class="sxs-lookup"><span data-stu-id="01457-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="01457-103">Po powiązaniu kontrolek formularzy Windows Forms do źródła danych i źródła danych zwraca <xref:System.DBNull> wartość odpowiednią wartość można zastąpić bez obsługi, formatowanie i analizowanie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="01457-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="01457-104"><xref:System.Windows.Forms.Binding.NullValue%2A> Przekonwertuje właściwość <xref:System.DBNull> podanemu obiektowi podczas formatowania lub analizowania wartości źródła danych.</span><span class="sxs-lookup"><span data-stu-id="01457-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01457-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="01457-105">Example</span></span>  
 <span data-ttu-id="01457-106">Poniższy przykład pokazuje jak powiązać <xref:System.DBNull> wartości w dwóch różnych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="01457-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="01457-107">Pierwszy pokazuje, jak ustawić <xref:System.Windows.Forms.Binding.NullValue%2A> dla właściwości ciągu; drugi pokazuje, jak ustawić <xref:System.Windows.Forms.Binding.NullValue%2A> właściwości obrazu.</span><span class="sxs-lookup"><span data-stu-id="01457-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="01457-108">Typy właściwości powiązanej i <xref:System.Windows.Forms.Binding.NullValue%2A> właściwości musi być taka sama lub spowoduje błąd żadnych dalszych <xref:System.Windows.Forms.Binding.NullValue%2A> wartości zostaną przetworzone.</span><span class="sxs-lookup"><span data-stu-id="01457-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="01457-109">W takiej sytuacji nie zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="01457-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="01457-110">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="01457-110">Compiling the Code</span></span>  
 <span data-ttu-id="01457-111">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="01457-111">This example requires:</span></span>  
  
-   <span data-ttu-id="01457-112">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="01457-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="01457-113">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="01457-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="01457-114">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="01457-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01457-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01457-115">See also</span></span>
- [<span data-ttu-id="01457-116">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="01457-116">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [<span data-ttu-id="01457-117">Instrukcje: Obsługa błędów i wyjątków występujących za powodu powiązania danych</span><span class="sxs-lookup"><span data-stu-id="01457-117">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="01457-118">Instrukcje: Powiązanie z typem formantu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="01457-118">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
