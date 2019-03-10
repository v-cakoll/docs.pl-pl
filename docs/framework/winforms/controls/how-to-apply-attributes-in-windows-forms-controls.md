---
title: 'Instrukcje: Stosowanie atrybutów w kontrolkach formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: fd41999b1cd1cde940d182f3acc505bbb92a3aa4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718548"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="5ff25-102">Instrukcje: Stosowanie atrybutów w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5ff25-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="5ff25-103">Do tworzenia składników i formantów, które nawiązują prawidłową interakcję z środowiska projektowania i poprawnego wykonania w czasie wykonywania, należy poprawnie zastosować atrybutów do klas i składowych.</span><span class="sxs-lookup"><span data-stu-id="5ff25-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ff25-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ff25-104">Example</span></span>  
 <span data-ttu-id="5ff25-105">Poniższy przykład kodu demonstruje sposób używania kilka atrybutów w formancie niestandardowym.</span><span class="sxs-lookup"><span data-stu-id="5ff25-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="5ff25-106">Kontrolka pokazuje prosty rejestrować.</span><span class="sxs-lookup"><span data-stu-id="5ff25-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="5ff25-107">Gdy kontrolka jest powiązana ze źródłem danych, wyświetla wartości wysyłane przez źródło danych w <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="5ff25-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5ff25-108">Jeśli wartość przekracza wartość określoną przez `Threshold` właściwości `ThresholdExceeded` zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="5ff25-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="5ff25-109">`AttributesDemoControl` Dzienniki wartościami `LogEntry` klasy.</span><span class="sxs-lookup"><span data-stu-id="5ff25-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="5ff25-110">`LogEntry` Klasa jest klasą szablonu, który oznacza, że jest ona parametryzowane na typ, który rejestruje.</span><span class="sxs-lookup"><span data-stu-id="5ff25-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="5ff25-111">Na przykład jeśli `AttributesDemoControl` jest rejestrowanie wartości typu `float`, każdy `LogEntry` wystąpienie jest zadeklarowana i używane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="5ff25-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  <span data-ttu-id="5ff25-112">Ponieważ `LogEntry` jest sparametryzowane według dowolnego typu go używać odbicia do działania na typ parametru.</span><span class="sxs-lookup"><span data-stu-id="5ff25-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="5ff25-113">Dla funkcji próg do pracy z typem parametru `T` musi implementować <xref:System.IComparable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5ff25-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="5ff25-114">Formularz, który jest hostem `AttributesDemoControl` okresowo wysyła zapytanie licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="5ff25-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="5ff25-115">Każda wartość jest spakowany w `LogEntry` odpowiedniego typu i dodany do formularza <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="5ff25-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="5ff25-116">`AttributesDemoControl` Otrzymuje wartość za pomocą jego powiązania danych i wyświetla wartości w <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="5ff25-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="5ff25-117">Pierwszy przykład kodu jest `AttributesDemoControl` implementacji.</span><span class="sxs-lookup"><span data-stu-id="5ff25-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="5ff25-118">Drugi przykład kodu demonstruje formularz, który używa `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="5ff25-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="5ff25-119">Atrybuty klasy</span><span class="sxs-lookup"><span data-stu-id="5ff25-119">Class-level Attributes</span></span>  
 <span data-ttu-id="5ff25-120">Niektóre atrybuty są stosowane na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="5ff25-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="5ff25-121">Poniższy przykład kodu pokazuje atrybuty, które są często stosowane do formantu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5ff25-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="5ff25-122">TypeConverter Attribute</span><span class="sxs-lookup"><span data-stu-id="5ff25-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="5ff25-123"><xref:System.ComponentModel.TypeConverterAttribute> jest inny atrybut poziomie klasy często używane.</span><span class="sxs-lookup"><span data-stu-id="5ff25-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="5ff25-124">Poniższy przykład kodu pokazuje jego stosowanie `LogEntry` klasy.</span><span class="sxs-lookup"><span data-stu-id="5ff25-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="5ff25-125">W tym przykładzie przedstawiono również implementację <xref:System.ComponentModel.TypeConverter> dla `LogEntry` typu, o nazwie `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="5ff25-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="5ff25-126">Atrybuty na poziomie członka</span><span class="sxs-lookup"><span data-stu-id="5ff25-126">Member-level Attributes</span></span>  
 <span data-ttu-id="5ff25-127">Niektóre atrybuty są stosowane na poziomie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="5ff25-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="5ff25-128">W poniższych przykładach kodu pokazano niektóre atrybuty, które są często stosowane do właściwości kontrolek formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5ff25-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="5ff25-129">AmbientValue Attribute</span><span class="sxs-lookup"><span data-stu-id="5ff25-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="5ff25-130">W poniższym przykładzie pokazano <xref:System.ComponentModel.AmbientValueAttribute> i zawiera kod, który obsługuje wchodzi w interakcję z środowisko projektowania.</span><span class="sxs-lookup"><span data-stu-id="5ff25-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="5ff25-131">Ta interakcja jest nazywany *otoczenie*.</span><span class="sxs-lookup"><span data-stu-id="5ff25-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="5ff25-132">Atrybuty wiązania danych</span><span class="sxs-lookup"><span data-stu-id="5ff25-132">Databinding Attributes</span></span>  
 <span data-ttu-id="5ff25-133">Poniższy przykład pokazuje implementację złożone powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="5ff25-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="5ff25-134">Klasa poziomie <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, jak pokazano wcześniej, określa `DataSource` i `DataMember` właściwości mają zostać użyte do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="5ff25-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="5ff25-135"><xref:System.ComponentModel.AttributeProviderAttribute> Określa typ, do którego `DataSource` właściwość zostanie z nim powiązane.</span><span class="sxs-lookup"><span data-stu-id="5ff25-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5ff25-136">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5ff25-136">Compiling the Code</span></span>  
  
-   <span data-ttu-id="5ff25-137">Formularz, który jest hostem `AttributesDemoControl` wymaga odwołania do `AttributesDemoControl` zestawu w celu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5ff25-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff25-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ff25-138">See also</span></span>
- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="5ff25-139">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5ff25-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="5ff25-140">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5ff25-140">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
- <span data-ttu-id="5ff25-141">[Instrukcje: Serializowanie kolekcji standardowych typów za pomocą DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="5ff25-141">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
