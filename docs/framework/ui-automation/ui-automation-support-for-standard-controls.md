---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: ed5e4f6ab23fe9ae77c94616a668da8accb46d4b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741700"
---
# <a name="ui-automation-support-for-standard-controls"></a>Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera informacje dotyczące [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi standardowych formantów w aplikacjach opracowanych dla platform [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32 i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Kontrolki Windows Presentation Foundation  
 Wszystkie elementy formantu [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], które zapewniają informacje lub pomoc techniczną dla interakcji użytkownika, mają pełną natywną obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Inne elementy, takie jak panele, nie są widoczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Kontrolki Win32  
 Większość formantów Win32 jest narażonych na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za poorednictwem dostawców po stronie klienta w UIAutomationClientsideProviders. dll. Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.  
  
 Pełna pomoc techniczna jest świadczona tylko dla formantów z wersji 6 programu *ComCtrl32. dll*.  
  
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
|Edytowanie|dokument|  
|Edytowanie|Edytowanie|  
|SysLink|Hyperlink|  
|Static|Tekst|  
|Static|Obraz|  
|SysIPAddress32|Niestandardowe|  
|SysHeader32|Nagłówek/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|Lista|  
|ListBox|Lista|  
|ListBox|ListItem|  
|#32768|Menu|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|Dokumentu. Zobacz Uwaga.|  
|RichEdit20A|dokument|  
|RichEdit20W|dokument|  
|RichEdit50W|dokument|  
|ScrollBar|Suwak|  
|msctls_trackbar32|Suwak|  
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
  
 **Uwaga** Formant RichEdit jest obsługiwany tylko w przypadku wersji dostarczonych z systemem Windows Vista (w biblioteki riched20. dll w wersji 3,1 i nowszych oraz MsftEdit. dll w wersji 4,1 i nowszych).  
  
 Następujące kontrolki nie są obsługiwane.  
  
|Nazwa klasy|Typ kontrolki|  
|----------------|------------------|  
|SysAnimate32|Obraz|  
|SysPager|pokrętło|  
|SysDateTimePick32|Niestandardowe|  
|SysMonthCal32|Kalendarz|  
|MS_WINNOTE|Etykietka narzędzia|  
|VBBubble|Etykietka narzędzia|  
|Pasek przewijania (używany jako formant autonomiczny)|Suwak|  
|Podsiatka|Niestandardowe|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Formanty formularzy systemu Windows  
 Kontrolki Windows Forms są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za poorednictwem dostawców po stronie klienta w UIAutomationClientsideProviders. dll. Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.  
  
 Zazwyczaj Windows Forms formantów, które są otokami zarządzanymi dla formantów standardowych Win32, są obsługiwane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Obsługiwane są następujące kontrolki.  
  
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
  
 Następujące kontrolki są dostępne do [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tylko w ramach obsługi usługi Microsoft Active Accessibility. Niektóre funkcje mogą być niedostępne.  
  
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
|HelpProvider|  
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
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|Rozdzielacz|  
|Elemencie RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Zobacz także

- [Typy kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-types.md)
