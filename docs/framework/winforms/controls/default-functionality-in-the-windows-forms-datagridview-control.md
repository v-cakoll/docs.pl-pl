---
title: Funkcje domyślne w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: 26633b0abaa8c1c2916153b2236ecf9e4982fd68
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208868"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Funkcje domyślne w formancie DataGridView formularzy systemu Windows
Formularze Windows <xref:System.Windows.Forms.DataGridView> kontroli udostępnia użytkownikom znacznej ilości funkcje domyślne.  
  
## <a name="default-functionality"></a>Domyślna funkcjonalność  
 Domyślnie <xref:System.Windows.Forms.DataGridView> sterowania:  
  
-   Automatycznie Wyświetla nagłówki kolumn i nagłówki wierszy, które pozostają widoczne, ponieważ tabela przewijać w pionie.  
  
-   Zawiera nagłówek wiersza, który zawiera wskaźnik zaznaczenia bieżącego wiersza.  
  
-   Nie ma prostokąta zaznaczenia w pierwszej komórki.  
  
-   Zawiera kolumny, które można automatycznie dopasowane, gdy użytkownik kliknie dwukrotnie separator kolumn.  
  
-   Automatycznie obsługuje stylów wizualnych Windows XP i rodziny Windows Server 2003 podczas <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda jest wywoływana z aplikacji `Main` metody.  
  
 Ponadto zawartość <xref:System.Windows.Forms.DataGridView> kontrolki mogą być edytowane przez domyślny:  
  
-   Jeśli użytkownik kliknie dwukrotnie lub naciśnie klawisz F2 w komórce, formant umieszcza komórkę w trybie edycji i automatycznie aktualizuje zawartość komórki, gdy użytkownik wpisuje.  
  
-   Jeśli użytkownik przewija widok w celu siatki, użytkownik będzie widział występuje wiersz do dodawania nowych rekordów. Gdy użytkownik kliknie ten wiersz, nowego wiersza zostanie dodane do <xref:System.Windows.Forms.DataGridView> kontrolki z wartościami domyślnymi. Gdy użytkownik naciśnie klawisz ESC, zniknie tego nowego wiersza.  
  
-   Jeśli użytkownik kliknie nagłówek wiersza, zostanie wybrany cały wiersz.  
  
 Po powiązaniu <xref:System.Windows.Forms.DataGridView> formant ze źródłem danych, ustawiając jego <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwość, formant:  
  
-   Automatycznie używa nazwy kolumn źródła danych jako tekst nagłówka kolumny.  
  
-   Jest wypełniana na podstawie zawartości źródła danych. <xref:System.Windows.Forms.DataGridView> kolumny są tworzone automatycznie dla każdej kolumny w źródle danych.  
  
-   Tworzy wiersz dla każdego wiersza widoczny w tabeli.  
  
-   Automatycznie sortuje wierszy oparte na danych bazowych, gdy użytkownik kliknie nagłówek kolumny.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView — Formant](datagridview-control-windows-forms.md)
