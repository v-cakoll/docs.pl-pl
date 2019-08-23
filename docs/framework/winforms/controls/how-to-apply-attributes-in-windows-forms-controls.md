---
title: 'Instrukcje: stosowanie atrybutów w kontrolkach formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 273d32927582f4467a92cd3b8f87e699c1f167d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922781"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="3efa2-102">Instrukcje: stosowanie atrybutów w kontrolkach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3efa2-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="3efa2-103">Aby opracować składniki i formanty współdziałające prawidłowo ze środowiskiem projektowym i działać prawidłowo w czasie wykonywania, należy prawidłowo zastosować atrybuty do klas i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="3efa2-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3efa2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3efa2-104">Example</span></span>  
 <span data-ttu-id="3efa2-105">Poniższy przykład kodu demonstruje, jak używać kilku atrybutów w kontrolce niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="3efa2-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="3efa2-106">Kontrolka pokazuje prostą funkcję rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="3efa2-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="3efa2-107">Gdy formant jest powiązany ze źródłem danych, wyświetla wartości wysyłane przez źródło danych w <xref:System.Windows.Forms.DataGridView> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="3efa2-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3efa2-108">Jeśli wartość przekroczy wartość określoną przez `Threshold` Właściwość `ThresholdExceeded` , zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="3efa2-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="3efa2-109">`AttributesDemoControl` Rejestruje wartości zklasą`LogEntry` .</span><span class="sxs-lookup"><span data-stu-id="3efa2-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="3efa2-110">`LogEntry` Klasa jest klasą szablonu, co oznacza, że jest sparametryzowane dla typu, który rejestruje.</span><span class="sxs-lookup"><span data-stu-id="3efa2-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="3efa2-111">Na przykład, jeśli `AttributesDemoControl` rejestruje wartości typu `float`, każde `LogEntry` wystąpienie jest zadeklarowane i używane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="3efa2-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="3efa2-112">Ponieważ `LogEntry` jest sparametryzowane przez dowolny typ, musi używać odbicia do działania na typie parametru.</span><span class="sxs-lookup"><span data-stu-id="3efa2-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="3efa2-113">Aby funkcja progu działała, typ `T` parametru musi <xref:System.IComparable> implementować interfejs.</span><span class="sxs-lookup"><span data-stu-id="3efa2-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="3efa2-114">Formularz, który `AttributesDemoControl` okresowo kieruje zapytania do licznika wydajności.</span><span class="sxs-lookup"><span data-stu-id="3efa2-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="3efa2-115">Każda wartość jest opakowana `LogEntry` do odpowiedniego typu i dodawana do <xref:System.Windows.Forms.BindingSource>formularza.</span><span class="sxs-lookup"><span data-stu-id="3efa2-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="3efa2-116">Odbiera wartość za pomocą powiązania danych i wyświetla wartość <xref:System.Windows.Forms.DataGridView> w kontrolce. `AttributesDemoControl`</span><span class="sxs-lookup"><span data-stu-id="3efa2-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="3efa2-117">Pierwszym przykładem kodu jest `AttributesDemoControl` implementacja.</span><span class="sxs-lookup"><span data-stu-id="3efa2-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="3efa2-118">Drugi przykład kodu demonstruje formularz, który używa `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="3efa2-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="3efa2-119">Atrybuty na poziomie klasy</span><span class="sxs-lookup"><span data-stu-id="3efa2-119">Class-level Attributes</span></span>  
 <span data-ttu-id="3efa2-120">Niektóre atrybuty są stosowane na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="3efa2-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="3efa2-121">Poniższy przykład kodu pokazuje atrybuty, które są powszechnie stosowane do formantu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3efa2-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="3efa2-122">TypeConverter — atrybut</span><span class="sxs-lookup"><span data-stu-id="3efa2-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="3efa2-123"><xref:System.ComponentModel.TypeConverterAttribute>jest innym powszechnie używanym atrybutem na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="3efa2-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="3efa2-124">Poniższy przykład kodu pokazuje jego użycie dla `LogEntry` klasy.</span><span class="sxs-lookup"><span data-stu-id="3efa2-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="3efa2-125">Ten przykład pokazuje również implementację <xref:System.ComponentModel.TypeConverter> `LogEntry` dla typu o nazwie `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="3efa2-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="3efa2-126">Atrybuty na poziomie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="3efa2-126">Member-level Attributes</span></span>  
 <span data-ttu-id="3efa2-127">Niektóre atrybuty są stosowane na poziomie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="3efa2-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="3efa2-128">Poniższe przykłady kodu pokazują pewne atrybuty, które są powszechnie stosowane do właściwości kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3efa2-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="3efa2-129">AmbientValue — atrybut</span><span class="sxs-lookup"><span data-stu-id="3efa2-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="3efa2-130">Poniższy przykład demonstruje <xref:System.ComponentModel.AmbientValueAttribute> i pokazuje kod, który obsługuje interakcje ze środowiskiem projektowym.</span><span class="sxs-lookup"><span data-stu-id="3efa2-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="3efa2-131">Ta interakcja jest nazywana *Ambience*.</span><span class="sxs-lookup"><span data-stu-id="3efa2-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="3efa2-132">Atrybuty wiązania danych</span><span class="sxs-lookup"><span data-stu-id="3efa2-132">Databinding Attributes</span></span>  
 <span data-ttu-id="3efa2-133">W poniższych przykładach przedstawiono implementację złożonego powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="3efa2-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="3efa2-134">Pokazany wcześniej poziom <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>klasy, `DataSource` określa właściwości i `DataMember` , które mają być używane do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="3efa2-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="3efa2-135">Określa typ, do `DataSource` którego zostanie powiązana właściwość. <xref:System.ComponentModel.AttributeProviderAttribute></span><span class="sxs-lookup"><span data-stu-id="3efa2-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3efa2-136">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3efa2-136">Compiling the Code</span></span>  
  
- <span data-ttu-id="3efa2-137">Formularz `AttributesDemoControl` obsługujący wymaga odwołania `AttributesDemoControl` do zestawu, aby można było go skompilować.</span><span class="sxs-lookup"><span data-stu-id="3efa2-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3efa2-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3efa2-138">See also</span></span>

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="3efa2-139">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3efa2-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="3efa2-140">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3efa2-140">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
- <span data-ttu-id="3efa2-141">[Instrukcje: Serializacja kolekcji typów standardowych z za pomocą DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="3efa2-141">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
