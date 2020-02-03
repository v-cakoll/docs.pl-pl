---
title: Nawigowanie po danych przy użyciu kontrolki BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
ms.openlocfilehash: 10508cb447e70cc387f9d98effa3bc4b5ccbbaa9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735998"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="5e910-102">Porady: nawigowanie w danych za pomocą kontrolki BindingNavigator formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5e910-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="5e910-103">Pojawieniu formantu <xref:System.Windows.Forms.BindingNavigator> w Windows Forms umożliwiają deweloperom udostępnianie użytkownikom końcowym prostego interfejsu użytkownika do nawigacji i manipulowania danymi na tworzonych formularzach.</span><span class="sxs-lookup"><span data-stu-id="5e910-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="5e910-104">Formant <xref:System.Windows.Forms.BindingNavigator> jest formantem <xref:System.Windows.Forms.ToolStrip> z wstępnie skonfigurowanymi przyciskami do nawigacji do pierwszego, ostatniego, następnego i poprzedniego rekordu w zestawie danych, a także przycisków służących do dodawania i usuwania rekordów.</span><span class="sxs-lookup"><span data-stu-id="5e910-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="5e910-105">Dodawanie przycisków do kontrolki <xref:System.Windows.Forms.BindingNavigator> jest proste, ponieważ jest to kontrolka <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="5e910-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="5e910-106">Aby zapoznać się z przykładami, zobacz [jak: Dodawanie przycisków Load, Save i Cancel do Windows Forms BindingNavigator Control](load-save-and-cancel-bindingnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="5e910-106">For examples, see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](load-save-and-cancel-bindingnavigator.md).</span></span>  
  
 <span data-ttu-id="5e910-107">Dla każdego przycisku w kontrolce <xref:System.Windows.Forms.BindingNavigator> istnieje odpowiedni element członkowski składnika <xref:System.Windows.Forms.BindingSource>, który programowo umożliwia korzystanie z tych samych funkcji.</span><span class="sxs-lookup"><span data-stu-id="5e910-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="5e910-108">Na przykład przycisk <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> odpowiada metodzie <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> składnika <xref:System.Windows.Forms.BindingSource>, przycisk <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> odpowiada metodzie <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="5e910-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="5e910-109">W związku z tym włączenie kontrolki <xref:System.Windows.Forms.BindingNavigator> do nawigowania po rekordach danych jest proste jako ustawienie właściwości <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> na odpowiedni składnik <xref:System.Windows.Forms.BindingSource> w formularzu.</span><span class="sxs-lookup"><span data-stu-id="5e910-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="5e910-110">Aby skonfigurować formant BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="5e910-110">To set up the BindingNavigator control</span></span>  
  
1. <span data-ttu-id="5e910-111">Dodaj składnik <xref:System.Windows.Forms.BindingSource> o nazwie `bindingSource1` i dwóch kontrolek <xref:System.Windows.Forms.TextBox> o nazwie `textBox1` i `textBox2`.</span><span class="sxs-lookup"><span data-stu-id="5e910-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2. <span data-ttu-id="5e910-112">Powiąż `bindingSource1` z danymi i kontrolki TextBox, aby `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="5e910-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="5e910-113">Aby to zrobić, wklej następujący kod do formularza i Wywołaj `LoadData` z konstruktora formularza lub <xref:System.Windows.Forms.Form.Load> metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5e910-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="5e910-114">Dodaj kontrolkę <xref:System.Windows.Forms.BindingNavigator> o nazwie `bindingNavigator1` do formularza.</span><span class="sxs-lookup"><span data-stu-id="5e910-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4. <span data-ttu-id="5e910-115">Ustaw właściwość <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> na `bindingNavigator1` na `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="5e910-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="5e910-116">Można to zrobić za pomocą projektanta lub kodu.</span><span class="sxs-lookup"><span data-stu-id="5e910-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="5e910-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e910-117">Example</span></span>  
 <span data-ttu-id="5e910-118">Poniższy przykład kodu jest kompletnym przykładem dla powyższych kroków.</span><span class="sxs-lookup"><span data-stu-id="5e910-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5e910-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5e910-119">Compiling the Code</span></span>  
 <span data-ttu-id="5e910-120">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5e910-120">This example requires:</span></span>  
  
- <span data-ttu-id="5e910-121">Odwołania do zestawów system, system. Data, system. Drawing, system. Windows. Forms i system. XML.</span><span class="sxs-lookup"><span data-stu-id="5e910-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e910-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e910-122">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="5e910-123">BindingNavigator, kontrolka</span><span class="sxs-lookup"><span data-stu-id="5e910-123">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="5e910-124">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="5e910-124">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
