---
title: Powiązanie danych
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 68871db848ab46b88865e668f27f09972e8debcf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734610"
---
# <a name="windows-forms-data-binding"></a>Powiązywanie danych formularzy systemu Windows
Powiązanie danych w Windows Forms umożliwia wyświetlanie i wprowadzanie zmian w informacjach ze źródła danych w kontrolkach w formularzu. Można powiązać zarówno tradycyjne źródła danych, jak i prawie wszystkie struktury zawierające dane.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wiązanie danych i formularzy Windows Forms](data-binding-and-windows-forms.md)  
 Zawiera omówienie powiązań danych w Windows Forms.  
  
 [Źródła danych obsługiwane przez formularze Windows Forms](data-sources-supported-by-windows-forms.md)  
 Opisuje źródła danych, które mogą być używane z Windows Forms.  
  
 [Interfejsy dotyczące wiązania danych](interfaces-related-to-data-binding.md)  
 Opisuje kilka interfejsów używanych z Windows Forms powiązania danych.  
  
 [Instrukcje: nawigowanie po danych w formularzach Windows Forms](how-to-navigate-data-in-windows-forms.md)  
 Pokazuje, w jaki sposób nawigować przez elementy w źródle danych.  
  
 [Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms](change-notification-in-windows-forms-data-binding.md)  
 Opisuje różne typy powiadomień o zmianach dla Windows Forms powiązania danych.  
  
 [Instrukcje: implementowanie interfejsu INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md)  
 Pokazuje, jak zaimplementować interfejs <xref:System.ComponentModel.INotifyPropertyChanged>. Interfejs komunikuje się z kontrolką powiązaną ze zmianą właściwości w obiekcie biznesowym  
  
 [Instrukcje: stosowanie wzorca PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)  
 Pokazuje, jak zastosować wzorzec zmiany *PropertyName*do właściwości kontrolki użytkownika Windows Forms.  
  
 [Instrukcje: implementowanie interfejsu ITypedList](how-to-implement-the-itypedlist-interface.md)  
 Pokazuje, jak włączyć odnajdywanie schematu dla listy możliwej do powiązania przez implementację interfejsu <xref:System.ComponentModel.ITypedList>.  
  
 [Instrukcje: implementowanie interfejsu IListSource](how-to-implement-the-ilistsource-interface.md)  
 Pokazuje, w jaki sposób zaimplementować interfejs <xref:System.ComponentModel.IListSource> w celu utworzenia klasy możliwej do powiązania nie implementuje <xref:System.Collections.IList>, ale zawiera listę z innej lokalizacji.  
  
 [Instrukcje: zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych](multiple-controls-bound-to-data-source-synchronized.md)  
 Pokazuje, jak obsłużyć zdarzenie <xref:System.Windows.Forms.BindingSource.BindingComplete>, aby upewnić się, że wszystkie kontrolki powiązane ze źródłem danych pozostaną zsynchronizowane.  
  
 [Instrukcje: zapewnienie pozostawania wybranego wiersza w tabeli podrzędnej w prawidłowym położeniu](ensure-the-selected-row-in-a-child-table-correct.md)  
 Pokazuje, jak upewnić się, że wybrany wiersz tabeli podrzędnej nie zmienia się, gdy zostanie wprowadzona zmiana w polu tabeli nadrzędnej.  
  
 Zobacz również [interfejsy powiązane z powiązaniem danych](interfaces-related-to-data-binding.md), [instrukcje: nawigowanie po danych w Windows Forms](how-to-navigate-data-in-windows-forms.md)i [instrukcje: tworzenie prostej kontroli powiązanej w formularzu systemu Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md).  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 Opisuje klasę, która reprezentuje powiązanie między składnikiem możliwym do powiązania a źródłem danych.  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 Opisuje klasę, która hermetyzuje źródło danych dla powiązania z kontrolkami.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [BindingSource, składnik](./controls/bindingsource-component.md)  
 Zawiera listę tematów, w których pokazano, jak używać składnika <xref:System.Windows.Forms.BindingSource>.  
  
 [DataGridView, kontrolka](./controls/datagridview-control-windows-forms.md)  
 Zawiera listę tematów, które pokazują, jak używać kontrolki DataGrid możliwej do powiązania.  
  
 Zobacz też [dostęp do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).
