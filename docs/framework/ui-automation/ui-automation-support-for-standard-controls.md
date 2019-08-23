---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: d83713a81e7675a68482890c2401f1a0a6803abc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914230"
---
# <a name="ui-automation-support-for-standard-controls"></a>Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Ten temat zawiera informacje o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsłudze standardowych formantów w aplikacjach utworzonych [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]dla środowisk, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]i [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] .  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## <a name="windows-presentation-foundation-controls"></a>Kontrolki Windows Presentation Foundation  
 Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy sterujące, które dostarczają informacji lub pomocy technicznej dla interakcji użytkownika, mają pełną [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]obsługę natywną. Inne elementy, takie jak panele, nie są widoczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programu.  
  
<a name="Win32_Controls"></a>   
## <a name="win32-controls"></a>Kontrolki Win32  
 Większość [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] formantów jest [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] narażonych przez dostawców po stronie klienta w UIAutomationClientsideProviders. dll. Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.  
  
 Pełna pomoc techniczna jest świadczona tylko dla formantów z wersji 6 programu ComCtrl32. dll (dostępne [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] z i nowsze).  
  
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
  
 **Uwaga** Formant RichEdit jest obsługiwany tylko w przypadku wersji dostarczonych z [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] programem (w biblioteki riched20. dll w wersji 3,1 lub nowszej oraz MsftEdit. dll w wersji 4,1 i nowszych).  
  
 Następujące kontrolki nie są obsługiwane.  
  
|Nazwa klasy|Typ formantu|  
|----------------|------------------|  
|SysAnimate32|Obraz|  
|SysPager|pokrętło|  
|SysDateTimePick32|Celnej|  
|SysMonthCal32|Kalendarz|  
|MS_WINNOTE|Wyowietlon|  
|VBBubble|Wyowietlon|  
|Pasek przewijania (używany jako formant autonomiczny)|Suwak|  
|Podsiatka|Celnej|  
  
<a name="Windows_Forms_Controls"></a>   
## <a name="windows-forms-controls"></a>Formanty formularzy systemu Windows  
 Kontrolki Windows Forms są dostępne [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dla dostawców po stronie klienta w UIAutomationClientsideProviders. dll. Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.  
  
 Zazwyczaj formanty Windows Forms, które są otokami zarządzanymi [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] dla wspólnych formantów, są [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]obsługiwane przez program. Obsługiwane są następujące kontrolki.  
  
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

- [Typy kontrolek automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-types.md)
