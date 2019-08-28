---
title: 'Instrukcje: wiązanie kontrolki formularzy systemu Windows z typem przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 5069d7d3b5ef4c5b05159dac521d32f5be8abdd1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046043"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="cb852-102">Instrukcje: wiązanie kontrolki formularzy systemu Windows z typem przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="cb852-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>

<span data-ttu-id="cb852-103">Podczas kompilowania formantów, które współpracują z danymi, czasami trzeba powiązać formant z typem, a nie obiektem.</span><span class="sxs-lookup"><span data-stu-id="cb852-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="cb852-104">Zazwyczaj należy powiązać kontrolkę z typem w czasie projektowania, gdy dane mogą nie być dostępne, ale nadal chcesz, aby formanty powiązane z danymi wyświetlały dane z interfejsu publicznego typu.</span><span class="sxs-lookup"><span data-stu-id="cb852-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="cb852-105">W poniższych procedurach pokazano, jak utworzyć nową <xref:System.Windows.Forms.BindingSource> , która jest powiązana z typem, a następnie powiązać jedną z właściwości <xref:System.Windows.Forms.TextBox.Text%2A> typu z właściwością <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="cb852-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>

### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="cb852-106">Aby powiązać źródło BindingSource z typem</span><span class="sxs-lookup"><span data-stu-id="cb852-106">To bind the BindingSource to a type</span></span>

1. <span data-ttu-id="cb852-107">Utwórz projekt Windows Forms (**plik** > **Nowy** > **projekt** > **Visual C#**  lub **Visual Basic** **klasyczny** pulpit >   >  **Windows Forms aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="cb852-107">Create a Windows Forms project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="cb852-108">W widoku **projektu** przeciągnij <xref:System.Windows.Forms.BindingSource> składnik na formularz.</span><span class="sxs-lookup"><span data-stu-id="cb852-108">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>

3. <span data-ttu-id="cb852-109">W oknie **Właściwości** kliknij strzałkę dla <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb852-109">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>

4. <span data-ttu-id="cb852-110">W **Edytorze typów interfejsu użytkownika źródła**danych kliknij przycisk **Dodaj źródło dane projektu**.</span><span class="sxs-lookup"><span data-stu-id="cb852-110">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>

5. <span data-ttu-id="cb852-111">Na stronie **Wybierz typ źródła danych** wybierz pozycję **obiekt** i kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="cb852-111">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>

6. <span data-ttu-id="cb852-112">Wybierz typ do powiązania:</span><span class="sxs-lookup"><span data-stu-id="cb852-112">Select the type to bind to:</span></span>

    - <span data-ttu-id="cb852-113">Jeśli typ, który ma zostać powiązany, znajduje się w bieżącym projekcie lub zestaw, który zawiera typ, został już dodany jako odwołanie, rozwiń węzły, aby znaleźć żądany typ, a następnie wybierz go.</span><span class="sxs-lookup"><span data-stu-id="cb852-113">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>

      <span data-ttu-id="cb852-114">\-oraz</span><span class="sxs-lookup"><span data-stu-id="cb852-114">\-or-</span></span>

    - <span data-ttu-id="cb852-115">Jeśli typ, który ma zostać powiązany, znajduje się w innym zestawie, nie jest obecnie na liście odwołań, kliknij przycisk **Dodaj odwołanie**, a następnie kliknij kartę **projekty** . Wybierz projekt zawierający obiekt biznesowy, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="cb852-115">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="cb852-116">Ten projekt pojawi się na liście zestawów, dzięki czemu można rozwinąć węzły w celu znalezienia żądanego typu, a następnie wybrać.</span><span class="sxs-lookup"><span data-stu-id="cb852-116">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>

      > [!NOTE]
      > <span data-ttu-id="cb852-117">Jeśli chcesz powiązać z typem w strukturze lub zestawie Microsoft, usuń zaznaczenie pola wyboru **Ukryj zestawy, które zaczynają się od firmy Microsoft lub systemu** .</span><span class="sxs-lookup"><span data-stu-id="cb852-117">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>

7. <span data-ttu-id="cb852-118">Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="cb852-118">Click **Next**, and then click **Finish**.</span></span>

### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="cb852-119">Aby powiązać formant z BindingSource</span><span class="sxs-lookup"><span data-stu-id="cb852-119">To bind the control to the BindingSource</span></span>

1. <span data-ttu-id="cb852-120"><xref:System.Windows.Forms.TextBox> Dodaj do formularza.</span><span class="sxs-lookup"><span data-stu-id="cb852-120">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>

2. <span data-ttu-id="cb852-121">W oknie **Właściwości** rozwiń węzeł **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="cb852-121">In the **Properties** window, expand the **(DataBindings)** node.</span></span>

3. <span data-ttu-id="cb852-122">Kliknij strzałkę obok <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb852-122">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>

4. <span data-ttu-id="cb852-123">W **Edytorze typów interfejsu użytkownika źródła danych**rozwiń węzeł <xref:System.Windows.Forms.BindingSource> dodany poprzednio i wybierz właściwość powiązanego typu, który chcesz powiązać z <xref:System.Windows.Forms.TextBox.Text%2A> właściwością <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="cb852-123">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb852-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb852-124">See also</span></span>

- [<span data-ttu-id="cb852-125">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="cb852-125">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="cb852-126">Instrukcje: Powiąż formant Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="cb852-126">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
- [<span data-ttu-id="cb852-127">Wiązanie kontrolek z danymi w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cb852-127">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
