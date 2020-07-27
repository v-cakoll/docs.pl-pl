---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
description: Uzyskaj informacje na temat obsługi automatyzacji interfejsu użytkownika dla standardowych kontrolek w aplikacjach utworzonych dla Windows Presentation Foundation (WPF), Win32 i Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 17916a6978008439e91caae00d8b6f26045f9018
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166117"
---
# <a name="ui-automation-support-for-standard-controls"></a>Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera informacje o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsłudze standardowych formantów w aplikacjach opracowanych dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] środowisk, Win32 i Windows Forms.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a>Kontrolki Windows Presentation Foundation  
 Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy sterujące, które dostarczają informacji lub pomocy technicznej dla interakcji użytkownika, mają pełną obsługę natywną [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Inne elementy, takie jak panele, nie są widoczne dla programu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a>Kontrolki Win32  
 Większość formantów Win32 jest narażonych [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] przez dostawców po stronie klienta w UIAutomationClientsideProviders.dll. Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.  
  
 Pełna pomoc techniczna jest świadczona tylko w przypadku formantów z wersji 6 programu *ComCtrl32.dll*.  
  
 Obsługiwane są następujące kontrolki.  
  
|Nazwa klasy|Typ formantu|  
|----------------|------------------|  
|Przycisk|Przycisk|  
|Przycisk|RadioButton|  
|Przycisk|Grupa|  
|Przycisk|CheckBox|  
|Przycisk|Hyperlink|  
|Przycisk|SplitButton|  
|Przycisk|CheckBox|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Edytuj|Dokument|  
|Edytuj|Edytuj|  
|SysLink|Hyperlink|  
|Statyczny|Tekst|  
|Statyczny|Image (Obraz)|  
|SysIPAddress32|Niestandardowy|  
|SysHeader32|Nagłówek/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|Lista|  
|ListBox|Lista|  
|ListBox|Metodę|  
|#32768|Menu|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|Dokumentu. Zobacz Uwaga.|  
|RichEdit20A|Dokument|  
|RichEdit20W|Dokument|  
|RichEdit50W|Dokument|  
|ScrollBar|Slider|  
|msctls_trackbar32|Slider|  
|msctls_updown32|pokrętło|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Tab|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|Przycisk|  
|ToolbarWindow32|CheckBox|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Separator|  
|tooltips_class32|ToolTip|  
|#32774|ToolTip|  
|ReBarWindow32|Pasek narzędzi|  
|SysTreeView32|Drzewo|  
|SysTreeView32|TreeItem|  
  
 **Uwaga** Formant RichEdit jest obsługiwany tylko w przypadku wersji dostarczonych z systemem Windows Vista (w RichEd20.dll w wersji 3,1 lub nowszej oraz MsftEdit.dll wersji 4,1 i nowszych).  
  
 Następujące kontrolki nie są obsługiwane.  
  
|Nazwa klasy|Typ kontrolki|  
|----------------|------------------|  
|SysAnimate32|Image (Obraz)|  
|SysPager|pokrętło|  
|SysDateTimePick32|Niestandardowy|  
|SysMonthCal32|Kalendarz|  
|MS_WINNOTE|Etykietka narzędzia|  
|VBBubble|Etykietka narzędzia|  
|Pasek przewijania (używany jako formant autonomiczny)|Slider|  
|Podsiatka|Niestandardowy|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a>Formanty formularzy systemu Windows  
 Kontrolki Windows Forms są dostępne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dostawców po stronie klienta w programie UIAutomationClientsideProviders.dll. Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.  
  
 Zazwyczaj formanty Windows Forms, które są otokami zarządzanymi dla formantów standardowych Win32, są obsługiwane przez program [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Obsługiwane są następujące kontrolki.  
  
|Nazwa klasy|  
|----------------|  
|Przycisk|  
|CheckBox|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HscrollBar|  
|Obrazów|  
|Etykieta|  
|ListBox|  
|ListView|  
|MainMenu/|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|Elementu ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|Elementy TabControl/TabPage|  
|TextBox|  
|Czasomierz|  
|Pasek narzędzi|  
|ToolTip|  
|TrackBar|  
|TreeView|  
|VScrollBar —|  
|Kontrol|  
  
 Następujące kontrolki są dostępne [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tylko w ramach obsługi usługi Microsoft Active Accessibility. Niektóre funkcje mogą być niedostępne.  
  
|Nazwa kontrolki|  
|------------------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
|Nawigator datanavigator|  
|DomainUpDown|  
|ErrorProvider|  
|FlowLayoutPanel|  
|Formularz|  
|LinkLabel|  
|HelpProvider —|  
|Formantem MaskedTextBox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|Panel|  
|Elemencie|  
|PrintDocument|  
|PrintPreview — kontrolka|  
|PrintPreview — okno dialogowe|  
|Używany|  
|UserControl|  
|ToolStrip|  
|Element TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|Rozdzielacz|  
|Elemencie RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Zobacz także

- [Typy formantów automatyzacji interfejsu użytkownika](ui-automation-control-types.md)
