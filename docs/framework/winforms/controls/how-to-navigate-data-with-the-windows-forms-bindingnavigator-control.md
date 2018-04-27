---
title: 'Porady: nawigowanie w danych za pomocą kontrolki BindingNavigator formularzy systemu Windows'
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
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a47273f9598b3776276c14d41e88f7f0dff5bed
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="7f250-102">Porady: nawigowanie w danych za pomocą kontrolki BindingNavigator formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7f250-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="7f250-103">Pojawienie się <xref:System.Windows.Forms.BindingNavigator> formantu w formularzach systemu Windows umożliwia deweloperom zapewnić użytkownikom końcowym proste danych nawigacji i manipulacji interfejsu użytkownika w formularzach tworzenia.</span><span class="sxs-lookup"><span data-stu-id="7f250-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="7f250-104"><xref:System.Windows.Forms.BindingNavigator> Formant jest <xref:System.Windows.Forms.ToolStrip> kontrolki z przycisków wstępnie nawigacji jako pierwszy, ostatni, następny i poprzedni rekord w zestawie danych, jak również przyciski dodawania i usuwania rekordów.</span><span class="sxs-lookup"><span data-stu-id="7f250-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="7f250-105">Dodawanie przycisków do <xref:System.Windows.Forms.BindingNavigator> formant jest łatwe, ponieważ jest on <xref:System.Windows.Forms.ToolStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="7f250-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  <span data-ttu-id="7f250-106">Zobacz też [porady: Dodawanie obciążenia, Zapisz i Anuluj przycisków do formantu BindingNavigator formularzy systemu Windows](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7f250-106">Also see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="7f250-107">Dla każdego przycisku na <xref:System.Windows.Forms.BindingNavigator> kontrolować, jest elementem członkowskim odpowiedniego <xref:System.Windows.Forms.BindingSource> składnik, który umożliwia programowo te same funkcje.</span><span class="sxs-lookup"><span data-stu-id="7f250-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="7f250-108">Na przykład <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> przycisk odpowiada <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metody <xref:System.Windows.Forms.BindingSource> składnika <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> przycisk odpowiada <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> — metoda i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="7f250-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="7f250-109">W związku z tym włączenie <xref:System.Windows.Forms.BindingNavigator> formant do nawigacji rekordów danych jest prostą jako ustawienie jej <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> właściwości do odpowiedniego <xref:System.Windows.Forms.BindingSource> składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="7f250-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="7f250-110">Aby skonfigurować BindingNavigator — formant</span><span class="sxs-lookup"><span data-stu-id="7f250-110">To set up the BindingNavigator control</span></span>  
  
1.  <span data-ttu-id="7f250-111">Dodaj <xref:System.Windows.Forms.BindingSource> składnika o nazwie `bindingSource1` i dwa <xref:System.Windows.Forms.TextBox> formantów `textBox1` i `textBox2`.</span><span class="sxs-lookup"><span data-stu-id="7f250-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2.  <span data-ttu-id="7f250-112">Powiąż `bindingSource1` do danych i formanty pole tekstowe `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="7f250-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="7f250-113">W tym celu Wklej następujący kod do formularza i wywołanie `LoadData` z konstruktora formularza lub <xref:System.Windows.Forms.Form.Load> metoda obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7f250-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="7f250-114">Dodaj <xref:System.Windows.Forms.BindingNavigator> formantu o nazwie `bindingNavigator1` do formularza.</span><span class="sxs-lookup"><span data-stu-id="7f250-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4.  <span data-ttu-id="7f250-115">Ustaw <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> właściwość `bindingNavigator1` do `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="7f250-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="7f250-116">Można to zrobić przy użyciu projektanta lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7f250-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="7f250-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f250-117">Example</span></span>  
 <span data-ttu-id="7f250-118">Poniższy przykładowy kod jest pełny przykład dla wymienionymi wcześniej czynności.</span><span class="sxs-lookup"><span data-stu-id="7f250-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f250-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7f250-119">Compiling the Code</span></span>  
 <span data-ttu-id="7f250-120">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="7f250-120">This example requires:</span></span>  
  
-   <span data-ttu-id="7f250-121">Odwołania do zestawów systemu, dane systemowe, System.Drawing, System.Windows.Forms i zestawów System.Xml.</span><span class="sxs-lookup"><span data-stu-id="7f250-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="7f250-122">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7f250-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7f250-123">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="7f250-123">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="7f250-124">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7f250-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f250-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f250-125">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [<span data-ttu-id="7f250-126">BindingNavigator, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7f250-126">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="7f250-127">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7f250-127">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
