---
title: "Porady: powiązywanie formantu formularzy systemu Windows z typem przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 215a69a47b0588e45fcc28202dce4c6210b1dfe6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="a0e69-102">Porady: powiązywanie formantu formularzy systemu Windows z typem przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="a0e69-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>
<span data-ttu-id="a0e69-103">Podczas tworzenia formantów, które współdziałają z danymi, czasami trzeba powiązanie formantu typu, a nie obiektu.</span><span class="sxs-lookup"><span data-stu-id="a0e69-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="a0e69-104">Zazwyczaj należy powiązać z typem formantu w czasie projektowania, gdy dane mogą nie być dostępne, ale nadal ma formantów powiązanych z danymi do wyświetlania danych z interfejsu publicznego typu.</span><span class="sxs-lookup"><span data-stu-id="a0e69-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="a0e69-105">Poniższe procedury pokazują, jak utworzyć nową <xref:System.Windows.Forms.BindingSource> który jest powiązany z typem, a następnie powiązać z jednej z właściwości typu do <xref:System.Windows.Forms.TextBox.Text%2A> właściwość <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="a0e69-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="a0e69-106">Aby powiązać element BindingSource typu</span><span class="sxs-lookup"><span data-stu-id="a0e69-106">To bind the BindingSource to a type</span></span>  
  
1.  <span data-ttu-id="a0e69-107">Utwórz projekt formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a0e69-107">Create a Windows Forms project.</span></span>  
  
     <span data-ttu-id="a0e69-108">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span><span class="sxs-lookup"><span data-stu-id="a0e69-108">For more information, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="a0e69-109">W **projekt** wyświetlić, przeciągnij <xref:System.Windows.Forms.BindingSource> składnika na formularzu.</span><span class="sxs-lookup"><span data-stu-id="a0e69-109">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>  
  
3.  <span data-ttu-id="a0e69-110">W **właściwości** okna, kliknij strzałkę obok <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a0e69-110">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>  
  
4.  <span data-ttu-id="a0e69-111">W **Edytor typów interfejsu użytkownika dla źródła danych**, kliknij przycisk **Dodaj źródło danych projektu**.</span><span class="sxs-lookup"><span data-stu-id="a0e69-111">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>  
  
5.  <span data-ttu-id="a0e69-112">Na **wybierz typ źródła danych** wybierz pozycję **obiektu** i kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="a0e69-112">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>  
  
6.  <span data-ttu-id="a0e69-113">Wybierz typ, aby powiązać:</span><span class="sxs-lookup"><span data-stu-id="a0e69-113">Select the type to bind to:</span></span>  
  
    -   <span data-ttu-id="a0e69-114">Jeśli typ, który chcesz powiązać to w bieżącym projekcie, lub zestawu zawierającego typ został już dodany jako odwołanie, rozwiń węzły można znaleźć żądanego typu, a następnie wybierz go.</span><span class="sxs-lookup"><span data-stu-id="a0e69-114">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>  
  
         <span data-ttu-id="a0e69-115">—lub—</span><span class="sxs-lookup"><span data-stu-id="a0e69-115">-or-</span></span>  
  
    -   <span data-ttu-id="a0e69-116">Jeśli chcesz powiązać typu jest w innym zestawie nie jest obecnie na liście odwołań, kliknij przycisk **Dodaj odwołanie**, a następnie kliknij przycisk **projekty** kartę. Wybierz projekt, który zawiera obiektu biznesowego, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a0e69-116">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="a0e69-117">Ten projekt zostanie wyświetlony na liście zestawów, dlatego można rozwinąć węzły można znaleźć typu można mają, a następnie wybierz go.</span><span class="sxs-lookup"><span data-stu-id="a0e69-117">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a0e69-118">Jeśli chcesz powiązać z typem w ramach lub zestawu Microsoft, wyczyść **Ukryj zestawy, które zaczynają się od firmy Microsoft lub System** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="a0e69-118">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>  
  
7.  <span data-ttu-id="a0e69-119">Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="a0e69-119">Click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="a0e69-120">Aby powiązać formantu BindingSource</span><span class="sxs-lookup"><span data-stu-id="a0e69-120">To bind the control to the BindingSource</span></span>  
  
1.  <span data-ttu-id="a0e69-121">Dodaj <xref:System.Windows.Forms.TextBox> do formularza.</span><span class="sxs-lookup"><span data-stu-id="a0e69-121">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>  
  
2.  <span data-ttu-id="a0e69-122">W **właściwości** okna, rozwiń węzeł **(DataBindings)** węzła.</span><span class="sxs-lookup"><span data-stu-id="a0e69-122">In the **Properties** window, expand the **(DataBindings)** node.</span></span>  
  
3.  <span data-ttu-id="a0e69-123">Kliknij strzałkę obok pozycji <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a0e69-123">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
4.  <span data-ttu-id="a0e69-124">W **Edytor typów interfejsu użytkownika dla źródła danych**, rozwiń węzeł <xref:System.Windows.Forms.BindingSource> dodane wcześniej, a następnie wybierz właściwość typu powiązanej chcesz powiązać <xref:System.Windows.Forms.TextBox.Text%2A> właściwość <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="a0e69-124">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e69-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0e69-125">See Also</span></span>  
 [<span data-ttu-id="a0e69-126">BindingSource — składnik</span><span class="sxs-lookup"><span data-stu-id="a0e69-126">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="a0e69-127">Porady: powiązanie formantu formularzy systemu Windows z typem</span><span class="sxs-lookup"><span data-stu-id="a0e69-127">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [<span data-ttu-id="a0e69-128">Powiązywanie formantów z danymi w Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a0e69-128">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
