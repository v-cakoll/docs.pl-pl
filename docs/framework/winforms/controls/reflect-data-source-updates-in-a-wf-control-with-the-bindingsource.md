---
title: 'Porady: odzwierciedlanie aktualizacji źródła danych w formancie formularzy systemu Windows za pomocą elementu BindingSource'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3efe2ee21b6e9073bc9046eae2537bcf8fd9aa1b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a><span data-ttu-id="58754-102">Porady: odzwierciedlanie aktualizacji źródła danych w formancie formularzy systemu Windows za pomocą elementu BindingSource</span><span class="sxs-lookup"><span data-stu-id="58754-102">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>
<span data-ttu-id="58754-103">Korzystając z formantów powiązanych z danymi, czasami trzeba reagowania na zmiany w źródle danych, gdy źródło danych nie wygenerował zdarzenia zmiany listy.</span><span class="sxs-lookup"><span data-stu-id="58754-103">When you use data-bound controls, you sometimes have to respond to changes in the data source when the data source does not raise list-changed events.</span></span> <span data-ttu-id="58754-104">Jeśli używasz <xref:System.Windows.Forms.BindingSource> składnika można powiązać źródła danych do formantu formularzy systemu Windows może powiadomić formant, który źródła danych został zmieniony przez wywołanie metody <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> — metoda.</span><span class="sxs-lookup"><span data-stu-id="58754-104">When you use the <xref:System.Windows.Forms.BindingSource> component to bind your data source to a Windows Forms control, you can notify the control that your data source has changed by calling the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58754-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="58754-105">Example</span></span>  
 <span data-ttu-id="58754-106">Poniższy przykład kodu pokazuje, przy użyciu <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> metodę, aby powiadomić powiązanej kontrolki dotyczące aktualizacji w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="58754-106">The following code example demonstrates using the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method to notify a bound control about an update in the data source.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="58754-107">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="58754-107">Compiling the Code</span></span>  
 <span data-ttu-id="58754-108">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="58754-108">This example requires:</span></span>  
  
-   <span data-ttu-id="58754-109">Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="58754-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="58754-110">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="58754-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="58754-111">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="58754-111">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="58754-112">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="58754-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58754-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58754-113">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="58754-114">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="58754-114">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="58754-115">Instrukcje: powiązanie kontrolki Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="58754-115">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
