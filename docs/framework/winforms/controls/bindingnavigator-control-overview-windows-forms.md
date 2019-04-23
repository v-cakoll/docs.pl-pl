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
ms.openlocfilehash: ad63f622aae55cb4175eddc93ab5e086965a8fe8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109112"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>BindingNavigator — Informacje o formancie [Formularze systemu Windows]
Możesz użyć <xref:System.Windows.Forms.BindingNavigator> formantu, aby utworzyć standardowe oznacza, że dla użytkowników wyszukać i zmiany danych w formularzu Windows. Często używane <xref:System.Windows.Forms.BindingNavigator> z <xref:System.Windows.Forms.BindingSource> składnika, aby umożliwić użytkownikom przechodzenie między rekordów danych na formularzu i interakcję z rekordami.  
  
## <a name="how-the-bindingnavigator-works"></a>Jak działa BindingNavigator  

 <xref:System.Windows.Forms.BindingNavigator> Kontroli składa się z <xref:System.Windows.Forms.ToolStrip> z serią <xref:System.Windows.Forms.ToolStripItem> obiektów dla najbardziej typowych akcji związanych z danymi: Dodawanie danych, usuwanie danych ani nawigować przez dane. Domyślnie <xref:System.Windows.Forms.BindingNavigator> kontrolka zawiera następujące przyciski standardowe. Poniższy zrzut ekranu przedstawia <xref:System.Windows.Forms.BindingNavigator> kontrolki na formularzu:
  
 ![Zrzut ekranu przedstawiający BindingNavigator — kontrolka.](./media/bindingnavigator-control-overview-windows-forms/bindingnavigator-control-form.gif)  
  
 Poniższej tabeli wymieniono kontrolek i opisano ich funkcje.  
  
|formant|Funkcja|  
|-------------|--------------|  
|<xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> Przycisk|Wstawia nowy wiersz do bazowego źródła danych.|  
|<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> Przycisk|Usuwa bieżący wiersz z bazowego źródła danych.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> Przycisk|Przenosi do pierwszego elementu w źródle danych.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> Przycisk|Przenosi do ostatniego elementu w źródle danych.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> Przycisk|Przechodzi do następnego elementu w źródle danych.|  
|<xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> Przycisk|Przenosi do poprzedniego elementu w źródle danych.|  
|<xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> pole tekstowe|Zwraca bieżącą pozycję w źródle danych.|  
|<xref:System.Windows.Forms.BindingNavigator.CountItem%2A> pole tekstowe|Zwraca całkowitą liczbę elementów w źródle danych.|  
  
 Dla każdej kontrolki w tej kolekcji jest elementem członkowskim odpowiednie <xref:System.Windows.Forms.BindingSource> składnika, który programowo udostępnia taką samą funkcjonalność. Na przykład <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> przycisk odnosi się do <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metody <xref:System.Windows.Forms.BindingSource> składnika <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> przycisk odnosi się do <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> metoda i tak dalej.  
  
 Jeśli przyciski domyślne nie są odpowiednie dla aplikacji lub jeśli potrzebujesz dodatkowych przycisków, aby obsłużyć inne typy funkcji, możesz podać własne <xref:System.Windows.Forms.ToolStrip> przycisków. Zobacz też [jak: Dodaj obciążenia, Zapisz i Anuluj przycisków Windows kontrolki BindingNavigator formularzy](load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
