---
title: 'Porady: stosowanie atrybutów w formantach formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 49c2aaa48a48e33a71b5112db31991975011551d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="3858d-102">Porady: stosowanie atrybutów w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3858d-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="3858d-103">Aby opracować składników i formantów, które nawiązują prawidłową interakcję z środowiska projektowania i poprawnego wykonania w czasie wykonywania, należy poprawnie zastosować atrybutów do klas i członków.</span><span class="sxs-lookup"><span data-stu-id="3858d-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3858d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3858d-104">Example</span></span>  
 <span data-ttu-id="3858d-105">Poniższy przykład kodu pokazuje, jak używać kilka atrybutów na kontrolkę niestandardową.</span><span class="sxs-lookup"><span data-stu-id="3858d-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="3858d-106">Formant pokazuje możliwości rejestrowania proste.</span><span class="sxs-lookup"><span data-stu-id="3858d-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="3858d-107">Jeśli formant jest powiązany ze źródłem danych, wyświetla wartości wysyłane przez źródło danych w <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="3858d-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3858d-108">Jeśli wartość przekracza wartość określoną przez `Threshold` właściwość `ThresholdExceeded` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3858d-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="3858d-109">`AttributesDemoControl` Dzienniki wartości z `LogEntry` klasy.</span><span class="sxs-lookup"><span data-stu-id="3858d-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="3858d-110">`LogEntry` Klasy to klasa szablonu, który oznacza, że jest ona sparametryzowana na typ, który rejestruje.</span><span class="sxs-lookup"><span data-stu-id="3858d-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="3858d-111">Na przykład jeśli `AttributesDemoControl` jest rejestrowanie wartości typu `float`, każdy `LogEntry` wystąpienia został zadeklarowany i używane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="3858d-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="3858d-112">Ponieważ `LogEntry` jest sparametryzowana przez dowolnego typu, należy użyć odbicia do działania na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="3858d-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="3858d-113">Do poprawnego, z typem parametru funkcji próg `T` musi implementować <xref:System.IComparable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3858d-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="3858d-114">Formularz, który jest hostem `AttributesDemoControl` okresowo kwerendy licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="3858d-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="3858d-115">Każda wartość jest spakowany w `LogEntry` odpowiedniego typu i dodany do formularza <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="3858d-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="3858d-116">`AttributesDemoControl` Otrzymuje wartość za pośrednictwem jej powiązania danych i wyświetla wartość w <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="3858d-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="3858d-117">W pierwszym przykładzie kodu jest `AttributesDemoControl` implementacji.</span><span class="sxs-lookup"><span data-stu-id="3858d-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="3858d-118">Drugi przykład kodu pokazuje formularza korzystającego z `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="3858d-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="3858d-119">Atrybuty klasy</span><span class="sxs-lookup"><span data-stu-id="3858d-119">Class-level Attributes</span></span>  
 <span data-ttu-id="3858d-120">Niektóre atrybuty są stosowane na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="3858d-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="3858d-121">Poniższy przykład kodu pokazuje atrybuty, które są często stosowane do formantu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3858d-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="3858d-122">Atrybut TypeConverter</span><span class="sxs-lookup"><span data-stu-id="3858d-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="3858d-123"><xref:System.ComponentModel.TypeConverterAttribute> jest inny atrybut często używane klasy poziomie.</span><span class="sxs-lookup"><span data-stu-id="3858d-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="3858d-124">Poniższy przykład kodu pokazuje jej na użytek `LogEntry` klasy.</span><span class="sxs-lookup"><span data-stu-id="3858d-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="3858d-125">W tym przykładzie przedstawiono również implementacja <xref:System.ComponentModel.TypeConverter> dla `LogEntry` typu o nazwie `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="3858d-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="3858d-126">Atrybuty na poziomie członka</span><span class="sxs-lookup"><span data-stu-id="3858d-126">Member-level Attributes</span></span>  
 <span data-ttu-id="3858d-127">Niektóre atrybuty są stosowane na poziomie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="3858d-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="3858d-128">W poniższych przykładach kodu pokazano niektóre atrybuty, które są często stosowane do właściwości formantów formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3858d-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="3858d-129">Atrybut AmbientValue</span><span class="sxs-lookup"><span data-stu-id="3858d-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="3858d-130">W poniższym przykładzie pokazano <xref:System.ComponentModel.AmbientValueAttribute> i zawiera kod, który obsługuje jego interakcji z środowisku projektowania.</span><span class="sxs-lookup"><span data-stu-id="3858d-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="3858d-131">Ta interakcja jest nazywany *otoczenie*.</span><span class="sxs-lookup"><span data-stu-id="3858d-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="3858d-132">Atrybuty wiązania danych</span><span class="sxs-lookup"><span data-stu-id="3858d-132">Databinding Attributes</span></span>  
 <span data-ttu-id="3858d-133">W poniższych przykładach pokazano implementacja złożone powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="3858d-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="3858d-134">Klasa poziomie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, pokazano wcześniej, określa `DataSource` i `DataMember` właściwości do użycia podczas wiązania z danymi.</span><span class="sxs-lookup"><span data-stu-id="3858d-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="3858d-135"><xref:System.ComponentModel.AttributeProviderAttribute> Określa typ, do którego `DataSource` właściwość zostanie z nim powiązane.</span><span class="sxs-lookup"><span data-stu-id="3858d-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3858d-136">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3858d-136">Compiling the Code</span></span>  
  
-   <span data-ttu-id="3858d-137">Formularz, który jest hostem `AttributesDemoControl` wymaga odwołania do `AttributesDemoControl` zestawu w celu przeprowadzenia kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3858d-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3858d-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3858d-138">See Also</span></span>  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="3858d-139">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3858d-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="3858d-140">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3858d-140">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="3858d-141">Porady: serializacji kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="3858d-141">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
