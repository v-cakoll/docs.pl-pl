---
title: 'Instrukcje: Wywoływanie powiadomień o zmianie za BindingSource Resetitem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: eb97191e30cd2c4eb5ad8b8bbc158819ac1fe396
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261417"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a><span data-ttu-id="d3ae4-102">Instrukcje: Wywoływanie powiadomień o zmianie za BindingSource Resetitem</span><span class="sxs-lookup"><span data-stu-id="d3ae4-102">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>
<span data-ttu-id="d3ae4-103">Niektóre źródła danych dla kontrolki nie wywoływanie powiadomień o zmianie, gdy elementy są zmieniane, dodawane lub usuwane.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-103">Some data sources for your controls do not raise change notifications when items are changed, added, or deleted.</span></span> <span data-ttu-id="d3ae4-104">Za pomocą <xref:System.Windows.Forms.BindingSource> składnik, można powiązać z takich źródeł danych i zgłosić powiadomienia o zmianach w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-104">With the <xref:System.Windows.Forms.BindingSource> component, you can bind to such data sources and raise a change notification from your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3ae4-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3ae4-105">Example</span></span>  
 <span data-ttu-id="d3ae4-106">Ten formularz, który demonstruje sposób użycia <xref:System.Windows.Forms.BindingSource> składnik do listy, aby powiązać <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-106">This form demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind a list to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d3ae4-107">Listy nie powoduje powiadomienia o zmianie, więc <xref:System.Windows.Forms.BindingSource.ResetItem%2A> metody <xref:System.Windows.Forms.BindingSource> jest wywoływana, gdy element na liście zostanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-107">The list does not raise change notifications, so the <xref:System.Windows.Forms.BindingSource.ResetItem%2A> method on the <xref:System.Windows.Forms.BindingSource> is called when an item in the list is changed.</span></span> <span data-ttu-id="d3ae4-108">.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-108">.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d3ae4-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d3ae4-109">Compiling the Code</span></span>  
 <span data-ttu-id="d3ae4-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="d3ae4-110">This example requires:</span></span>  
  
-   <span data-ttu-id="d3ae4-111">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-111">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="d3ae4-112">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d3ae4-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="d3ae4-113">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="d3ae4-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ae4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3ae4-114">See also</span></span>
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="d3ae4-115">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="d3ae4-115">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [<span data-ttu-id="d3ae4-116">Instrukcje: Powiązanie z typem formantu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3ae4-116">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
