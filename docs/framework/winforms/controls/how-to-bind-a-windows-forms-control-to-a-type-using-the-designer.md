---
title: 'Porady: powiązywanie formantu formularzy systemu Windows z typem przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 33df9e050dd8c2b3ace8ff89cbd5939b538fcd95
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780228"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="53889-102">Porady: powiązywanie formantu formularzy systemu Windows z typem przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="53889-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>
<span data-ttu-id="53889-103">Podczas tworzenia formantów, które współdziałają z danymi, czasami konieczne Powiąż formant typu, a nie obiekt.</span><span class="sxs-lookup"><span data-stu-id="53889-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="53889-104">Zazwyczaj konieczne powiązanie z typem formantu w czasie projektowania, gdy dane nie mogą być dostępne, ale nadal chcesz formantów powiązanych z danymi do wyświetlania danych z interfejsu publicznego typu.</span><span class="sxs-lookup"><span data-stu-id="53889-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="53889-105">Poniższe procedury pokazują, jak utworzyć nową <xref:System.Windows.Forms.BindingSource> oznacza to powiązane z typem, a następnie jak powiązać z jednej z właściwości typu do <xref:System.Windows.Forms.TextBox.Text%2A> właściwość <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="53889-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="53889-106">Aby powiązać BindingSource — typ</span><span class="sxs-lookup"><span data-stu-id="53889-106">To bind the BindingSource to a type</span></span>  
  
1.  <span data-ttu-id="53889-107">Utwórz projekt Windows Forms (**pliku** > **New** > **projektu** > **Visual C#** lub **Języka Visual Basic** > **Classic Desktop** > **Windows Forms aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="53889-107">Create a Windows Forms project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="53889-108">W **projektowania** wyświetlić, przeciągnij <xref:System.Windows.Forms.BindingSource> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="53889-108">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>  
  
3.  <span data-ttu-id="53889-109">W **właściwości** okna, kliknij strzałkę obok <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="53889-109">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>  
  
4.  <span data-ttu-id="53889-110">W **edytora typów Interfejsu DataSource**, kliknij przycisk **Dodaj źródło danych projektu**.</span><span class="sxs-lookup"><span data-stu-id="53889-110">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>  
  
5.  <span data-ttu-id="53889-111">Na **wybierz typ źródła danych** wybierz opcję **obiektu** i kliknij przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="53889-111">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>  
  
6.  <span data-ttu-id="53889-112">Wybierz typ można powiązać:</span><span class="sxs-lookup"><span data-stu-id="53889-112">Select the type to bind to:</span></span>  
  
    -   <span data-ttu-id="53889-113">Jeśli typ, który chcesz powiązać w bieżącym projekcie lub zestawu, który zawiera typ został już dodany jako odwołanie, rozwiń węzły, które można znaleźć żądanego typu, a następnie wybierz ją.</span><span class="sxs-lookup"><span data-stu-id="53889-113">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>  
  
         <span data-ttu-id="53889-114">—lub—</span><span class="sxs-lookup"><span data-stu-id="53889-114">-or-</span></span>  
  
    -   <span data-ttu-id="53889-115">Jeśli typ, który chcesz powiązać to w innym zestawie, nie jest obecnie na liście odwołań, kliknij przycisk **Dodaj odwołanie**, a następnie kliknij przycisk **projektów** kartę. Wybierz projekt, który zawiera obiekt biznesowych, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="53889-115">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="53889-116">Tego projektu, pojawi się na liście zestawów, dzięki czemu można rozwinąć węzły można znaleźć typu użytkownik ma, a następnie wybierz go.</span><span class="sxs-lookup"><span data-stu-id="53889-116">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="53889-117">Jeśli chcesz powiązać z typem w ramach lub zestawu Microsoft, wyczyść **Ukryj zestawy, które zaczynają się od firmy Microsoft lub System** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="53889-117">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>  
  
7.  <span data-ttu-id="53889-118">Kliknij przycisk **dalej**, a następnie kliknij przycisk **Zakończ**.</span><span class="sxs-lookup"><span data-stu-id="53889-118">Click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="53889-119">Aby powiązać kontrolki BindingSource</span><span class="sxs-lookup"><span data-stu-id="53889-119">To bind the control to the BindingSource</span></span>  
  
1.  <span data-ttu-id="53889-120">Dodaj <xref:System.Windows.Forms.TextBox> do formularza.</span><span class="sxs-lookup"><span data-stu-id="53889-120">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>  
  
2.  <span data-ttu-id="53889-121">W **właściwości** okna, rozwiń węzeł **(powiązania danych)** węzła.</span><span class="sxs-lookup"><span data-stu-id="53889-121">In the **Properties** window, expand the **(DataBindings)** node.</span></span>  
  
3.  <span data-ttu-id="53889-122">Kliknij strzałkę obok pozycji <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="53889-122">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
4.  <span data-ttu-id="53889-123">W **edytora typów Interfejsu DataSource**, rozwiń węzeł <xref:System.Windows.Forms.BindingSource> dodane wcześniej, a następnie wybierz pozycję Właściwości powiązanej typ, który chcesz powiązać <xref:System.Windows.Forms.TextBox.Text%2A> właściwość <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="53889-123">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53889-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53889-124">See Also</span></span>  
 [<span data-ttu-id="53889-125">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="53889-125">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="53889-126">Instrukcje: powiązanie kontrolki Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="53889-126">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [<span data-ttu-id="53889-127">Wiązanie kontrolek z danymi w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="53889-127">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
