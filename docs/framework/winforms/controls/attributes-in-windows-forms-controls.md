---
title: Atrybuty w formantach formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
ms.openlocfilehash: e06836e53a69394ad899bedc8e545dbff9b9c29d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="attributes-in-windows-forms-controls"></a>Atrybuty w formantach formularzy systemu Windows
.NET Framework jest dostępnych wiele atrybutów, które można zastosować do elementów członkowskich niestandardowe formanty i składniki. Niektóre z tych atrybutów wpływają na zachowanie środowiska wykonawczego klasy, a inne mają wpływ na zachowanie czasu projektowania.  
  
## <a name="attributes-for-control-and-component-properties"></a>Atrybuty dla formantu i właściwości składnika  
 W poniższej tabeli przedstawiono atrybuty, które można zastosować do właściwości lub innych elementach członkowskich niestandardowe formanty i składniki. Na przykład, który używa wielu z tych atrybutów, zobacz [porady: zastosowanie atrybutów w formantach formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md).  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|Określa wartość do przekazania do właściwości spowodować właściwości do pobrania jego wartość z innego źródła. Jest to nazywane *otoczenie*.|  
|<xref:System.ComponentModel.BrowsableAttribute>|Określa, czy właściwość lub zdarzenie ma być wyświetlany w **właściwości** okna.|  
|<xref:System.ComponentModel.CategoryAttribute>|Określa nazwę kategorii służące do grupowania właściwość lub zdarzenie, gdy wyświetlany w <xref:System.Windows.Forms.PropertyGrid> kontroli ustawiona <xref:System.Windows.Forms.PropertySort.Categorized> tryb.|  
|<xref:System.ComponentModel.DefaultValueAttribute>|Określa wartość domyślną właściwości.|  
|<xref:System.ComponentModel.DescriptionAttribute>|Określa opis właściwości lub zdarzenia.|  
|<xref:System.ComponentModel.DisplayNameAttribute>|Określa nazwę wyświetlaną dla właściwości, zdarzenia lub `public``void` metodę, która nie przyjmuje żadnych argumentów.|  
|<xref:System.ComponentModel.EditorAttribute>|Określa użyć, aby zmienić właściwość w edytorze.|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|Określa, że właściwość lub metoda są widoczne w edytorze.|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|Słowo kluczowe kontekst dla klasy ani elementu członkowskiego.|  
|<xref:System.ComponentModel.LocalizableAttribute>|Określa, czy właściwość powinna być lokalizowany.|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|Wskazuje, że obiekt Reprezentacja tekstowa jest zostanie przesłonięty przez znaki, takie jak gwiazdki.|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|Określa, czy właściwość, którą jest powiązany ten atrybut jest tylko do odczytu lub odczytu/zapisu w czasie projektowania.|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|Wskazuje, że siatki właściwości należy odświeżyć, po zmianie wartości właściwości skojarzonej.|  
|<xref:System.ComponentModel.TypeConverterAttribute>|Określa, jaki typ ma być używana jako konwertera dla obiekt ten atrybut jest powiązany.|  
  
## <a name="attributes-for-data-binding-properties"></a>Atrybuty dla właściwości powiązania danych  
 W poniższej tabeli przedstawiono atrybuty, które można zastosować do określ sposób interakcji z niestandardowych kontrolek i składników z wiązania z danymi.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|Określa, czy właściwość jest zwykle używane dla wiązania.|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Określa źródło danych i właściwości elementu członkowskiego danych dla składnika.|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Określa domyślną właściwość powiązania dla składnika.|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Określa źródło danych i właściwości elementu członkowskiego danych dla składnika.|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|Umożliwia atrybutu przekierowania.|  
  
## <a name="attributes-for-classes"></a>Atrybuty klasy  
 W poniższej tabeli przedstawiono atrybuty, które można zastosować do określania zachowania niestandardowe formanty i składniki w czasie projektowania.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|Określa domyślne zdarzenie dla składnika.|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|Określa domyślną właściwość dla składnika.|  
|<xref:System.ComponentModel.DesignerAttribute>|Określa klasę, używaną do zaimplementowania usług czasu projektowania dla składnika.|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|Określa, że projektanta dla klasy należy do określonej kategorii.|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|Reprezentuje atrybut elementu przybornika.|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|Określa ciąg filtru i typ filtru dla elementu przybornika.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Attribute>  
 [Instrukcje: stosowanie atrybutów w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [Rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
