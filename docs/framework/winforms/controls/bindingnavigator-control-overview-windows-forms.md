---
title: BindingNavigator — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: c2747a6801d4aa9cfde4227ffd5c29ca1de78d48
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744103"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>BindingNavigator — Informacje o formancie [Formularze systemu Windows]
Za pomocą kontrolki <xref:System.Windows.Forms.BindingNavigator> można utworzyć ustandaryzowaną metodę, aby użytkownicy mogli przeszukiwać i zmieniać dane w formularzu systemu Windows. Często używasz <xref:System.Windows.Forms.BindingNavigator> ze składnikiem <xref:System.Windows.Forms.BindingSource>, aby umożliwić użytkownikom przechodzenie między rekordami danych w formularzu i korzystanie z tych rekordów.  
  
## <a name="how-the-bindingnavigator-works"></a>Jak działa parametr BindingNavigator  

 Formant <xref:System.Windows.Forms.BindingNavigator> składa się z <xref:System.Windows.Forms.ToolStrip> z serią obiektów <xref:System.Windows.Forms.ToolStripItem> dla większości typowych akcji związanych z danymi: Dodawanie danych, usuwanie danych i nawigowanie po danych. Domyślnie formant <xref:System.Windows.Forms.BindingNavigator> zawiera te standardowe przyciski. Poniższy zrzut ekranu przedstawia kontrolkę <xref:System.Windows.Forms.BindingNavigator> w formularzu:
  
 ![Zrzut ekranu przedstawiający formant BindingNavigator.](./media/bindingnavigator-control-overview-windows-forms/bindingnavigator-control-form.gif)  
  
 Poniższa tabela zawiera listę formantów i opis ich funkcji.  
  
|formant|Funkcja|  
|-------------|--------------|  
|przycisk <xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A>|Wstawia nowy wiersz do bazowego źródła danych.|  
|przycisk <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A>|Usuwa bieżący wiersz z bazowego źródła danych.|  
|przycisk <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A>|Przenosi do pierwszego elementu w bazowym źródle danych.|  
|przycisk <xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A>|Przenosi do ostatniego elementu w źródłowym źródle danych.|  
|przycisk <xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A>|Przechodzi do następnego elementu w bazowym źródle danych.|  
|przycisk <xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A>|Przenosi do poprzedniego elementu w źródłowym źródle danych.|  
|pole tekstowe <xref:System.Windows.Forms.BindingNavigator.PositionItem%2A>|Zwraca bieżącą pozycję w źródłowym źródle danych.|  
|pole tekstowe <xref:System.Windows.Forms.BindingNavigator.CountItem%2A>|Zwraca łączną liczbę elementów w źródłowym źródle danych.|  
  
 Dla każdej kontrolki w tej kolekcji istnieje odpowiedni element członkowski składnika <xref:System.Windows.Forms.BindingSource>, który programowo udostępnia te same funkcje. Na przykład przycisk <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> odpowiada metodzie <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> składnika <xref:System.Windows.Forms.BindingSource>, przycisk <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> odpowiada metodzie <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> i tak dalej.  
  
 Jeśli przyciski domyślne nie są odpowiednie dla aplikacji lub jeśli potrzebujesz dodatkowych przycisków do obsługi innych typów funkcjonalności, możesz podać własne przyciski <xref:System.Windows.Forms.ToolStrip>. Zapoznaj się również z tematem [: Dodawanie przycisków Załaduj, Zapisz i Anuluj do kontrolki Windows Forms BindingNavigator](load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
