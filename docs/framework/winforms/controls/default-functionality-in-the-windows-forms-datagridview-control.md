---
title: "Funkcje domyślne w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d6b15085c301f074ef6fcf9e60a75299c4b245b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Funkcje domyślne w formancie DataGridView formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.DataGridView> kontroli udostępnia użytkownikom znaczną ilość domyślna funkcjonalność.  
  
## <a name="default-functionality"></a>Domyślna funkcjonalność  
 Domyślnie <xref:System.Windows.Forms.DataGridView> sterowania:  
  
-   Automatycznie Wyświetla nagłówki kolumn i nagłówki wierszy, które są widoczne jako tabeli Przewija w pionie.  
  
-   Zawiera nagłówek zawierający wskaźnik wybór dla bieżącego wiersza.  
  
-   Ma prostokąta zaznaczenia w pierwszej komórki.  
  
-   Zawiera kolumny, które można automatycznie dopasowane, gdy użytkownik kliknie dwukrotnie separator kolumn.  
  
-   Automatycznie obsługuje style wizualne w systemie Windows XP i z rodziny Windows Server 2003 podczas <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoda jest wywoływana z poziomu aplikacji `Main` metody.  
  
 Ponadto zawartość <xref:System.Windows.Forms.DataGridView> domyślnie można edytować kontrolki:  
  
-   Jeśli użytkownik kliknie dwukrotnie lub naciśnie klawisz F2 w komórce, formantu umieszcza komórki w trybie edycji i automatycznie aktualizuje zawartość komórki jako typy użytkownika.  
  
-   Jeśli użytkownik przewija widok w celu siatki, użytkownik zobaczy, czy wiersz dodawania nowych rekordów jest obecny. Jeśli użytkownik kliknie ten wiersz, jest dodawany nowy wiersz <xref:System.Windows.Forms.DataGridView> kontroli z wartościami domyślnymi. Gdy użytkownik naciśnie klawisz ESC, zniknie tego nowego wiersza.  
  
-   Gdy użytkownik kliknie nagłówek, cały wiersz jest zaznaczone.  
  
 Po powiązaniu <xref:System.Windows.Forms.DataGridView> formantu ze źródłem danych, ustawiając jego <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości, formant:  
  
-   Automatycznie używa nazwy kolumn źródła danych jako tekst nagłówka kolumny.  
  
-   Jest wypełniana zawartość źródła danych. <xref:System.Windows.Forms.DataGridView>kolumny są tworzone automatycznie dla każdej kolumny w źródle danych.  
  
-   Tworzy wiersz dla każdego wiersza widoczny w tabeli.  
  
-   Automatycznie sortuje wiersze oparte na danych, gdy użytkownik kliknie nagłówek kolumny.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 [DataGridView — formant](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
