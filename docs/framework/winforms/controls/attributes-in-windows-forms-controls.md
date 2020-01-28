---
title: Atrybuty w kontrolkach
ms.date: 03/30/2017
helpviewer_keywords:
- attributes [Windows Forms]
- attributes [Windows Forms], data binding properties
- attributes [Windows Forms], control properties
- attributes [Windows Forms], classes
ms.assetid: 2c5640e9-6c6c-49d7-a5e4-a768f6be7853
ms.openlocfilehash: b32e4f87e953438a3bb11569445a9270e11c7922
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732126"
---
# <a name="attributes-in-windows-forms-controls"></a>Atrybuty w formantach formularzy systemu Windows
.NET Framework zawiera różne atrybuty, które można zastosować do elementów członkowskich niestandardowych formantów i składników. Niektóre z tych atrybutów wpływają na zachowanie klasy w czasie wykonywania, a inne mają wpływ na zachowanie w czasie projektowania.  
  
## <a name="attributes-for-control-and-component-properties"></a>Atrybuty kontrolki i właściwości składnika  
 W poniższej tabeli przedstawiono atrybuty, które można zastosować do właściwości lub innych elementów niestandardowych formantów i składników. Aby zapoznać się z przykładem, który używa wielu z tych atrybutów, zobacz [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.AmbientValueAttribute>|Określa wartość, która ma zostać przekazana do właściwości, aby spowodować, że właściwość pobierze jej wartość z innego źródła. Jest to tzw. *Ambience*.|  
|<xref:System.ComponentModel.BrowsableAttribute>|Określa, czy właściwość lub zdarzenie ma być wyświetlane w oknie **Właściwości** .|  
|<xref:System.ComponentModel.CategoryAttribute>|Określa nazwę kategorii, w której należy zgrupować właściwość lub zdarzenie, gdy jest wyświetlany w <xref:System.Windows.Forms.PropertyGrid> formantu ustawionym na tryb <xref:System.Windows.Forms.PropertySort.Categorized>.|  
|<xref:System.ComponentModel.DefaultValueAttribute>|Określa wartość domyślną właściwości.|  
|<xref:System.ComponentModel.DescriptionAttribute>|Określa opis właściwości lub zdarzenia.|  
|<xref:System.ComponentModel.DisplayNameAttribute>|Określa nazwę wyświetlaną dla właściwości, zdarzenia lub `public void` metody, która nie przyjmuje argumentów.|  
|<xref:System.ComponentModel.EditorAttribute>|Określa edytor używany do zmiany właściwości.|  
|<xref:System.ComponentModel.EditorBrowsableAttribute>|Określa, że właściwość lub metoda jest widoczna w edytorze.|  
|<xref:System.ComponentModel.Design.HelpKeywordAttribute>|Określa słowo kluczowe kontekstu dla klasy lub składowej.|  
|<xref:System.ComponentModel.LocalizableAttribute>|Określa, czy właściwość powinna być zlokalizowana.|  
|<xref:System.ComponentModel.PasswordPropertyTextAttribute>|Wskazuje, że reprezentacja tekstu obiektu jest zasłonięta znakami, takimi jak gwiazdki.|  
|<xref:System.ComponentModel.ReadOnlyAttribute>|Określa, czy właściwość, z którą jest powiązany ten atrybut jest tylko do odczytu, czy odczytu/zapisu w czasie projektowania.|  
|<xref:System.ComponentModel.RefreshPropertiesAttribute>|Wskazuje, że siatka właściwości ma być odświeżana, gdy zostanie zmieniona skojarzona wartość właściwości.|  
|<xref:System.ComponentModel.TypeConverterAttribute>|Określa typ, który ma być używany jako konwerter dla obiektu, z którym jest powiązany ten atrybut.|  
  
## <a name="attributes-for-data-binding-properties"></a>Atrybuty właściwości powiązań danych  
 W poniższej tabeli przedstawiono atrybuty, które można zastosować, aby określić sposób działania formantów niestandardowych i składników z powiązaniem danych.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.BindableAttribute>|Określa, czy właściwość jest zazwyczaj używana do wiązania.|  
|<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Określa właściwości źródła danych i elementu członkowskiego danych dla składnika.|  
|<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Określa domyślną właściwość powiązania dla składnika.|  
|<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Określa właściwości źródła danych i elementu członkowskiego danych dla składnika.|  
|<xref:System.ComponentModel.AttributeProviderAttribute>|Włącza przekierowywanie atrybutów.|  
  
## <a name="attributes-for-classes"></a>Atrybuty klas  
 W poniższej tabeli przedstawiono atrybuty, które można zastosować, aby określić zachowanie niestandardowych kontrolek i składników w czasie projektowania.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|<xref:System.ComponentModel.DefaultEventAttribute>|Określa domyślne zdarzenie dla składnika.|  
|<xref:System.ComponentModel.DefaultPropertyAttribute>|Określa właściwość domyślną dla składnika.|  
|<xref:System.ComponentModel.DesignerAttribute>|Określa klasę używaną do implementowania usług czasu projektowania dla składnika.|  
|<xref:System.ComponentModel.DesignerCategoryAttribute>|Określa, że Projektant klasy należy do pewnej kategorii.|  
|<xref:System.ComponentModel.ToolboxItemAttribute>|Reprezentuje atrybut elementu przybornika.|  
|<xref:System.ComponentModel.ToolboxItemFilterAttribute>|Określa ciąg filtru i typ filtru, który ma być używany dla elementu przybornika.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Attribute>
- [Instrukcje: stosowanie atrybutów w kontrolkach formularzy Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md)
- [Rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
