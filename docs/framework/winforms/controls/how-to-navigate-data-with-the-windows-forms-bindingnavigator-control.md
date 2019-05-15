---
title: 'Instrukcje: nawigowanie w danych za pomocą kontrolki BindingNavigator formularzy systemu Windows'
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
ms.openlocfilehash: 81a265d13e94cb623040ad28cf279c0ec5b7887b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590961"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="db8a9-102">Instrukcje: nawigowanie w danych za pomocą kontrolki BindingNavigator formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="db8a9-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="db8a9-103">Pojawienie się <xref:System.Windows.Forms.BindingNavigator> kontroli w formularzach Windows Forms umożliwia deweloperom zapewni użytkownikom końcowym proste dane nawigacji i manipulowania interfejsu użytkownika w formularzach tworzą.</span><span class="sxs-lookup"><span data-stu-id="db8a9-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="db8a9-104"><xref:System.Windows.Forms.BindingNavigator> Formant jest <xref:System.Windows.Forms.ToolStrip> sterowania za pomocą przycisków wstępnie skonfigurować pod kątem nawigację do pierwszego, last, następnej i poprzedniej rekordu w zestawie danych, jak również przycisków, aby dodawać i usuwać rekordy.</span><span class="sxs-lookup"><span data-stu-id="db8a9-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="db8a9-105">Dodawanie przycisków do <xref:System.Windows.Forms.BindingNavigator> kontroli jest łatwe, ponieważ jest on <xref:System.Windows.Forms.ToolStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="db8a9-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="db8a9-106">Aby uzyskać przykłady, zobacz [jak: Dodaj obciążenia, Zapisz i Anuluj przycisków Windows kontrolki BindingNavigator formularzy](load-save-and-cancel-bindingnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="db8a9-106">For examples, see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](load-save-and-cancel-bindingnavigator.md).</span></span>  
  
 <span data-ttu-id="db8a9-107">Dla każdego przycisku w <xref:System.Windows.Forms.BindingNavigator> sterowania, jest elementem członkowskim odpowiednie <xref:System.Windows.Forms.BindingSource> składnik, który programowo zezwala na taką samą funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="db8a9-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="db8a9-108">Na przykład <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> przycisk odnosi się do <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metody <xref:System.Windows.Forms.BindingSource> składnika <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> przycisk odnosi się do <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> metoda i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="db8a9-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="db8a9-109">W rezultacie, umożliwiając <xref:System.Windows.Forms.BindingNavigator> sterowania Przejdź rekordów danych to prosty jako ustawienie jego <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> właściwości do odpowiednich <xref:System.Windows.Forms.BindingSource> składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="db8a9-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="db8a9-110">Aby skonfigurować BindingNavigator — kontrolka</span><span class="sxs-lookup"><span data-stu-id="db8a9-110">To set up the BindingNavigator control</span></span>  
  
1. <span data-ttu-id="db8a9-111">Dodaj <xref:System.Windows.Forms.BindingSource> składnika o nazwie `bindingSource1` oraz dwóch <xref:System.Windows.Forms.TextBox> kontrolki o nazwie `textBox1` i `textBox2`.</span><span class="sxs-lookup"><span data-stu-id="db8a9-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2. <span data-ttu-id="db8a9-112">Powiąż `bindingSource1` do danych i kontrolki pola tekstowego do `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="db8a9-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="db8a9-113">Aby to zrobić, wklej następujący kod do formularza i wywołania `LoadData` z konstruktora formularza lub <xref:System.Windows.Forms.Form.Load> metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="db8a9-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="db8a9-114">Dodaj <xref:System.Windows.Forms.BindingNavigator> formantu o nazwie `bindingNavigator1` do formularza.</span><span class="sxs-lookup"><span data-stu-id="db8a9-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4. <span data-ttu-id="db8a9-115">Ustaw <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> właściwość `bindingNavigator1` do `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="db8a9-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="db8a9-116">Można to zrobić za pomocą projektanta lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="db8a9-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="db8a9-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="db8a9-117">Example</span></span>  
 <span data-ttu-id="db8a9-118">Poniższy przykład kodu jest kompletny przykład kroków wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="db8a9-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="db8a9-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="db8a9-119">Compiling the Code</span></span>  
 <span data-ttu-id="db8a9-120">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="db8a9-120">This example requires:</span></span>  
  
- <span data-ttu-id="db8a9-121">Odwołania do zestawów systemu, dane systemowe, System.Drawing, przestrzeń nazw System.Windows.Forms i System.Xml.</span><span class="sxs-lookup"><span data-stu-id="db8a9-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db8a9-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db8a9-122">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="db8a9-123">BindingNavigator, kontrolka</span><span class="sxs-lookup"><span data-stu-id="db8a9-123">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="db8a9-124">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="db8a9-124">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
