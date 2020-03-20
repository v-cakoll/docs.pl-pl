---
title: Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
ms.date: 03/30/2017
helpviewer_keywords:
- controls, UI Automation support for
- UI Automation, support for standard controls
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
ms.openlocfilehash: 36028d589e98177f6a0e83092edd656860b1a8d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179849"
---
# <a name="ui-automation-support-for-standard-controls"></a>Obsługa automatyzacji interfejsu użytkownika dla standardowych formantów
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] informacje dotyczące obsługi standardowych [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]formantów w aplikacjach opracowanych dla frameworków formularzy Win32 i Windows Forms.  
  
<a name="Windows_Presentation_Foundation_Controls"></a>
## <a name="windows-presentation-foundation-controls"></a>Kontrolki fundacji prezentacji systemu Windows  
 Wszystkie [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementy sterujące, które zapewniają informacje lub [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]wsparcie dla interakcji z użytkownikiem mają pełną obsługę natywną dla . Inne elementy, takie jak panele, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nie są widoczne dla programu .  
  
<a name="Win32_Controls"></a>
## <a name="win32-controls"></a>Sterowanie Win32  
 Większość formantów Win32 są narażone na [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] za pośrednictwem dostawców po stronie klienta w UIAutomationClientsideProviders.dll. Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.  
  
 Pełna obsługa jest dostępna tylko dla formantów z wersji 6 *comctrl32.dll*.  
  
 Obsługiwane są następujące formanty.  
  
|Nazwa klasy|Typ sterowania|  
|----------------|------------------|  
|Button|Button|  
|Button|RadioButton|  
|Button|Grupa|  
|Button|CheckBox|  
|Button|Hyperlink|  
|Button|Splitbutton|  
|Button|CheckBox|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Edytuj|Dokument|  
|Edytuj|Edytuj|  
|SysLink (syslink)|Hyperlink|  
|Statyczny|Tekst|  
|Statyczny|Image (Obraz)|  
|SysIPAddress32|Niestandardowy|  
|SysHeader32 (Właz głowy)|Nagłówek/nagłówekItem|  
|Widok SysListView32|DataGrid|  
|Widok SysListView32|List|  
|ListBox|List|  
|ListBox|Listitem|  
|#32768|Menu|  
|#32768|MenuItem|  
|msctls_progress32|ProgressBar|  
|Richedit|Dokumentu. Patrz uwaga.|  
|RichEdit20A|Dokument|  
|RichEdit20W|Dokument|  
|BogatyEdyt50W|Dokument|  
|ScrollBar|Suwak|  
|msctls_trackbar32|Suwak|  
|msctls_updown32|pokrętło|  
|msctls_statusbar32|StatusBar|  
|SysTabControl32|Tab|  
|SysTabControl32|Tabitem|  
|Pasek narzędziWindow32|ToolBar|  
|Pasek narzędziWindow32|MenuItem|  
|Pasek narzędziWindow32|Button|  
|Pasek narzędziWindow32|CheckBox|  
|Pasek narzędziWindow32|RadioButton|  
|Pasek narzędziWindow32|Separator|  
|tooltips_class32|ToolTip|  
|#32774|ToolTip|  
|ReBarWindow32|Pasek narzędzi|  
|Widok SysTreeView32|Drzewo|  
|Widok SysTreeView32|Treeitem|  
  
 **Uwaga** Formant RichEdit jest obsługiwany tylko w wersjach dostarczanych z systemem Windows Vista (w pliku RichEd20.dll w wersji 3.1 i nowszej oraz msftEdit.dll w wersji 4.1 i nowszej).  
  
 Następujące formanty nie są obsługiwane.  
  
|Nazwa klasy|Typ kontrolki|  
|----------------|------------------|  
|SysAnimate32 (WysAnimate32)|Image (Obraz)|  
|SysPager (SysPager)|pokrętło|  
|SysDateTimePick32|Niestandardowy|  
|Miesiąc SysCal32|Kalendarz|  
|MS_WINNOTE|Etykietka narzędzia|  
|VBBubble (VBBubble)|Etykietka narzędzia|  
|Pasek przewijania (używany jako formant autonomiczny)|Suwak|  
|SuperGrid (SuperGrid)|Niestandardowy|  
  
<a name="Windows_Forms_Controls"></a>
## <a name="windows-forms-controls"></a>Formanty formularzy systemu Windows  
 Formanty formularzy [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] systemu Windows są widoczne za pośrednictwem dostawców po stronie klienta w UIAutomationClientsideProviders.dll. Ten zestaw jest automatycznie rejestrowany do użytku z aplikacjami klienckimi automatyzacji interfejsu użytkownika.  
  
 Zazwyczaj formanty windows forms, które są zarządzane otoki dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]win32 typowe formanty są obsługiwane przez . Obsługiwane są następujące formanty.  
  
|Nazwa klasy|  
|----------------|  
|Button|  
|CheckBox|  
|Checkedlistbox|  
|Colordialog|  
|ComboBox|  
|FolderBrowser|  
|Fontdialog|  
|GroupBox|  
|Hscrollbar|  
|Imagelist|  
|Label|  
|ListBox|  
|ListView|  
|MainMenu/ContextMenu|  
|MonthCalendar|  
|Notifyicon|  
|Openfiledialog|  
|Pagesetupdialog|  
|PrintDialog|  
|ProgressBar|  
|RadioButton|  
|RichTextBox|  
|Savefiledialog|  
|Scrollablecontrol|  
|Soundplayer|  
|StatusBar|  
|TabControl/TabPage|  
|TextBox|  
|Czasomierz|  
|Pasek narzędzi|  
|ToolTip|  
|Trackbar|  
|TreeView|  
|Vscrollbar|  
|Webbrowser|  
  
 Poniższe formanty [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] są widoczne tylko za pośrednictwem ich obsługi dostępności microsoft active. Niektóre funkcje mogą być niedostępne.  
  
|Nazwa formantu|  
|------------------|  
|BindingSource|  
|DataGrid|  
|Datagridview|  
|Nawigator danych|  
|Domainupdown|  
|Errorprovider|  
|Flowlayoutpanel|  
|Formularz|  
|Linklabel|  
|Helpprovider|  
|Maskedtextbox|  
|MenuStrip/ContextMenuStrip|  
|NumericUpDown|  
|Panel|  
|Picturebox|  
|Printdocument|  
|PrintPreview-Sterowanie|  
|Okno dialogowe PrintPreview|  
|Propertygrid|  
|Usercontrol|  
|ToolStrip|  
|Tablelayoutpanel|  
|Panel SplitContainer/Splitter|  
|Rozdzielacz|  
|SpływyKontainer|  
|StatusStrip|  
  
## <a name="see-also"></a>Zobacz też

- [Typy kontrolek automatyzacji interfejsu użytkownika](ui-automation-control-types.md)
