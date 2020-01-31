---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 49277073706444fd611ae41e762442388ac50b71
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789603"
---
# <a name="ui-automation-support-for-standard-controls"></a>Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera informacje dotyczące [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi standardowych formantów w aplikacjach opracowanych dla platform [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], Win32 i Windows Forms.  
  
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
|SysIPAddress32|Celnej|  
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
  
|Nazwa klasy|Typ formantu|  
|----------------|------------------|  
|SysAnimate32|Obraz|  
|SysPager|pokrętło|  
|SysDateTimePick32|Celnej|  
|SysMonthCal32|Kalendarz|  
|MS_WINNOTE|wyowietlon|  
|VBBubble|wyowietlon|  
|Pasek przewijania (używany jako formant autonomiczny)|Suwak|  
|Podsiatka|Celnej|  
  
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
|Dzielnik|  
|Elemencie RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Zobacz także

- [Typy kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-types.md)
