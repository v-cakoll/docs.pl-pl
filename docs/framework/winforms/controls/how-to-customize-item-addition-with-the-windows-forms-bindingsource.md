---
title: 'Porady: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 299b24eb42c576535389f53982581bf4a776ee3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="29bdb-102">Porady: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="29bdb-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="29bdb-103">Jeśli używasz <xref:System.Windows.Forms.BindingSource> składnika powiązanie formantu formularzy systemu Windows ze źródłem danych może być konieczne dostosowanie tworzenie nowych elementów.</span><span class="sxs-lookup"><span data-stu-id="29bdb-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="29bdb-104"><xref:System.Windows.Forms.BindingSource> Składnika sprawia, że to proste zapewniając <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenie, które zwykle jest wywoływane, gdy formant związany potrzebuje do utworzenia nowego elementu.</span><span class="sxs-lookup"><span data-stu-id="29bdb-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="29bdb-105">Obsługi zdarzenia zapewniają wszelkie niestandardowe zachowanie jest wymagana (na przykład wywołanie metody usługi sieci Web lub wprowadzenie nowego obiektu z fabryki klasy).</span><span class="sxs-lookup"><span data-stu-id="29bdb-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29bdb-106">Po dodaniu elementu Obsługa <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzeń, nie można anulować operacji dodawania.</span><span class="sxs-lookup"><span data-stu-id="29bdb-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29bdb-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="29bdb-107">Example</span></span>  
 <span data-ttu-id="29bdb-108">W poniższym przykładzie pokazano, jak można powiązać <xref:System.Windows.Forms.DataGridView> formantu fabrykę klas przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="29bdb-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="29bdb-109">Po kliknięciu przez użytkownika <xref:System.Windows.Forms.DataGridView> formantu nowy wiersz <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="29bdb-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="29bdb-110">Tworzy nową klasę programu obsługi zdarzeń `DemoCustomer` obiektu, który jest przypisany do <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="29bdb-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="29bdb-111">Powoduje to, że nowe `DemoCustomer` obiekt ma zostać dodany do <xref:System.Windows.Forms.BindingSource> listy składnika i mają być wyświetlane w nowym wierszu <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="29bdb-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="29bdb-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="29bdb-112">Compiling the Code</span></span>  
 <span data-ttu-id="29bdb-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="29bdb-113">This example requires:</span></span>  
  
-   <span data-ttu-id="29bdb-114">Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="29bdb-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="29bdb-115">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="29bdb-115">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="29bdb-116">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="29bdb-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="29bdb-117">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="29bdb-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29bdb-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29bdb-118">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="29bdb-119">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="29bdb-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="29bdb-120">Instrukcje: powiązanie kontrolki Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="29bdb-120">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
