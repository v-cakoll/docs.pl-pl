---
title: Zastosuj atrybuty w kontrolkach
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: b8ecd516cf6bb189c6ad1b208dd8e3a5444f001c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741496"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a><span data-ttu-id="86e15-102">Porady: stosowanie atrybutów w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="86e15-102">How to: Apply Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="86e15-103">Aby opracować składniki i formanty współdziałające prawidłowo ze środowiskiem projektowym i działać prawidłowo w czasie wykonywania, należy prawidłowo zastosować atrybuty do klas i elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="86e15-103">To develop components and controls that interact correctly with the design environment and execute correctly at run time, you need to apply attributes correctly to classes and members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86e15-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="86e15-104">Example</span></span>  
 <span data-ttu-id="86e15-105">Poniższy przykład kodu demonstruje, jak używać kilku atrybutów w kontrolce niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="86e15-105">The following code example demonstrates how to use several attributes on a custom control.</span></span> <span data-ttu-id="86e15-106">Kontrolka pokazuje prostą funkcję rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="86e15-106">The control demonstrates a simple logging capability.</span></span> <span data-ttu-id="86e15-107">Gdy formant jest powiązany ze źródłem danych, wyświetla wartości wysyłane przez źródło danych w kontrolce <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="86e15-107">When the control is bound to a data source, it displays the values sent by the data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="86e15-108">Jeśli wartość przekroczy wartość określoną przez właściwość `Threshold`, zostanie zgłoszone zdarzenie `ThresholdExceeded`.</span><span class="sxs-lookup"><span data-stu-id="86e15-108">If a value exceeds the value specified by the `Threshold` property, a `ThresholdExceeded` event is raised.</span></span>  
  
 <span data-ttu-id="86e15-109">`AttributesDemoControl` rejestruje wartości z klasą `LogEntry`.</span><span class="sxs-lookup"><span data-stu-id="86e15-109">The `AttributesDemoControl` logs values with a `LogEntry` class.</span></span> <span data-ttu-id="86e15-110">Klasa `LogEntry` jest klasą szablonu, co oznacza, że jest sparametryzowane dla typu, który rejestruje.</span><span class="sxs-lookup"><span data-stu-id="86e15-110">The `LogEntry` class is a template class, which means it is parameterized on the type that it logs.</span></span> <span data-ttu-id="86e15-111">Na przykład jeśli `AttributesDemoControl` rejestruje wartości typu `float`, każde wystąpienie `LogEntry` jest zadeklarowane i używane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="86e15-111">For example, if the `AttributesDemoControl` is logging values of type `float`, each `LogEntry` instance is declared and used as follows.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="86e15-112">Ponieważ `LogEntry` jest sparametryzowane przez dowolny typ, musi używać odbicia do operowania na typie parametru.</span><span class="sxs-lookup"><span data-stu-id="86e15-112">Because `LogEntry` is parameterized by an arbitrary type, it must use reflection to operate on the parameter type.</span></span> <span data-ttu-id="86e15-113">Aby funkcja progu działała, typ parametru `T` musi implementować interfejs <xref:System.IComparable>.</span><span class="sxs-lookup"><span data-stu-id="86e15-113">For the threshold feature to work, the parameter type `T` must implement the <xref:System.IComparable> interface.</span></span>  
  
 <span data-ttu-id="86e15-114">Formularz, który hostuje `AttributesDemoControl` wysyła zapytanie do licznika wydajności okresowo.</span><span class="sxs-lookup"><span data-stu-id="86e15-114">The form that hosts the `AttributesDemoControl` queries a performance counter periodically.</span></span> <span data-ttu-id="86e15-115">Każda wartość jest pakowana w `LogEntry` odpowiedniego typu i dodawane do <xref:System.Windows.Forms.BindingSource>formularza.</span><span class="sxs-lookup"><span data-stu-id="86e15-115">Each value is packaged in a `LogEntry` of the appropriate type and added to the form's <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="86e15-116">`AttributesDemoControl` otrzymuje wartość za pomocą powiązania danych i wyświetla wartość w kontrolce <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="86e15-116">The `AttributesDemoControl` receives the value through its data binding and displays the value in a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 <span data-ttu-id="86e15-117">Pierwszy przykład kodu jest implementacją `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="86e15-117">The first code example is the `AttributesDemoControl` implementation.</span></span> <span data-ttu-id="86e15-118">Drugi przykład kodu demonstruje formularz, który używa `AttributesDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="86e15-118">The second code example demonstrates a form that uses the `AttributesDemoControl`.</span></span>  
  
## <a name="class-level-attributes"></a><span data-ttu-id="86e15-119">Atrybuty na poziomie klasy</span><span class="sxs-lookup"><span data-stu-id="86e15-119">Class-level Attributes</span></span>  
 <span data-ttu-id="86e15-120">Niektóre atrybuty są stosowane na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="86e15-120">Some attributes are applied at the class level.</span></span> <span data-ttu-id="86e15-121">Poniższy przykład kodu pokazuje atrybuty, które są powszechnie stosowane do formantu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="86e15-121">The following code example shows the attributes that are commonly applied to a Windows Forms control.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a><span data-ttu-id="86e15-122">TypeConverter — atrybut</span><span class="sxs-lookup"><span data-stu-id="86e15-122">TypeConverter Attribute</span></span>  
 <span data-ttu-id="86e15-123"><xref:System.ComponentModel.TypeConverterAttribute> jest innym powszechnie używanym atrybutem na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="86e15-123"><xref:System.ComponentModel.TypeConverterAttribute> is another commonly used class-level attribute.</span></span> <span data-ttu-id="86e15-124">Poniższy przykład kodu pokazuje jego użycie dla klasy `LogEntry`.</span><span class="sxs-lookup"><span data-stu-id="86e15-124">The following code example shows its use for the `LogEntry` class.</span></span> <span data-ttu-id="86e15-125">W tym przykładzie przedstawiono również implementację <xref:System.ComponentModel.TypeConverter> typu `LogEntry` o nazwie `LogEntryTypeConverter`.</span><span class="sxs-lookup"><span data-stu-id="86e15-125">This example also shows an implementation of a <xref:System.ComponentModel.TypeConverter> for the `LogEntry` type, called `LogEntryTypeConverter`.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a><span data-ttu-id="86e15-126">Atrybuty na poziomie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="86e15-126">Member-level Attributes</span></span>  
 <span data-ttu-id="86e15-127">Niektóre atrybuty są stosowane na poziomie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="86e15-127">Some attributes are applied at the member level.</span></span> <span data-ttu-id="86e15-128">Poniższe przykłady kodu pokazują pewne atrybuty, które są powszechnie stosowane do właściwości kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="86e15-128">The following code examples show some attributes that are commonly applied to properties of Windows Forms controls.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a><span data-ttu-id="86e15-129">AmbientValue — atrybut</span><span class="sxs-lookup"><span data-stu-id="86e15-129">AmbientValue Attribute</span></span>  
 <span data-ttu-id="86e15-130">Poniższy przykład ilustruje <xref:System.ComponentModel.AmbientValueAttribute> i pokazuje kod, który obsługuje interakcje ze środowiskiem projektowym.</span><span class="sxs-lookup"><span data-stu-id="86e15-130">The following example demonstrates the <xref:System.ComponentModel.AmbientValueAttribute> and shows code that supports its interaction with the design environment.</span></span> <span data-ttu-id="86e15-131">Ta interakcja jest nazywana *Ambience*.</span><span class="sxs-lookup"><span data-stu-id="86e15-131">This interaction is called *ambience*.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a><span data-ttu-id="86e15-132">Atrybuty wiązania danych</span><span class="sxs-lookup"><span data-stu-id="86e15-132">Databinding Attributes</span></span>  
 <span data-ttu-id="86e15-133">W poniższych przykładach przedstawiono implementację złożonego powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="86e15-133">The following examples demonstrate an implementation of complex data binding.</span></span> <span data-ttu-id="86e15-134"><xref:System.ComponentModel.ComplexBindingPropertiesAttribute>na poziomie klasy, pokazane wcześniej, określa `DataSource` i `DataMember` właściwości, które mają być używane do wiązania danych.</span><span class="sxs-lookup"><span data-stu-id="86e15-134">The class-level <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, shown previously, specifies the `DataSource` and `DataMember` properties to use for data binding.</span></span> <span data-ttu-id="86e15-135"><xref:System.ComponentModel.AttributeProviderAttribute> określa typ, do którego zostanie powiązana właściwość `DataSource`.</span><span class="sxs-lookup"><span data-stu-id="86e15-135">The <xref:System.ComponentModel.AttributeProviderAttribute> specifies the type to which the `DataSource` property will bind.</span></span>  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="86e15-136">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="86e15-136">Compiling the Code</span></span>  
  
- <span data-ttu-id="86e15-137">Formularz, który hostuje `AttributesDemoControl` wymaga odwołania do zestawu `AttributesDemoControl` w celu skompilowania.</span><span class="sxs-lookup"><span data-stu-id="86e15-137">The form that hosts the `AttributesDemoControl` requires a reference to the `AttributesDemoControl` assembly in order to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e15-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86e15-138">See also</span></span>

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="86e15-139">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="86e15-139">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="86e15-140">Atrybuty w kontrolkach formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="86e15-140">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)
- <span data-ttu-id="86e15-141">[Instrukcje: serializacja kolekcji typów standardowych przy użyciu za pomocą DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="86e15-141">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
