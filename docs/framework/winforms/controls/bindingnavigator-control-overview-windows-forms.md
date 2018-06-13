---
title: BindingNavigator — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: ae1e8273c39122e094817e28379e52c19c573a3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528785"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>BindingNavigator — Informacje o formancie [Formularze systemu Windows]
Można użyć <xref:System.Windows.Forms.BindingNavigator> formantu, aby utworzyć standardowych środków użytkownikom wyszukiwanie i zmienić danych na formularzu systemu Windows. Często używane <xref:System.Windows.Forms.BindingNavigator> z <xref:System.Windows.Forms.BindingSource> składnik, aby umożliwić użytkownikom przechodzenie między rekordów danych w formularzu i interakcję z rekordów.  
  
## <a name="how-the-bindingnavigator-works"></a>Jak działa BindingNavigator  
 <xref:System.Windows.Forms.BindingNavigator> Kontroli składa się z <xref:System.Windows.Forms.ToolStrip> z serii <xref:System.Windows.Forms.ToolStripItem> obiektów większość typowych akcji związanych z danymi: Dodawanie danych, usuwanie danych ani nawigować przez dane. Domyślnie <xref:System.Windows.Forms.BindingNavigator> formant zawiera tych przycisków standardowa. Następujący ekran zrzut pokazuje <xref:System.Windows.Forms.BindingNavigator> kontrolkę w formularzu.  
  
 ![BindingNavigator — kontrolka](../../../../docs/framework/winforms/controls/media/cpdatacontainerctrl.gif "cpDataContainerCtrl")  
  
 Poniższa tabela zawiera listę formantów oraz opis ich funkcji.  
  
|Formant|Funkcja|  
|-------------|--------------|  
|<xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> Przycisk|Wstawia nowy wiersz w źródle danych.|  
|<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> Przycisk|Usuwa bieżący wiersz w źródle danych.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> Przycisk|Przenosi do pierwszego elementu w źródle danych.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> Przycisk|Przenosi do ostatniego elementu w źródle danych.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> Przycisk|Przechodzi do następnego elementu w źródle danych.|  
|<xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> Przycisk|Przenosi do poprzedniego elementu w źródle danych.|  
|<xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> Pole tekstowe|Zwraca bieżącą pozycję w źródle danych.|  
|<xref:System.Windows.Forms.BindingNavigator.CountItem%2A> Pole tekstowe|Zwraca całkowitą liczbę elementów w źródle danych.|  
  
 Dla każdego formantu w tej kolekcji jest elementem członkowskim odpowiedniego <xref:System.Windows.Forms.BindingSource> składnik, który programowo zapewnia te same funkcje. Na przykład <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> przycisk odpowiada <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metody <xref:System.Windows.Forms.BindingSource> składnika <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> przycisk odpowiada <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> — metoda i tak dalej.  
  
 Jeśli domyślnych przycisków nie są odpowiednie do aplikacji lub jeśli potrzebujesz dodatkowych przycisków do obsługi innych funkcji, możesz podać własne <xref:System.Windows.Forms.ToolStrip> przycisków. Zobacz też [porady: Dodawanie obciążenia, Zapisz i Anuluj przycisków do formantu BindingNavigator formularzy systemu Windows](../../../../docs/framework/winforms/controls/load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingNavigator, kontrolka](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
