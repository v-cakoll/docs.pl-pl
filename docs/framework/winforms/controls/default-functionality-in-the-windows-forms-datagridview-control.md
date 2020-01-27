---
title: Domyślna funkcjonalność w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: b695883ac7ec3fb0c459adb66214b0eceab3a128
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746137"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Funkcje domyślne w formancie DataGridView formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.DataGridView> Windows Forms zapewnia użytkownikom znaczną liczbę domyślnych funkcji.  
  
## <a name="default-functionality"></a>Domyślna funkcjonalność  
 Domyślnie formant <xref:System.Windows.Forms.DataGridView>:  
  
- Automatycznie wyświetla nagłówki kolumn i nagłówki wierszy, które pozostaną widoczne, gdy tabela jest przewijana pionowo.  
  
- Zawiera nagłówek wiersza, który zawiera wskaźnik wyboru dla bieżącego wiersza.  
  
- Zawiera prostokąt wyboru w pierwszej komórce.  
  
- Ma kolumny, których rozmiar można zmienić automatycznie, gdy użytkownik kliknie dwukrotnie linię podziału kolumn.  
  
- Program automatycznie obsługuje style wizualne w systemach Windows XP i Windows Server 2003, gdy metoda <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> jest wywoływana z metody `Main` aplikacji.  
  
 Ponadto zawartość kontrolki <xref:System.Windows.Forms.DataGridView> można edytować domyślnie:  
  
- Jeśli użytkownik kliknie dwukrotnie lub naciśnie klawisz F2 w komórce, formant automatycznie umieści komórkę w trybie edycji i zaktualizuje zawartość komórki jako typy użytkowników.  
  
- Jeśli użytkownik przejdzie do końca siatki, zobaczysz, że jest dostępny wiersz służący do dodawania nowych rekordów. Gdy użytkownik kliknie ten wiersz, do kontrolki <xref:System.Windows.Forms.DataGridView> zostanie dodany nowy wiersz z wartościami domyślnymi. Gdy użytkownik naciśnie klawisz ESC, ten nowy wiersz zniknie.  
  
- Jeśli użytkownik kliknie nagłówek wiersza, zostanie wybrany cały wiersz.  
  
 Po powiązaniu formantu <xref:System.Windows.Forms.DataGridView> ze źródłem danych przez ustawienie jego właściwości <xref:System.Windows.Forms.DataGridView.DataSource%2A> kontrolka:  
  
- Automatycznie używa nazw kolumn źródła danych jako tekstu nagłówka kolumny.  
  
- Jest wypełniana zawartością źródła danych. kolumny <xref:System.Windows.Forms.DataGridView> są tworzone automatycznie dla każdej kolumny w źródle danych.  
  
- Tworzy wiersz dla każdego widocznego wiersza w tabeli.  
  
- Automatycznie sortuje wiersze na podstawie danych źródłowych, gdy użytkownik kliknie nagłówek kolumny.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView, kontrolka](datagridview-control-windows-forms.md)
