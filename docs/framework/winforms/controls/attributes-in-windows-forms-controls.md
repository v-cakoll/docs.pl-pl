---
title: Atrybuty w formantach formularzy systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 21f39aa1f85e06f1967d278e07731b73dcf7cb10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="attributes-in-windows-forms-controls"></a><span data-ttu-id="2e45f-102">Atrybuty w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2e45f-102">Attributes in Windows Forms Controls</span></span>
<span data-ttu-id="2e45f-103">.NET Framework jest dostępnych wiele atrybutów, które można zastosować do elementów członkowskich niestandardowe formanty i składniki.</span><span class="sxs-lookup"><span data-stu-id="2e45f-103">The .NET Framework provides a variety of attributes you can apply to the members of your custom controls and components.</span></span> <span data-ttu-id="2e45f-104">Niektóre z tych atrybutów wpływają na zachowanie środowiska wykonawczego klasy, a inne mają wpływ na zachowanie czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="2e45f-104">Some of these attributes affect the run-time behavior of a class, and others affect the design-time behavior.</span></span>  
  
## <a name="attributes-for-control-and-component-properties"></a><span data-ttu-id="2e45f-105">Atrybuty dla formantu i właściwości składnika</span><span class="sxs-lookup"><span data-stu-id="2e45f-105">Attributes for Control and Component Properties</span></span>  
 <span data-ttu-id="2e45f-106">W poniższej tabeli przedstawiono atrybuty, które można zastosować do właściwości lub innych elementach członkowskich niestandardowe formanty i składniki.</span><span class="sxs-lookup"><span data-stu-id="2e45f-106">The following table shows the attributes you can apply to properties or other members of your custom controls and components.</span></span> <span data-ttu-id="2e45f-107">Na przykład, który używa wielu z tych atrybutów, zobacz [porady: zastosowanie atrybutów w formantach formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="2e45f-107">For an example that uses many of these attributes, see [How to: Apply Attributes in Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).</span></span>  
  
|<span data-ttu-id="2e45f-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2e45f-108">Attribute</span></span>|<span data-ttu-id="2e45f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2e45f-109">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|<span data-ttu-id="2e45f-110">Określa wartość do przekazania do właściwości spowodować właściwości do pobrania jego wartość z innego źródła.</span><span class="sxs-lookup"><span data-stu-id="2e45f-110">Specifies the value to pass to a property to cause the property to get its value from another source.</span></span> <span data-ttu-id="2e45f-111">Jest to nazywane *otoczenie*.</span><span class="sxs-lookup"><span data-stu-id="2e45f-111">This is known as *ambience*.</span></span>|  
|<xref:System.ComponentModel.BrowsableAttribute>|<span data-ttu-id="2e45f-112">Określa, czy właściwość lub zdarzenie ma być wyświetlany w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="2e45f-112">Specifies whether a property or event should be displayed in a **Properties** window.</span></span>|  
|<xref:System.ComponentModel.CategoryAttribute>|<span data-ttu-id="2e45f-113">Określa nazwę kategorii służące do grupowania właściwość lub zdarzenie, gdy wyświetlany w <xref:System.Windows.Forms.PropertyGrid> kontroli ustawiona <xref:System.Windows.Forms.PropertySort.Categorized> tryb.</span><span class="sxs-lookup"><span data-stu-id="2e45f-113">Specifies the name of the category in which to group the property or event when displayed in a <xref:System.Windows.Forms.PropertyGrid> control set to <xref:System.Windows.Forms.PropertySort.Categorized> mode.</span></span>|  
|<xref:System.ComponentModel.DefaultValueAttribute>|<span data-ttu-id="2e45f-114">Określa wartość domyślną właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e45f-114">Specifies the default value for a property.</span></span>|  
|<xref:System.ComponentModel.DescriptionAttribute>|<span data-ttu-id="2e45f-115">Określa opis właściwości lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2e45f-115">Specifies a description for a property or event.</span></span>|  
|<xref:System.ComponentModel.DisplayNameAttribute>|<span data-ttu-id="2e45f-116">Określa nazwę wyświetlaną dla właściwości, zdarzenia lub `public``void` metodę, która nie przyjmuje żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="2e45f-116">Specifies the display name for a property, event, or `public``void` method that takes no arguments.</span></span>|  
|<xref:System.ComponentModel.EditorAttribute>|<span data-ttu-id="2e45f-117">Określa użyć, aby zmienić właściwość w edytorze.</span><span class="sxs-lookup"><span data-stu-id="2e45f-117">Specifies the editor to use to change a property.</span></span>|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|<span data-ttu-id="2e45f-118">Określa, że właściwość lub metoda są widoczne w edytorze.</span><span class="sxs-lookup"><span data-stu-id="2e45f-118">Specifies that a property or method is viewable in an editor.</span></span>|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|<span data-ttu-id="2e45f-119">Słowo kluczowe kontekst dla klasy ani elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="2e45f-119">Specifies the context keyword for a class or member.</span></span>|  
|<xref:System.ComponentModel.LocalizableAttribute>|<span data-ttu-id="2e45f-120">Określa, czy właściwość powinna być lokalizowany.</span><span class="sxs-lookup"><span data-stu-id="2e45f-120">Specifies whether a property should be localized.</span></span>|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|<span data-ttu-id="2e45f-121">Wskazuje, że obiekt Reprezentacja tekstowa jest zostanie przesłonięty przez znaki, takie jak gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="2e45f-121">Indicates that an object's text representation is obscured by characters such as asterisks.</span></span>|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|<span data-ttu-id="2e45f-122">Określa, czy właściwość, którą jest powiązany ten atrybut jest tylko do odczytu lub odczytu/zapisu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="2e45f-122">Specifies whether the property this attribute is bound to is read-only or read/write at design time.</span></span>|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|<span data-ttu-id="2e45f-123">Wskazuje, że siatki właściwości należy odświeżyć, po zmianie wartości właściwości skojarzonej.</span><span class="sxs-lookup"><span data-stu-id="2e45f-123">Indicates that the property grid should refresh when the associated property value changes.</span></span>|  
|<xref:System.ComponentModel.TypeConverterAttribute>|<span data-ttu-id="2e45f-124">Określa, jaki typ ma być używana jako konwertera dla obiekt ten atrybut jest powiązany.</span><span class="sxs-lookup"><span data-stu-id="2e45f-124">Specifies what type to use as a converter for the object this attribute is bound to.</span></span>|  
  
## <a name="attributes-for-data-binding-properties"></a><span data-ttu-id="2e45f-125">Atrybuty dla właściwości powiązania danych</span><span class="sxs-lookup"><span data-stu-id="2e45f-125">Attributes for Data Binding Properties</span></span>  
 <span data-ttu-id="2e45f-126">W poniższej tabeli przedstawiono atrybuty, które można zastosować do określ sposób interakcji z niestandardowych kontrolek i składników z wiązania z danymi.</span><span class="sxs-lookup"><span data-stu-id="2e45f-126">The following table shows the attributes you can apply to specify how your custom controls and components interact with data binding.</span></span>  
  
|<span data-ttu-id="2e45f-127">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2e45f-127">Attribute</span></span>|<span data-ttu-id="2e45f-128">Opis</span><span class="sxs-lookup"><span data-stu-id="2e45f-128">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|<span data-ttu-id="2e45f-129">Określa, czy właściwość jest zwykle używane dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="2e45f-129">Specifies whether a property is typically used for binding.</span></span>|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|<span data-ttu-id="2e45f-130">Określa źródło danych i właściwości elementu członkowskiego danych dla składnika.</span><span class="sxs-lookup"><span data-stu-id="2e45f-130">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|<span data-ttu-id="2e45f-131">Określa domyślną właściwość powiązania dla składnika.</span><span class="sxs-lookup"><span data-stu-id="2e45f-131">Specifies the default binding property for a component.</span></span>|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|<span data-ttu-id="2e45f-132">Określa źródło danych i właściwości elementu członkowskiego danych dla składnika.</span><span class="sxs-lookup"><span data-stu-id="2e45f-132">Specifies the data source and data member properties for a component.</span></span>|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|<span data-ttu-id="2e45f-133">Umożliwia atrybutu przekierowania.</span><span class="sxs-lookup"><span data-stu-id="2e45f-133">Enables attribute redirection.</span></span>|  
  
## <a name="attributes-for-classes"></a><span data-ttu-id="2e45f-134">Atrybuty klasy</span><span class="sxs-lookup"><span data-stu-id="2e45f-134">Attributes for Classes</span></span>  
 <span data-ttu-id="2e45f-135">W poniższej tabeli przedstawiono atrybuty, które można zastosować do określania zachowania niestandardowe formanty i składniki w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="2e45f-135">The following table shows the attributes you can apply to specify the behavior of your custom controls and components at design time.</span></span>  
  
|<span data-ttu-id="2e45f-136">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2e45f-136">Attribute</span></span>|<span data-ttu-id="2e45f-137">Opis</span><span class="sxs-lookup"><span data-stu-id="2e45f-137">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|<span data-ttu-id="2e45f-138">Określa domyślne zdarzenie dla składnika.</span><span class="sxs-lookup"><span data-stu-id="2e45f-138">Specifies the default event for a component.</span></span>|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|<span data-ttu-id="2e45f-139">Określa domyślną właściwość dla składnika.</span><span class="sxs-lookup"><span data-stu-id="2e45f-139">Specifies the default property for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerAttribute>|<span data-ttu-id="2e45f-140">Określa klasę, używaną do zaimplementowania usług czasu projektowania dla składnika.</span><span class="sxs-lookup"><span data-stu-id="2e45f-140">Specifies the class used to implement design-time services for a component.</span></span>|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|<span data-ttu-id="2e45f-141">Określa, że projektanta dla klasy należy do określonej kategorii.</span><span class="sxs-lookup"><span data-stu-id="2e45f-141">Specifies that the designer for a class belongs to a certain category.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|<span data-ttu-id="2e45f-142">Reprezentuje atrybut elementu przybornika.</span><span class="sxs-lookup"><span data-stu-id="2e45f-142">Represents an attribute of a toolbox item.</span></span>|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|<span data-ttu-id="2e45f-143">Określa ciąg filtru i typ filtru dla elementu przybornika.</span><span class="sxs-lookup"><span data-stu-id="2e45f-143">Specifies the filter string and filter type to use for a Toolbox item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e45f-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e45f-144">See Also</span></span>  
 <xref:System.Attribute>  
 [<span data-ttu-id="2e45f-145">Porady: stosowanie atrybutów w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2e45f-145">How to: Apply Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [<span data-ttu-id="2e45f-146">Rozszerzenie obsługi w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="2e45f-146">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [<span data-ttu-id="2e45f-147">Opracowywanie niestandardowych formularzy systemu Windows formantów za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2e45f-147">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
