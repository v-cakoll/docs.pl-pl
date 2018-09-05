---
title: 'Porady: odzwierciedlanie aktualizacji źródła danych w formancie formularzy systemu Windows za pomocą elementu BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
ms.openlocfilehash: 95e17675011b7e4d628b980fc0cbf15a50ce3932
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554352"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a><span data-ttu-id="1d756-102">Porady: odzwierciedlanie aktualizacji źródła danych w formancie formularzy systemu Windows za pomocą elementu BindingSource</span><span class="sxs-lookup"><span data-stu-id="1d756-102">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>
<span data-ttu-id="1d756-103">Korzystając z formantów powiązanych z danymi, czasami konieczne reagowanie na zmiany w źródle danych, gdy źródło danych nie powoduje zmiany listy zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1d756-103">When you use data-bound controls, you sometimes have to respond to changes in the data source when the data source does not raise list-changed events.</span></span> <span data-ttu-id="1d756-104">Kiedy używasz <xref:System.Windows.Forms.BindingSource> składnika można powiązać źródła danych do kontrolki formularzy Windows może powiadomić kontrolkę źródle danych została zmieniona przez wywołanie metody <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> — metoda.</span><span class="sxs-lookup"><span data-stu-id="1d756-104">When you use the <xref:System.Windows.Forms.BindingSource> component to bind your data source to a Windows Forms control, you can notify the control that your data source has changed by calling the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d756-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d756-105">Example</span></span>  
 <span data-ttu-id="1d756-106">Poniższy przykład kodu demonstruje sposób użycia <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> metody powiadamianie powiązanego formantu o aktualizacji w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="1d756-106">The following code example demonstrates using the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method to notify a bound control about an update in the data source.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d756-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1d756-107">Compiling the Code</span></span>  
 <span data-ttu-id="1d756-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="1d756-108">This example requires:</span></span>  
  
-   <span data-ttu-id="1d756-109">Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1d756-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1d756-110">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1d756-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1d756-111">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="1d756-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="1d756-112">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1d756-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d756-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d756-113">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="1d756-114">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="1d756-114">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="1d756-115">Instrukcje: powiązanie kontrolki Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="1d756-115">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
