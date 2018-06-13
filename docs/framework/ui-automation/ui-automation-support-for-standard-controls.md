---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3ccd6e1348125f5d901e0f093d2b5483b818719f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409094"
---
# <a name="ui-automation-support-for-standard-controls"></a>Obsługa automatyzacji interfejsu użytkownika dla standardowych kontrolek
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsługi dla standardowych formantów w aplikacjach przeznaczonych dla [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] struktury.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Windows Presentation Foundation formantów  
 Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy kontroli, które udostępniają informacje lub pomocy technicznej do interakcji z użytkownikiem mają pełną natywną obsługę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Nie są widoczne dla innych elementów, takich jak panele, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Formanty Win32  
 Większość [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formanty są widoczne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll. Ten zestaw jest automatycznie dodawane do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.  
  
 Pełna obsługa jest udostępniany tylko dla formantów z ComCtrl32.dll w wersji 6 (dostępnych z [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] i nowsze).  
  
 Obsługiwane są następujące formanty.  
  
|Nazwa klasy|Typ formantu|  
|----------------|------------------|  
|Przycisk|Przycisk|  
|Przycisk|RadioButton|  
|Przycisk|Grupa|  
|Przycisk|CheckBox|  
|Przycisk|Hyperlink|  
|Przycisk|Przycisk podziału|  
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
|#32768|Element MenuItem|  
|msctls_progress32|ProgressBar|  
|RichEdit|dokument. Zobacz uwagi.|  
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
|ToolbarWindow32|Element MenuItem|  
|ToolbarWindow32|Przycisk|  
|ToolbarWindow32|CheckBox|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Separator|  
|tooltips_class32|ToolTip|  
|#32774|ToolTip|  
|ReBarWindow32|Pasek narzędzi|  
|SysTreeView32|Drzewo|  
|SysTreeView32|TreeItem|  
  
 **Uwaga** formantu RichEdit jest obsługiwana tylko dla wersji dostarczone z [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] (w wersji biblioteki RichEd20.dll 3.1 lub nowszy, a MsftEdit.dll wersji 4.1 i nowszych).  
  
 Następujące formanty nie są obsługiwane.  
  
|Nazwa klasy|Typ formantu|  
|----------------|------------------|  
|SysAnimate32|Obraz|  
|SysPager|pokrętło|  
|SysDateTimePick32|Niestandardowe|  
|SysMonthCal32|Kalendarz|  
|MS_WINNOTE|Etykietka narzędzia|  
|VBBubble|Etykietka narzędzia|  
|Pasek przewijania (jeśli jest używany jako formant autonomiczne)|Suwak|  
|SuperGrid|Niestandardowe|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Formanty formularzy systemu Windows  
 Formanty formularzy systemu Windows są widoczne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawcy po stronie klienta w UIAutomationClientsideProviders.dll. Ten zestaw jest automatycznie dodawane do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.  
  
 Zazwyczaj formanty formularzy systemu Windows, które są zarządzane otoki [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formanty standardowe są obsługiwane przez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Obsługiwane są następujące formanty.  
  
|Nazwa klasy|  
|----------------|  
|Przycisk|  
|CheckBox|  
|CheckedListBox —|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HscrollBar|  
|Listy obrazów|  
|Etykieta|  
|ListBox|  
|ListView|  
|MainMenu — / ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog —|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|Elementu ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl — / TabPage|  
|TextBox|  
|Czasomierz|  
|Pasek narzędzi|  
|ToolTip|  
|TrackBar|  
|TreeView|  
|Vscrollbar —|  
|WebBrowser|  
  
 Następujące sterowniki są widoczne dla [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tylko za pośrednictwem ich obsługę [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. Niektóre funkcje mogą nie być dostępne.  
  
|Nazwa formantu|  
|------------------|  
|BindingSource|  
|DataGrid|  
|Formant DataGridView|  
|DataNavigator|  
|DomainUpDown|  
|ErrorProvider|  
|FlowLayoutPanel|  
|Formularz|  
|LinkLabel|  
|Helpprovider —|  
|MaskedTextBox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|Panel|  
|PictureBox|  
|PrintDocument —|  
|Printpreview — formant|  
|Printpreview — okno dialogowe|  
|PropertyGrid|  
|UserControl|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer/SplitterPanel|  
|Podziału|  
|RaftingContainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types.md)
