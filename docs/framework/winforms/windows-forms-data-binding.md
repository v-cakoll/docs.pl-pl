---
title: Powiązanie danych
description: Dowiedz się, jak używać powiązań danych w Windows Forms, aby wyświetlać i wprowadzać zmiany w informacjach ze źródła danych w kontrolkach w formularzu.
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 3dfce24147caf9b138916ca8dc3b7a9010439f58
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325542"
---
# <a name="windows-forms-data-binding"></a>Powiązywanie danych formularzy systemu Windows
Powiązanie danych w Windows Forms umożliwia wyświetlanie i wprowadzanie zmian w informacjach ze źródła danych w kontrolkach w formularzu. Można powiązać zarówno tradycyjne źródła danych, jak i prawie wszystkie struktury zawierające dane.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wiązanie danych i formularze systemu Windows](data-binding-and-windows-forms.md)  
 Zawiera omówienie powiązań danych w Windows Forms.  
  
 [Źródła danych obsługiwane przez formularze systemu Windows](data-sources-supported-by-windows-forms.md)  
 Opisuje źródła danych, które mogą być używane z Windows Forms.  
  
 [Interfejsy dotyczące wiązania danych](interfaces-related-to-data-binding.md)  
 Opisuje kilka interfejsów używanych z Windows Forms powiązania danych.  
  
 [Instrukcje: Nawigowanie po danych w formularzach Windows Forms](how-to-navigate-data-in-windows-forms.md)  
 Pokazuje, w jaki sposób nawigować przez elementy w źródle danych.  
  
 [Powiadomienie o zmianie w powiązaniu danych w formularzach systemu Windows](change-notification-in-windows-forms-data-binding.md)  
 Opisuje różne typy powiadomień o zmianach dla Windows Forms powiązania danych.  
  
 [Instrukcje: Implementowanie interfejsu INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md)  
 Pokazuje, jak zaimplementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejs. Interfejs komunikuje się z kontrolką powiązaną ze zmianą właściwości w obiekcie biznesowym  
  
 [Instrukcje: Stosowanie wzorca PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)  
 Pokazuje, jak zastosować wzorzec zmiany *PropertyName*do właściwości kontrolki użytkownika Windows Forms.  
  
 [Instrukcje: Implementowanie interfejsu ITypedList](how-to-implement-the-itypedlist-interface.md)  
 Pokazuje, jak włączyć odnajdywanie schematu dla listy możliwej do powiązania przez implementację <xref:System.ComponentModel.ITypedList> interfejsu.  
  
 [Instrukcje: Implementowanie interfejsu IListSource](how-to-implement-the-ilistsource-interface.md)  
 Pokazuje, jak zaimplementować <xref:System.ComponentModel.IListSource> interfejs do tworzenia klasy możliwej do powiązania nie implementuje <xref:System.Collections.IList> , ale zawiera listę z innej lokalizacji.  
  
 [Instrukcje: Zapewnienie synchronizacji wiązania wielu kontrolek z jednym źródłem danych](multiple-controls-bound-to-data-source-synchronized.md)  
 Pokazuje, jak obsłużyć <xref:System.Windows.Forms.BindingSource.BindingComplete> zdarzenie, aby upewnić się, że wszystkie kontrolki powiązane ze źródłem danych pozostaną zsynchronizowane.  
  
 [Instrukcje: Zapewnienie pozostawania wybranego wiersza w tabeli podrzędnej w prawidłowym położeniu](ensure-the-selected-row-in-a-child-table-correct.md)  
 Pokazuje, jak upewnić się, że wybrany wiersz tabeli podrzędnej nie zmienia się, gdy zostanie wprowadzona zmiana w polu tabeli nadrzędnej.  
  
 Zobacz również [interfejsy powiązane z powiązaniem danych](interfaces-related-to-data-binding.md), [instrukcje: nawigowanie po danych w Windows Forms](how-to-navigate-data-in-windows-forms.md)i [instrukcje: tworzenie prostej kontroli powiązanej w formularzu systemu Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md).  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 Opisuje klasę, która reprezentuje powiązanie między składnikiem możliwym do powiązania a źródłem danych.  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 Opisuje klasę, która hermetyzuje źródło danych dla powiązania z kontrolkami.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [BindingSource, składnik](./controls/bindingsource-component.md)  
 Zawiera listę tematów, które pokazują, jak używać <xref:System.Windows.Forms.BindingSource> składnika.  
  
 [DataGridView — Formant](./controls/datagridview-control-windows-forms.md)  
 Zawiera listę tematów, które pokazują, jak używać kontrolki DataGrid możliwej do powiązania.  
  
 Zobacz też [dostęp do danych w programie Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).
